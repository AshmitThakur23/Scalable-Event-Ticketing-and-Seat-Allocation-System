# 🛡️ Scalable Event Ticketing & Seat Allocation System  
### **Cloud-Scale, Zero-Oversell Ticketing Architecture (Technical + Visual Version)**

This project implements a **production-grade ticket booking platform** similar to  
BookMyShow or Ticketmaster—designed for **100K+ concurrent users**, **5K reservations/sec**,  
with **strong consistency**, **sharding**, **flash-sale queueing**, and **zero double-booking** guarantees.

It covers everything: APIs, ERD, concurrency model, flows, caching, queues, SLOs, monitoring,  
failures, capacity planning, and more—in a highly visual ASCII form.

---

# ============================================================
# 🟦 1. Executive Summary (Very Clear Breakdown)
# ============================================================

The system must:

✔ Allow fast browsing of events (< 100 ms p50)  
✔ Show real-time seat availability  
✔ Hold seats for 5–15 minutes  
✔ Commit seats atomically after payment  
✔ Prevent overselling at all times  
✔ Handle flash-sales (20K RPS bursts)  
✔ Guarantee p99 < 2 seconds for checkout  
✔ Maintain 99.95% uptime  

The core of the design is **Optimistic CAS** (Compare-And-Set) + **sharded inventory DB**  
+ **Redis/Raft-based Reservation Coordinator**.

---

# ============================================================
# 🟦 2. High-Level Architecture (Deep Visual Diagram)
# ============================================================

```
                                  ┌────────────────────────────────────────┐
                                  │               API GATEWAY              │
                                  │ Auth | WAF | Rate-Limit | Routing      │
                                  └───────────────┬────────────────────────┘
                                                  │
        ┌─────────────────────────────┬───────────┼───────────┬─────────────────────────────┐
        │                             │           │           │                             │
        ▼                             ▼           ▼           ▼                             ▼

┌────────────────────┐      ┌──────────────────┐   ┌─────────────────────┐      ┌────────────────────┐
│   Catalog Service   │      │ Seat Map Service │   │  Reservation Svc    │      │ Commit/Allocation  │
│  (Events, Venues)   │      │ (Layouts + TTL)  │   │ Create seat holds   │      │ Final booking +    │
│ Eventual consistency│      │ Cached 5–15 sec  │   │ TTL expiry handling │      │ payment integration │
└────────────────────┘      └──────────────────┘   └───────────┬─────────┘      └───────────┬────────┘
                                                                │                           │
                                                                ▼                           ▼

                                                 ┌──────────────────────────┐    ┌──────────────────────────┐
                                                 │ Reservation Coordinator  │    │       Payment Adapter     │
                                                 │ Redis/Raft - CAS Control │    │    Stripe/Razorpay etc.   │
                                                 └───────────────┬──────────┘    └──────────────┬──────────┘
                                                                 │                               │
                                                                 ▼                               ▼

                                                 ┌──────────────────────────┐     ┌──────────────────────────┐
                                                 │     Inventory DB         │     │       Orders DB          │
                                                 │ Sharded seats + version  │     │ Confirmed bookings store │
                                                 └──────────────────────────┘     └──────────────────────────┘
```

### Why this architecture?

- Decomposed microservices prevent hotspots  
- Strong seat consistency isolated to Inventory DB  
- Read-heavy (Catalog/SeatMap) handled by cache  
- Flash-sale pressure absorbed via queue + coordinator  
- Payment flows isolated for PCI safety  

---

# ============================================================
# 🟦 3. Data Model (ERD - Visual ASCII)
# ============================================================

```
                 ┌──────────────┐
                 │    Event     │
                 └───────┬──────┘
                         │ 1..*
                         ▼
                 ┌──────────────┐
                 │    Venue     │
                 └───────┬──────┘
                         │ 1..*
                         ▼
                 ┌──────────────┐
                 │   Section    │
                 └───────┬──────┘
                         │ 1..*
                         ▼
                 ┌──────────────┐
                 │     Row      │
                 └───────┬──────┘
                         │ 1..*
                         ▼
                 ┌──────────────┐
                 │     Seat     │
                 └──────────────┘


                     ┌──────────────┐
                     │     User     │
                     └──────────────┘
                             │ 1..*
                             ▼
                     ┌──────────────┐
                     │ Reservation  │
                     │ (Holds w/TTL)│
                     └───────┬──────┘
                             │ 1..1
                             ▼
                     ┌──────────────┐
                     │    Order     │
                     └───────┬──────┘
                             │ 1..1
                             ▼
                     ┌──────────────┐
                     │ PaymentRecord│
                     └──────────────┘
```

---

# ============================================================
# 🟦 4. API Contracts (Clear & Complete)
# ============================================================

## 🔍 Browse Events
```
GET /events?from=&to=&q=
```
Returns paginated list (TTL 30s).

---

## 🗺️ Get Seat Map
```
GET /events/{id}/seatmap
```

- Layout (rows, seats, colors)  
- Light availability snapshot (cache 5–15s)

---

## ✋ Reserve Seats (Hold)
```
POST /events/{id}/reservations
{
  "client_reservation_id": "uuid-123",
  "user_id": "U1",
  "seat_ids": ["A-10", "A-11"],
  "ttl_seconds": 300
}
```

Responses:
- **201** → hold created  
- **409** → seat unavailable  
- **429** → rate limit hit  

---

## 💳 Commit Reservation
```
POST /reservations/{hold_id}/commit
{
  "payment_token": "tok_visa",
  "idempotency_key": "pay-001"
}
```

Responses:
- **200** → order confirmed  
- **410** → hold expired  

---

## ❌ Cancel Hold
```
DELETE /reservations/{hold_id}
```

---

# ============================================================
# 🟦 5. Seat Allocation Consistency (100% Oversell Prevention)
# ============================================================

## ✔ CAS (Compare-And-Set) Query  
This ensures **only 1 user** can grab a seat.

```
UPDATE inventory
SET status='held',
    version = version + 1
WHERE seat_id=? 
  AND status='available'
  AND version=?;
```

If `rows_affected = 1` → hold success  
If `rows_affected = 0` → someone else already took it  

**No global locks, no bottlenecks, highly scalable.**

---

# ============================================================
# 🟦 6. Reserve → Commit Sequence Flow (ASCII Diagram)
# ============================================================

```
User
  │
  ▼
API Gateway
  │
  ▼
Reservation Service
  │
  ▼
Reservation Coordinator (Redis/Raft)
  │
  ▼
Inventory DB (CAS seat hold)
  │
  └───► Returns hold_id + expiry


User pays →
Commit Service
  │
  ▼
Payment Adapter → Payment Provider
  │                       │
  │                       └──► payment_success
  ▼
Commit Service
  ▼
Atomic Transaction:
  - Mark seats BOOKED
  - Create Order
  - Create PaymentRecord
  - Finalize reservation
  ▼
Return order_id
```

---

# ============================================================
# 🟦 7. Flash Sale Handling
# ============================================================

```
           ┌───────────────────────────┐
           │        API Gateway        │
           │   Rate Limit (throttle)   │
           └──────────────┬────────────┘
                           │
                           ▼
              ┌────────────────────────┐
              │   Admission Queue       │
              │ Redis/Kafka (FIFO/Token)│
              └──────────────┬─────────┘
                             │
                             ▼
                 ┌───────────────────────┐
                 │ Reservation Service    │
                 │ Processes at safe rate │
                 └───────────────────────┘
```

- Queue protects DB from overload  
- Tickets allocated **fairly**  
- Backpressure ensures stability  

---

# ============================================================
# 🟦 8. Caching Strategy
# ============================================================

| Layer     | Cache      | TTL      |
|-----------|------------|----------|
| Catalog   | CDN/Redis  | 30–60s   |
| Seat Map  | Redis/CDN  | 5–15s    |
| Sessions  | Redis      | 15m      |

Cache invalidation via:
```
seat:update:{event}:{section}
```

---

# ============================================================
# 🟦 9. Capacity Planning (From PDF)
# ============================================================

| Metric | Value |
|--------|--------|
| Peak concurrent users | 100K |
| Seat holds/sec | 5K sustained / 20K burst |
| Commit/sec | 2K |
| Shards | 8–16 |
| Redis nodes | 6–8 |
| API workers | autoscaled (10+ pods) |

Headroom: **3×** for traffic spikes.

---

# ============================================================
# 🟦 10. Failure Handling (From PDF)
# ============================================================

| Failure | Mitigation |
|---------|------------|
| Oversell race | CAS + unique seat constraint |
| Payment timeout | TTL holds + webhook reconciliation |
| Coordinator crash | Idempotency keys & retry |
| Duplicate payment | Idempotent commit + webhook dedupe |

---

# ============================================================
# 🟦 11. Payments & Idempotency
# ============================================================

- Client generates **payment_token**  
- Server uses **idempotency_key**  
- Payment provider webhook also deduped  
- Commit = **single atomic DB transaction**

---

# ============================================================
# 🟦 12. Monitoring & Alerts
# ============================================================

Metrics:
- Seat reservation success rate  
- Reservation latency p95/p99  
- DB shard utilization  
- Oversell counter  
- Queue depth  
- Cache hit ratio  

Alerts:
- oversell_event = 1  
- payment_success < 90%  
- queue_depth > threshold  
- reservation_failure > 5%  

---

# ============================================================
# 🟦 13. Deployment & Scaling
# ============================================================

- Kubernetes + HPA  
- Blue/Green deployments  
- Sharded services (by event_id or section)  
- CDN for static assets  
- Redis cluster for coordinator/caching  

---

# ============================================================
# 🟦 14. Testing Plan (From PDF)
# ============================================================

| Test | Purpose |
|------|---------|
| Load test | 20K RPS flash-sale |
| Chaos test | kill coordinator mid-sale |
| Idempotency test | replay commit requests |
| Reconciliation test | ensure no oversell |
| E2E test | Reserve → Commit → Order |

---

# ============================================================
# 🟦 15. Appendix: Example Payloads
# ============================================================

### Reserve
```
POST /events/123/reservations
{
  "client_reservation_id": "uuid-abc",
  "user_id": "user-42",
  "seat_ids": ["A-10","A-11"],
  "ttl_seconds": 300
}
```

### Commit
```
POST /reservations/hold-789/commit
{
  "idempotency_key": "pay-0001",
  "payment_token": "tok_visa_..."
}
```

---

# 🎉 End of README  
This is the **final, complete, visual, deeply explained, interview-ready README.**
