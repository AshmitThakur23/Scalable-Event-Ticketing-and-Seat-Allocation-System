<div align="center">

# 🎫 Scalable Event Ticketing & Seat Allocation System
### *Production-Grade Distributed Ticketing Platform*

[![System Design](https://img.shields.io/badge/System-Design-blue.svg)](https://github.com/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System)
[![Microservices](https://img.shields.io/badge/Architecture-Microservices-green.svg)](https://github.com/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System)
[![High Availability](https://img.shields.io/badge/Availability-99.95%25-brightgreen.svg)](https://github.com/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System)
[![Concurrency](https://img.shields.io/badge/Concurrent_Users-100K%2B-orange.svg)](https://github.com/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System)

**⚡ Real-time Seat Booking** | **🔒 Zero Overselling** | **🚀 Flash-Sale Ready** | **💳 Secure Payments**

*Enterprise-grade ticketing architecture designed to handle millions of concurrent users with sub-second latency, inspired by industry leaders like BookMyShow, Ticketmaster, and Eventbrite.*

[📖 Documentation](https://github.com/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System/blob/main/Scalable%20Ticketing%20System%20Design%20Report.pdf) • [📊 Presentation](https://github.com/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System/blob/main/Scalable-Event-Ticketing-and-Seat-Allocation-System%20(wecompress.com).pptx) • [🎯 Use Cases](#-real-world-applications)

---

</div>

## 📑 Table of Contents

- [🌟 Overview](#-overview)
- [✨ Key Features](#-key-features)
- [🎯 Real-World Applications](#-real-world-applications)
- [🏗️ System Architecture](#️-system-architecture)
- [🧩 Core Components](#-core-components)
- [📊 Data Model](#-data-model)
- [🔌 API Design](#-api-design)
- [🛡️ Consistency Guarantees](#️-consistency-guarantees)
- [⚡ Performance Optimization](#-performance-optimization)
- [🎪 Flash Sale Strategy](#-flash-sale-strategy)
- [💾 Caching Architecture](#-caching-architecture)
- [💳 Payment Processing](#-payment-processing)
- [📈 Scalability & Capacity](#-scalability--capacity)
- [🔧 Failure Recovery](#-failure-recovery)
- [📊 Monitoring & Observability](#-monitoring--observability)
- [🧪 Testing Strategy](#-testing-strategy)
- [🚀 Deployment Architecture](#-deployment-architecture)
- [🔐 Security Measures](#-security-measures)
- [📚 Technology Stack](#-technology-stack)
- [🎓 Learning Resources](#-learning-resources)

---

## 🌟 Overview

This project represents a **production-ready, distributed event ticketing platform** capable of handling the most demanding scenarios in the live entertainment industry. Built with modern cloud-native principles, it addresses the critical challenges of:

- **Race Conditions**: Preventing double-booking through optimistic locking (CAS)
- **High Concurrency**: Supporting 100K+ simultaneous users
- **Flash Sales**: Managing viral events with millions of requests
- **Data Consistency**: Guaranteeing zero overselling across distributed systems
- **Payment Reliability**: Ensuring atomic, idempotent transactions
- **Global Scale**: Multi-region deployment with low latency

### 📊 System Capabilities

```
┌─────────────────────────────────────────────────────────┐
│  Performance Metrics (Production SLA)                   │
├─────────────────────────────────────────────────────────┤
│  ⚡ Concurrent Active Users      : 100,000+             │
│  🎟️  Reservations/sec (sustained): 5,000               │
│  📈 Burst Capacity              : 20,000 req/sec        │
│  🔄 Commit Throughput           : 2,000 orders/sec      │
│  📊 Browsing Latency (p50)      : < 100 ms              │
│  ✅ Checkout Latency (p99)      : < 2 seconds           │
│  🛡️  System Uptime               : 99.95%               │
│  🚫 Overselling Rate            : 0% (guaranteed)       │
└─────────────────────────────────────────────────────────┘
```

---

## ✨ Key Features

### 🎯 Core Booking Features

#### ⚡ **Real-Time Seat Availability**
- **Live Seat Map Updates**: WebSocket-based real-time availability overlay
- **Interactive Seat Selection**: Visual, color-coded seat picker with pricing tiers
- **Instant Feedback**: Sub-100ms availability checks via Redis cache
- **Smart Recommendations**: AI-powered best seat suggestions based on user preferences

#### 🔒 **Zero-Oversell Guarantee**
- **Optimistic Locking (CAS)**: Compare-and-swap operations at database level
- **Version-Based Concurrency**: Prevents lost updates in distributed environment
- **Atomic State Transitions**: Single-source-of-truth inventory management
- **Conflict Resolution**: Graceful degradation with user-friendly error messages

#### ⏰ **Intelligent Reservation System**
- **Configurable TTL**: 5–15 minute seat holds (customizable per event)
- **Auto-Expiration Workers**: Background jobs to release abandoned carts
- **Reservation Extensions**: Allow users to extend holds during checkout
- **Cart Hoarding Prevention**: Limits on simultaneous reservations per user

#### 🎪 **Flash-Sale Architecture**
- **Admission Queue System**: Fair, token-based user queuing
- **Progressive Rate Limiting**: Adaptive throttling based on system load
- **Backpressure Handling**: Graceful degradation under extreme load
- **Virtual Waiting Room**: Real-time queue position updates

#### 💳 **Enterprise Payment Integration**
- **PCI DSS Compliant**: Secure tokenized payment processing
- **Multi-Gateway Support**: Stripe, PayPal, Razorpay, etc.
- **Idempotent Operations**: Prevents duplicate charges on retries
- **Webhook Reconciliation**: Automated payment verification and order confirmation

### 🚀 Advanced Features

#### 🌍 **Multi-Region Support**
- Geographic seat allocation zones
- CDN-based content delivery
- Regional database sharding
- Cross-region failover

#### 🎨 **Dynamic Pricing**
- Time-based pricing (early bird, last minute)
- Demand-based surge pricing
- Group discount automation
- Promotional code engine

#### 📱 **Multi-Platform Support**
- Web application (React/Vue)
- Mobile apps (iOS/Android)
- Progressive Web App (PWA)
- Third-party API integrations

#### 🤖 **Smart Features**
- Anti-bot detection (CAPTCHA, device fingerprinting)
- Fraud detection algorithms
- User behavior analytics
- Recommendation engine

---

## 🎯 Real-World Applications

This system architecture is suitable for:

| Industry | Use Cases | Scale Examples |
|----------|-----------|----------------|
| 🎵 **Live Entertainment** | Concerts, Music Festivals | Taylor Swift tours, Coachella |
| 🎬 **Cinema** | Movie theaters, Film festivals | IMAX screenings, Premieres |
| ⚽ **Sports** | Stadiums, Arenas | FIFA World Cup, Super Bowl |
| 🎭 **Performing Arts** | Theaters, Opera houses | Broadway shows, Ballet |
| 🎓 **Education** | Conferences, Workshops | Tech summits, Training sessions |
| ✈️ **Transportation** | Airlines, Railways | Flight bookings, Train reservations |
| 🏨 **Hospitality** | Hotels, Restaurants | Room reservations, Table bookings |

---

## 🏗️ System Architecture

### 🎨 High-Level Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           CLIENT LAYER                                       │
│  📱 Mobile Apps     💻 Web Browser     🖥️  Admin Portal     🔌 Partner APIs  │
└──────────────────────────────────┬──────────────────────────────────────────┘
                                   │
                                   │ HTTPS/WSS
                                   ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                        EDGE & SECURITY LAYER                                 │
│  🌍 CDN (CloudFlare)  │  🛡️ WAF  │  🔐 DDoS Protection  │  🚦 Rate Limiter  │
└──────────────────────────────────┬──────────────────────────────────────────┘
                                   │
                                   ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                          API GATEWAY LAYER                                   │
│   🔑 Authentication (JWT/OAuth2)  │  🎯 Routing  │  📊 Telemetry            │
│   ⚖️  Load Balancing              │  🔄 Retries  │  🔍 Request Logging      │
└──────────────────────────────────┬──────────────────────────────────────────┘
                                   │
        ┌──────────────────────────┼──────────────────────────┐
        │                          │                          │
        ▼                          ▼                          ▼
┌────────────────┐      ┌────────────────────┐    ┌─────────────────────┐
│ 📚 CATALOG     │      │ 🗺️  SEAT MAP       │    │ 🎫 RESERVATION      │
│    SERVICE     │      │    SERVICE         │    │    SERVICE          │
│                │      │                    │    │                     │
│ • Events CRUD  │      │ • Venue layouts    │    │ • Hold management   │
│ • Search       │      │ • Availability     │    │ • TTL enforcement   │
│ • Filtering    │      │ • Real-time sync   │    │ • Lock acquisition  │
└────────────────┘      └────────────────────┘    └──────────┬──────────┘
                                                              │
                                                              ▼
                                                   ┌──────────────────────┐
                                                   │ 🎯 RESERVATION       │
                                                   │    COORDINATOR       │
                                                   │                      │
                                                   │ • CAS operations     │
                                                   │ • Consensus (Raft)   │
                                                   │ • State machine      │
                                                   └──────────┬───────────┘
                                                              │
        ┌─────────────────────────────────────────────────────┼────────────┐
        │                                                     │            │
        ▼                                                     ▼            ▼
┌────────────────┐      ┌────────────────────┐    ┌──────────────────────────┐
│ 💳 PAYMENT     │      │ 📧 NOTIFICATION    │    │ 📊 ANALYTICS             │
│    SERVICE     │      │    SERVICE         │    │    SERVICE               │
│                │      │                    │    │                          │
│ • Gateway API  │      │ • Email/SMS        │    │ • Event tracking         │
│ • Idempotency  │      │ • Push notifs      │    │ • User behavior          │
│ • Webhooks     │      │ • Templates        │    │ • Business intelligence  │
└────────────────┘      └────────────────────┘    └──────────────────────────┘

═══════════════════════════════════════════════════════════════════════════════
                              DATA LAYER
═══════════════════════════════════════════════════════════════════════════════

┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
│ 🗄️  POSTGRESQL    │  │ ⚡ REDIS CLUSTER │  │ 📨 KAFKA         │
│    (Sharded)     │  │                  │  │                  │
│                  │  │ • Cache          │  │ • Event stream   │
│ • Inventory DB   │  │ • Sessions       │  │ • Async tasks    │
│ • User DB        │  │ • Pub/Sub        │  │ • Audit logs     │
│ • Order DB       │  │ • Rate limit     │  │ • Analytics      │
└──────────────────┘  └──────────────────┘  └──────────────────┘
```

### 🔄 Request Flow: User Journey

```
1️⃣  User browses events
    ↓ [CDN cached, Redis backed]
2️⃣  Selects event & views seat map
    ↓ [WebSocket for real-time updates]
3️⃣  Chooses seats & initiates reservation
    ↓ [CAS operation on inventory DB]
4️⃣  Seats HELD (TTL starts)
    ↓ [Background worker monitors expiry]
5️⃣  User proceeds to payment
    ↓ [Payment gateway integration]
6️⃣  Payment processed successfully
    ↓ [Webhook received, verified]
7️⃣  Reservation COMMITTED → Order created
    ↓ [Atomic DB transaction]
8️⃣  Ticket generated & sent
    ↓ [Email/SMS notification]
9️⃣  Seat marked as BOOKED
    ↓ [Cache invalidated, real-time update]
```

---

## 🧩 Core Components

### 1. 📚 **Catalog Service**
**Responsibility**: Event discovery and metadata management

```yaml
Features:
  - Event CRUD operations
  - Advanced search (Elasticsearch)
  - Filtering (date, location, category, price)
  - Trending events algorithm
  - Recommendations engine

Endpoints:
  - GET    /api/v1/events
  - GET    /api/v1/events/{id}
  - POST   /api/v1/events (Admin)
  - PATCH  /api/v1/events/{id} (Admin)
  - DELETE /api/v1/events/{id} (Admin)

Data Store:
  - Primary: PostgreSQL
  - Cache: Redis (30-60s TTL)
  - Search: Elasticsearch
```

### 2. 🗺️ **Seat Map Service**
**Responsibility**: Venue layouts and real-time availability

```yaml
Features:
  - Dynamic seat map rendering
  - Pricing tier visualization
  - Accessibility seat marking
  - Section-based navigation
  - Real-time availability overlay

Technology:
  - SVG-based interactive maps
  - WebSocket connections
  - Redis Pub/Sub for updates
  - Cached layouts (15s refresh)

Optimization:
  - Section-level locking
  - Incremental updates
  - Client-side rendering
```

### 3. 🎫 **Reservation Service**
**Responsibility**: Seat hold management and TTL enforcement

```yaml
Core Logic:
  - Attempt seat reservation (CAS)
  - Create temporary hold record
  - Set expiration timer
  - Handle concurrent conflicts
  - Manage reservation extensions

Background Workers:
  - Expiry scanner (every 30s)
  - Abandoned cart cleaner
  - Metrics aggregator

State Machine:
  AVAILABLE → HELD → BOOKED
           ↓
       EXPIRED (back to AVAILABLE)
```

### 4. 🎯 **Reservation Coordinator**
**Responsibility**: Distributed consensus and conflict resolution

```yaml
Algorithm: Raft Consensus
Purpose: Single source of truth for seat state

Guarantees:
  - Linearizability
  - Strong consistency
  - Fault tolerance (leader election)
  - No split-brain scenarios

Implementation:
  - Redis cluster with Redlock
  - Or dedicated Raft library (etcd/Consul)
  - Quorum-based writes (N/2 + 1)
```

### 5. 💳 **Payment Service**
**Responsibility**: Secure payment processing

```yaml
Features:
  - Multi-gateway abstraction
  - PCI-compliant tokenization
  - Idempotent charge API
  - Webhook handler
  - Refund automation
  - Fraud detection integration

Supported Gateways:
  - Stripe
  - PayPal
  - Razorpay
  - Square

Security:
  - No card data storage
  - Token-based processing
  - TLS 1.3 encryption
  - Audit logging
```

### 6. 📧 **Notification Service**
**Responsibility**: Multi-channel communication

```yaml
Channels:
  - Email (SendGrid/SES)
  - SMS (Twilio/SNS)
  - Push notifications (FCM/APNS)
  - In-app messages

Templates:
  - Booking confirmation
  - Payment receipt
  - Event reminders
  - Cancellation notices
  - Promotional campaigns

Delivery:
  - Async queue processing
  - Retry mechanism
  - Delivery tracking
  - Unsubscribe management
```

---

## 📊 Data Model

### 🗂️ Entity Relationship Diagram

```
┌─────────────┐          ┌─────────────┐          ┌─────────────┐
│    USER     │          │   VENUE     │          │  CATEGORY   │
├─────────────┤          ├─────────────┤          ├─────────────┤
│ id          │          │ id          │          │ id          │
│ email       │          │ name        │          │ name        │
│ name        │          │ address     │          │ icon        │
│ phone       │          │ capacity    │          │ description │
│ created_at  │          │ latitude    │          └─────────────┘
└──────┬──────┘          │ longitude   │                 │
       │                 │ timezone    │                 │
       │                 └──────┬──────┘                 │
       │                        │                        │
       │                        │                        │
       │                 ┌──────▼──────┐                 │
       │                 │    EVENT    │◄────────────────┘
       │                 ├─────────────┤
       │                 │ id          │
       │                 │ title       │
       │                 │ description │
       │                 │ venue_id    │
       │                 │ category_id │
       │                 │ start_time  │
       │                 │ end_time    │
       │                 │ status      │
       │                 └──────┬──────┘
       │                        │
       │                        │
       │                 ┌──────▼──────┐
       │                 │   SECTION   │
       │                 ├─────────────┤
       │                 │ id          │
       │                 │ event_id    │
       │                 │ name        │
       │                 │ base_price  │
       │                 └──────┬──────┘
       │                        │
       │                        │
       │                 ┌──────▼──────┐
       │                 │     ROW     │
       │                 ├─────────────┤
       │                 │ id          │
       │                 │ section_id  │
       │                 │ row_number  │
       │                 └──────┬──────┘
       │                        │
       │                        │
       │                 ┌──────▼──────┐
       │           ┌─────┤    SEAT     │
       │           │     ├─────────────┤
       │           │     │ id          │
       │           │     │ row_id      │
       │           │     │ seat_number │
       │           │     │ status      │───┐
       │           │     │ version     │   │ (AVAILABLE, HELD, BOOKED)
       │           │     │ price       │   │
       │           │     └─────────────┘   │
       │           │                       │
       │           │                       │
       │     ┌─────▼─────────┐             │
       │     │  RESERVATION  │◄────────────┘
       │     ├───────────────┤
       │     │ id            │
       └─────┤ user_id       │
             │ seat_id       │
             │ status        │─── (PENDING, CONFIRMED, EXPIRED, CANCELLED)
             │ expires_at    │
             │ created_at    │
             └───────┬───────┘
                     │
                     │ (1 reservation → 1 order after payment)
                     │
             ┌───────▼───────┐
             │     ORDER     │
             ├───────────────┤
             │ id            │
             │ user_id       │
             │ reservation_id│
             │ total_amount  │
             │ status        │─── (PENDING, PAID, FAILED, REFUNDED)
             │ created_at    │
             │ confirmed_at  │
             └───────┬───────┘
                     │
                     │
             ┌───────▼────────┐
             │ PAYMENT_RECORD │
             ├────────────────┤
             │ id             │
             │ order_id       │
             │ gateway        │─── (stripe, paypal, etc.)
             │ transaction_id │
             │ amount         │
             │ currency       │
             │ status         │
             │ idempotency_key│
             │ created_at     │
             └────────────────┘
```

### 📋 Key Database Tables

#### **seats** (Inventory Table - Sharded)
```sql
CREATE TABLE seats (
    id              BIGSERIAL PRIMARY KEY,
    event_id        BIGINT NOT NULL,
    row_id          BIGINT NOT NULL,
    seat_number     VARCHAR(10) NOT NULL,
    section_id      BIGINT NOT NULL,
    price           DECIMAL(10,2) NOT NULL,
    status          VARCHAR(20) NOT NULL DEFAULT 'AVAILABLE',
    version         BIGINT NOT NULL DEFAULT 0,  -- Optimistic locking
    held_by         BIGINT,
    held_until      TIMESTAMP,
    booked_by       BIGINT,
    booked_at       TIMESTAMP,
    created_at      TIMESTAMP DEFAULT NOW(),
    updated_at      TIMESTAMP DEFAULT NOW(),
    
    UNIQUE(event_id, row_id, seat_number),
    INDEX idx_event_status (event_id, status),
    INDEX idx_held_until (held_until) WHERE status = 'HELD',
    
    CHECK (status IN ('AVAILABLE', 'HELD', 'BOOKED', 'BLOCKED'))
);
```

#### **reservations** (Hold Management)
```sql
CREATE TABLE reservations (
    id                      UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    client_reservation_id   UUID NOT NULL,  -- Idempotency
    user_id                 BIGINT NOT NULL,
    event_id                BIGINT NOT NULL,
    seat_ids                BIGINT[] NOT NULL,
    status                  VARCHAR(20) NOT NULL DEFAULT 'PENDING',
    total_price             DECIMAL(10,2) NOT NULL,
    expires_at              TIMESTAMP NOT NULL,
    created_at              TIMESTAMP DEFAULT NOW(),
    updated_at              TIMESTAMP DEFAULT NOW(),
    committed_at            TIMESTAMP,
    
    UNIQUE(client_reservation_id),
    INDEX idx_user_active (user_id, status) WHERE status IN ('PENDING', 'HELD'),
    INDEX idx_expiry (expires_at) WHERE status = 'HELD'
);
```

#### **orders** (Confirmed Bookings)
```sql
CREATE TABLE orders (
    id                  BIGSERIAL PRIMARY KEY,
    order_number        VARCHAR(20) UNIQUE NOT NULL,
    user_id             BIGINT NOT NULL,
    reservation_id      UUID NOT NULL REFERENCES reservations(id),
    event_id            BIGINT NOT NULL,
    total_amount        DECIMAL(10,2) NOT NULL,
    currency            VARCHAR(3) DEFAULT 'USD',
    status              VARCHAR(20) NOT NULL DEFAULT 'PENDING',
    payment_status      VARCHAR(20),
    created_at          TIMESTAMP DEFAULT NOW(),
    confirmed_at        TIMESTAMP,
    
    INDEX idx_user_orders (user_id, created_at DESC),
    INDEX idx_event_orders (event_id, created_at DESC)
);
```

---

## 🔌 API Design

### 🔍 **Event Discovery**

#### List Events
```http
GET /api/v1/events?from=2024-01-01&to=2024-12-31&category=concerts&city=New York&page=1&limit=20

Response 200 OK:
{
  "data": [
    {
      "id": 12345,
      "title": "Taylor Swift - The Eras Tour",
      "description": "...",
      "venue": {
        "id": 1,
        "name": "Madison Square Garden",
        "city": "New York",
        "capacity": 20000
      },
      "category": "Concert",
      "start_time": "2024-06-15T19:00:00Z",
      "status": "on_sale",
      "price_range": {
        "min": 49.99,
        "max": 499.99
      },
      "availability": {
        "total_seats": 20000,
        "available_seats": 15420
      }
    }
  ],
  "meta": {
    "total": 156,
    "page": 1,
    "limit": 20
  }
}
```

### 🗺️ **Seat Map**

#### Get Seat Map with Availability
```http
GET /api/v1/events/12345/seatmap

Response 200 OK:
{
  "event_id": 12345,
  "venue_id": 1,
  "layout_version": "v2.1",
  "sections": [
    {
      "id": "FLOOR",
      "name": "Floor Section",
      "price": 299.99,
      "rows": [
        {
          "row_number": "A",
          "seats": [
            {
              "id": 1001,
              "seat_number": "1",
              "status": "available",
              "price": 299.99
            },
            {
              "id": 1002,
              "seat_number": "2",
              "status": "held",
              "price": 299.99
            },
            {
              "id": 1003,
              "seat_number": "3",
              "status": "booked",
              "price": 299.99
            }
          ]
        }
      ]
    }
  ],
  "last_updated": "2024-01-15T10:30:00Z"
}
```

### 🎫 **Reservation Flow**

#### Create Reservation (Hold Seats)
```http
POST /api/v1/events/12345/reservations
Authorization: Bearer <jwt_token>

Request Body:
{
  "client_reservation_id": "550e8400-e29b-41d4-a716-446655440000",
  "seat_ids": [1001, 1005, 1006],
  "ttl_seconds": 600
}

Response 201 Created:
{
  "reservation_id": "abc123-def456-ghi789",
  "status": "held",
  "seats": [
    {
      "id": 1001,
      "section": "FLOOR",
      "row": "A",
      "number": "1",
      "price": 299.99
    }
  ],
  "total_price": 899.97,
  "currency": "USD",
  "expires_at": "2024-01-15T10:40:00Z",
  "created_at": "2024-01-15T10:30:00Z"
}

Response 409 Conflict:
{
  "error": "seat_unavailable",
  "message": "One or more seats are no longer available",
  "unavailable_seats": [1001],
  "available_alternatives": [1010, 1011, 1012]
}

Response 429 Too Many Requests:
{
  "error": "rate_limit_exceeded",
  "message": "You are in queue. Please wait.",
  "queue_position": 1247,
  "estimated_wait_seconds": 45
}
```

#### Extend Reservation
```http
PATCH /api/v1/reservations/abc123-def456-ghi789/extend
Authorization: Bearer <jwt_token>

Request Body:
{
  "additional_seconds": 300
}

Response 200 OK:
{
  "reservation_id": "abc123-def456-ghi789",
  "expires_at": "2024-01-15T10:45:00Z",
  "extensions_remaining": 0
}
```

### 💳 **Payment & Commit**

#### Commit Reservation (Process Payment)
```http
POST /api/v1/reservations/abc123-def456-ghi789/commit
Authorization: Bearer <jwt_token>

Request Body:
{
  "payment_method_id": "pm_1234567890",
  "idempotency_key": "pay_550e8400-e29b-41d4-a716-446655440000",
  "billing_details": {
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "+1234567890"
  }
}

Response 200 OK:
{
  "order_id": "ORD-2024-001234",
  "status": "confirmed",
  "payment": {
    "transaction_id": "ch_1234567890",
    "amount": 899.97,
    "currency": "USD",
    "gateway": "stripe",
    "status": "succeeded"
  },
  "tickets": [
    {
      "ticket_number": "TKT-2024-001234-001",
      "seat": "FLOOR-A-1",
      "qr_code": "https://tickets.example.com/qr/TKT-2024-001234-001"
    }
  ],
  "confirmed_at": "2024-01-15T10:35:00Z"
}

Response 410 Gone:
{
  "error": "reservation_expired",
  "message": "Reservation has expired. Please create a new reservation.",
  "expired_at": "2024-01-15T10:40:00Z"
}

Response 402 Payment Required:
{
  "error": "payment_failed",
  "message": "Payment could not be processed",
  "reason": "insufficient_funds",
  "reservation_id": "abc123-def456-ghi789",
  "retry_allowed": true
}
```

#### Get Order Details
```http
GET /api/v1/orders/ORD-2024-001234
Authorization: Bearer <jwt_token>

Response 200 OK:
{
  "order_number": "ORD-2024-001234",
  "event": {
    "title": "Taylor Swift - The Eras Tour",
    "date": "2024-06-15T19:00:00Z",
    "venue": "Madison Square Garden"
  },
  "tickets": [...],
  "total_amount": 899.97,
  "status": "confirmed",
  "created_at": "2024-01-15T10:35:00Z"
}
```

---

## 🛡️ Consistency Guarantees

### 🔒 **Optimistic Locking with Compare-And-Swap (CAS)**

The cornerstone of our zero-oversell guarantee is **optimistic concurrency control**.

#### **How It Works**

```sql
-- Step 1: Read current state
SELECT id, status, version 
FROM seats 
WHERE id = 1001 AND event_id = 12345;

-- Result: status='AVAILABLE', version=5

-- Step 2: Attempt to hold seat with version check
UPDATE seats
SET 
    status = 'HELD',
    held_by = 987654,  -- user_id
    held_until = NOW() + INTERVAL '10 minutes',
    version = version + 1,
    updated_at = NOW()
WHERE 
    id = 1001 
    AND status = 'AVAILABLE'   -- Must still be available
    AND version = 5;           -- Version must match

-- Step 3: Check affected rows
-- rows_affected = 1  ✅ Success! You got the seat
-- rows_affected = 0  ❌ Conflict! Someone else grabbed it
```

#### **Concurrent Conflict Scenario**

```
Timeline:
─────────────────────────────────────────────────────────────
User A                          User B
─────────────────────────────────────────────────────────────
T0: Read seat (v=5)             
                                T1: Read seat (v=5)
T2: Update (v=5 → v=6) ✅       
                                T3: Update (v=5 → v=6) ❌
                                    FAILS! Version mismatch
                                    → Retry or notify user
```

### 🎯 **Distributed Coordination**

For multi-node deployments, we use **distributed locks**:

```python
# Pseudocode: Redlock implementation
def reserve_seat(seat_id, user_id):
    lock_key = f"seat:lock:{seat_id}"
    lock_ttl = 10  # seconds
    
    # Acquire distributed lock
    lock_acquired = redis.set(
        lock_key, 
        user_id, 
        nx=True,    # Only set if not exists
        ex=lock_ttl # Expire after 10s
    )
    
    if not lock_acquired:
        return {"error": "seat_locked_by_another_user"}
    
    try:
        # Perform CAS operation
        result = db.execute("""
            UPDATE seats 
            SET status='HELD', version=version+1
            WHERE seat_id=? AND status='AVAILABLE' AND version=?
        """, [seat_id, current_version])
        
        if result.rows_affected == 1:
            return {"success": True}
        else:
            return {"error": "seat_already_taken"}
    finally:
        # Release lock
        redis.delete(lock_key)
```

### 🔄 **Saga Pattern for Distributed Transactions**

Payment commit follows the **Saga pattern**:

```
1. BEGIN SAGA: Commit Reservation
   │
   ├─→ 2. Charge Payment
   │      ├─ Success ✅ → Continue
   │      └─ Failure ❌ → Compensate (release seats)
   │
   ├─→ 3. Update Seat Status (HELD → BOOKED)
   │      ├─ Success ✅ → Continue
   │      └─ Failure ❌ → Compensate (refund payment)
   │
   ├─→ 4. Create Order Record
   │      ├─ Success ✅ → Continue
   │      └─ Failure ❌ → Compensate (rollback all)
   │
   └─→ 5. Send Confirmation
          └─ Fire-and-forget (async)
```

---

## ⚡ Performance Optimization

### 🚀 **Caching Strategy**

#### **Multi-Layer Caching**

```
┌─────────────────────────────────────────────────┐
│ Layer 1: CDN (CloudFlare)                       │
│ • Static assets (images, CSS, JS)               │
│ • Event catalog pages (60s TTL)                 │
│ • TTL: 1-5 minutes                              │
└──────────────┬──────────────────────────────────┘
               │ Cache Miss
               ▼
┌─────────────────────────────────────────────────┐
│ Layer 2: Application Cache (Redis)              │
│ • Seat map layouts (15s TTL)                    │
│ • User sessions (15m TTL)                       │
│ • Rate limit counters (1m TTL)                  │
│ • Hot event data (30s TTL)                      │
└──────────────┬──────────────────────────────────┘
               │ Cache Miss
               ▼
┌─────────────────────────────────────────────────┐
│ Layer 3: Database Query Cache                   │
│ • Materialized views                            │
│ • Query result caching                          │
└──────────────┬──────────────────────────────────┘
               │ Cache Miss
               ▼
┌─────────────────────────────────────────────────┐
│ Layer 4: Primary Database (PostgreSQL)          │
└─────────────────────────────────────────────────┘
```

#### **Cache Invalidation Strategy**

```python
# Event-driven cache invalidation
def on_seat_status_change(seat_id, event_id, section_id):
    # Invalidate specific cache keys
    redis.delete(f"seat:{seat_id}")
    redis.delete(f"section:{section_id}:availability")
    
    # Publish real-time update
    redis.publish(f"seat:update:{event_id}:{section_id}", {
        "seat_id": seat_id,
        "new_status": "HELD",
        "timestamp": time.now()
    })
    
    # Update counter cache
    redis.decr(f"event:{event_id}:available_count")
```

### 📊 **Database Optimization**

#### **Sharding Strategy**

```
Shard Key: event_id % num_shards

Example with 8 shards:
┌─────────────────────────────────────────────┐
│ Shard 0: Events 0, 8, 16, 24, ...           │
│ Shard 1: Events 1, 9, 17, 25, ...           │
│ Shard 2: Events 2, 10, 18, 26, ...          │
│ Shard 3: Events 3, 11, 19, 27, ...          │
│ Shard 4: Events 4, 12, 20, 28, ...          │
│ Shard 5: Events 5, 13, 21, 29, ...          │
│ Shard 6: Events 6, 14, 22, 30, ...          │
│ Shard 7: Events 7, 15, 23, 31, ...          │
└─────────────────────────────────────────────┘

Benefits:
✅ Horizontal scalability
✅ Isolated blast radius
✅ Parallel query execution
✅ Even load distribution
```

#### **Indexing Strategy**

```sql
-- Composite indexes for common queries
CREATE INDEX idx_seats_event_status 
ON seats(event_id, status) 
INCLUDE (seat_number, price);

-- Partial indexes for specific states
CREATE INDEX idx_held_seats_expiry 
ON seats(held_until) 
WHERE status = 'HELD';

-- Covering indexes to avoid table lookups
CREATE INDEX idx_event_catalog 
ON events(start_time, status) 
INCLUDE (title, venue_id, price_range);
```

### ⚡ **Connection Pooling**

```yaml
Database Connection Pool:
  Min Connections: 20
  Max Connections: 100
  Connection Timeout: 5s
  Idle Timeout: 10m
  Max Lifetime: 1h
  
Redis Connection Pool:
  Min Connections: 10
  Max Connections: 50
  Read Timeout: 1s
  Write Timeout: 1s
```

---

## 🎪 Flash Sale Strategy

### 🚦 **Admission Queue System**

When demand exceeds capacity, users enter a **virtual waiting room**:

```
┌─────────────────────────────────────────────────────┐
│          FLASH SALE ADMISSION FLOW                  │
└─────────────────────────────────────────────────────┘

1. User arrives at event page
   │
   ▼
2. Check: Is flash sale active?
   │
   ├─ NO  → Direct access ✅
   │
   └─ YES → Enter admission queue
             │
             ▼
3. Assign queue position + token
   │
   ▼
4. Wait in virtual waiting room
   │ (Real-time position updates via WebSocket)
   │
   ▼
5. Position reaches front of queue
   │
   ▼
6. Grant temporary access token (15 min TTL)
   │
   ▼
7. User can now browse & reserve seats
```

### 🎟️ **Token-Based Fairness**

```python
# Token generation
def generate_queue_token(user_id, event_id):
    position = redis.rpush(f"queue:{event_id}", user_id)
    token = jwt.encode({
        "user_id": user_id,
        "event_id": event_id,
        "queue_position": position,
        "joined_at": time.now(),
        "exp": time.now() + 3600  # 1 hour expiry
    }, secret_key)
    return token, position

# Admission control
def admit_next_batch(event_id, batch_size=100):
    for _ in range(batch_size):
        user_id = redis.lpop(f"queue:{event_id}")
        if user_id:
            access_token = generate_access_token(user_id, event_id)
            redis.setex(
                f"access:{event_id}:{user_id}",
                900,  # 15 minutes
                access_token
            )
            notify_user(user_id, "Your turn! Access granted.")
```

### 📊 **Rate Limiting**

```yaml
Rate Limits:
  Global:
    - 10,000 req/sec across all services
    
  Per User:
    - Browse: 100 req/min
    - Reserve: 10 req/min
    - Commit: 5 req/min
    
  Per IP:
    - 300 req/min (anti-bot)
    
  Per Event (Hot Events):
    - Reservation: 500 req/sec
    - Commit: 200 req/sec

Implementation:
  - Token bucket algorithm
  - Distributed rate limiting (Redis)
  - Sliding window counters
```

### 🛡️ **Anti-Bot Measures**

```yaml
Protection Layers:
  1. CAPTCHA:
     - reCAPTCHA v3 (invisible)
     - Triggered on suspicious activity
     
  2. Device Fingerprinting:
     - Browser fingerprinting
     - Detect automation tools
     
  3. Behavioral Analysis:
     - Mouse movement patterns
     - Keystroke dynamics
     - Session duration
     
  4. IP Reputation:
     - Blacklist known bot IPs
     - VPN/proxy detection
     
  5. Account Limits:
     - Max 4 tickets per transaction
     - Max 8 tickets per event per user
```

---

## 💾 Caching Architecture

### 🎯 **Cache Aside Pattern**

```python
def get_seat_map(event_id):
    # Try cache first
    cache_key = f"seatmap:{event_id}"
    cached_data = redis.get(cache_key)
    
    if cached_data:
        return json.loads(cached_data)
    
    # Cache miss - fetch from DB
    seat_map = db.query("SELECT * FROM seats WHERE event_id = ?", event_id)
    
    # Store in cache (15s TTL)
    redis.setex(
        cache_key,
        15,
        json.dumps(seat_map)
    )
    
    return seat_map
```

### 🔄 **Write-Through Caching**

```python
def update_seat_status(seat_id, new_status):
    # Update database
    db.execute("""
        UPDATE seats 
        SET status = ?, updated_at = NOW()
        WHERE id = ?
    """, [new_status, seat_id])
    
    # Update cache immediately
    redis.hset(f"seat:{seat_id}", "status", new_status)
    
    # Publish change event
    redis.publish(f"seat:changed", {
        "seat_id": seat_id,
        "status": new_status
    })
```

### 📡 **Real-Time Updates via Pub/Sub**

```javascript
// Client-side WebSocket subscription
const ws = new WebSocket('wss://api.example.com/ws');

ws.on('open', () => {
  // Subscribe to seat updates for specific event
  ws.send(JSON.stringify({
    action: 'subscribe',
    channel: 'seat:updates',
    event_id: 12345
  }));
});

ws.on('message', (data) => {
  const update = JSON.parse(data);
  // Update UI instantly
  updateSeatOnMap(update.seat_id, update.status);
});
```

```python
# Server-side Redis Pub/Sub
def publish_seat_update(seat_id, event_id, section_id, status):
    redis.publish(f"seat:update:{event_id}", {
        "seat_id": seat_id,
        "section_id": section_id,
        "status": status,
        "timestamp": time.now()
    })

# WebSocket server broadcasts to connected clients
async def redis_subscriber():
    pubsub = redis.pubsub()
    pubsub.subscribe("seat:update:*")
    
    for message in pubsub.listen():
        event_id = extract_event_id(message['channel'])
        await broadcast_to_clients(event_id, message['data'])
```

---

## 💳 Payment Processing

### 🔐 **Payment Flow**

```
┌──────────────────────────────────────────────────────┐
│             PAYMENT PROCESSING FLOW                   │
└──────────────────────────────────────────────────────┘

1. User initiates payment
   │
   ▼
2. Frontend collects payment method (tokenized)
   │ (No card data touches our servers - PCI compliant)
   │
   ▼
3. Backend receives payment_method_token
   │
   ▼
4. Generate idempotency_key
   │ (Prevents duplicate charges on retries)
   │
   ▼
5. Create Payment Intent with gateway
   │
   ├─ Success ✅
   │  │
   │  ▼
   │  6. Charge payment
   │     │
   │     ├─ Success ✅
   │     │  │
   │     │  ▼
   │     │  7. Atomically:
   │     │     - Update seat status (HELD → BOOKED)
   │     │     - Create order record
   │     │     - Store payment record
   │     │     - Delete reservation hold
   │     │  │
   │     │  ▼
   │     │  8. Generate tickets
   │     │  │
   │     │  ▼
   │     │  9. Send confirmation (async)
   │     │  │
   │     │  └─ COMPLETE ✅
   │     │
   │     └─ Failure ❌
   │        │
   │        ▼
   │        Retry logic (exponential backoff)
   │        │
   │        └─ Max retries exceeded
   │           │
   │           ▼
   │           Release seats
   │           Notify user
   │
   └─ Failure ❌
      │
      └─ Return error to user
```

### 🔁 **Idempotency Implementation**

```python
def process_payment(reservation_id, payment_method_id, idempotency_key):
    # Check if already processed
    existing_payment = db.query("""
        SELECT * FROM payment_records 
        WHERE idempotency_key = ?
    """, [idempotency_key])
    
    if existing_payment:
        # Already processed - return cached result
        return {
            "status": "success",
            "order_id": existing_payment.order_id,
            "cached": True
        }
    
    # First time processing
    try:
        # Charge payment
        charge = stripe.charge.create(
            amount=reservation.total_price,
            currency="usd",
            payment_method=payment_method_id,
            idempotency_key=idempotency_key
        )
        
        # Atomic database transaction
        with db.transaction():
            # Create order
            order = create_order(reservation_id)
            
            # Store payment record
            create_payment_record(
                order_id=order.id,
                transaction_id=charge.id,
                idempotency_key=idempotency_key
            )
            
            # Update seat status
            update_seats_to_booked(reservation.seat_ids)
            
            # Delete reservation
            delete_reservation(reservation_id)
        
        return {"status": "success", "order_id": order.id}
        
    except PaymentError as e:
        # Log and return error
        log_payment_failure(reservation_id, e)
        return {"status": "failed", "error": e.message}
```

### 🔔 **Webhook Handling**

```python
@app.route('/webhooks/stripe', methods=['POST'])
def stripe_webhook():
    payload = request.get_data()
    sig_header = request.headers.get('Stripe-Signature')
    
    try:
        # Verify webhook signature
        event = stripe.Webhook.construct_event(
            payload, sig_header, webhook_secret
        )
    except ValueError:
        return "Invalid payload", 400
    except stripe.error.SignatureVerificationError:
        return "Invalid signature", 400
    
    # Handle event
    if event.type == 'payment_intent.succeeded':
        payment_intent = event.data.object
        confirm_order(payment_intent.id)
        
    elif event.type == 'payment_intent.payment_failed':
        payment_intent = event.data.object
        handle_payment_failure(payment_intent.id)
    
    return "Success", 200

def confirm_order(payment_intent_id):
    # Idempotent order confirmation
    order = db.query("""
        SELECT * FROM orders 
        WHERE payment_intent_id = ?
    """, [payment_intent_id])
    
    if order.status == 'confirmed':
        return  # Already confirmed
    
    db.execute("""
        UPDATE orders 
        SET status = 'confirmed', confirmed_at = NOW()
        WHERE payment_intent_id = ?
    """, [payment_intent_id])
    
    # Trigger ticket generation
    generate_tickets(order.id)
    send_confirmation_email(order.id)
```

---

## 📈 Scalability & Capacity

### 🎯 **Capacity Planning**

```yaml
Target Metrics:
  Concurrent Users: 100,000
  Daily Active Users: 1,000,000
  Peak Events: 50 simultaneous hot sales
  
Database Capacity:
  Shards: 16 (PostgreSQL)
  Reads/sec per shard: 10,000
  Writes/sec per shard: 2,000
  Total DB capacity: 160K reads/sec, 32K writes/sec
  
Cache Capacity:
  Redis Cluster Nodes: 8
  Memory per node: 64 GB
  Total cache capacity: 512 GB
  Operations/sec: 500,000+
  
API Gateway:
  Instances: Auto-scaled (10-100)
  Requests/sec per instance: 1,000
  Total capacity: 100,000 req/sec
  
Message Queue:
  Kafka Partitions: 32
  Throughput: 1M messages/sec
  Retention: 7 days
```

### 📊 **Horizontal Scaling**

```
Service Replicas (Kubernetes):

┌────────────────────────────────────────────────┐
│ Service          │ Min │ Max │ CPU Target      │
├────────────────────────────────────────────────┤
│ API Gateway      │  3  │ 20  │ 70%             │
│ Catalog Service  │  2  │ 10  │ 60%             │
│ Seat Map Service │  5  │ 30  │ 75% (hot path)  │
│ Reservation Svc  │  3  │ 25  │ 80%             │
│ Payment Service  │  2  │ 15  │ 70%             │
│ Notification Svc │  2  │  8  │ 50%             │
└────────────────────────────────────────────────┘

Autoscaling Triggers:
- CPU utilization > target
- Request queue depth > 100
- Response time p95 > 500ms
```

### 🌍 **Multi-Region Deployment**

```
┌───────────────────────────────────────────────────┐
│         GLOBAL ARCHITECTURE                       │
└───────────────────────────────────────────────────┘

Region: US-East (Primary)
  - Full read/write capability
  - Master database
  - Active traffic handling
  
Region: US-West (Hot Standby)
  - Read replicas
  - Failover ready
  - Disaster recovery
  
Region: EU-West (Active)
  - Regional events
  - Local database shard
  - CDN edge locations
  
Region: Asia-Pacific (Active)
  - Regional events
  - Local database shard
  - CDN edge locations

Database Replication:
  - Master-Slave (streaming replication)
  - Cross-region lag: < 100ms
  - Automatic failover (3-5 min RTO)
```

---

## 🔧 Failure Recovery

### 🛡️ **Failure Scenarios & Mitigation**

| Failure Type | Impact | Detection | Recovery | Prevention |
|--------------|--------|-----------|----------|------------|
| **Database Node Down** | Partial outage | Health check (5s interval) | Failover to replica (30s) | Multi-AZ deployment, replicas |
| **Cache Eviction** | Performance degradation | Cache miss rate spike | Rebuild from DB | Persistent cache, larger memory |
| **Payment Gateway Timeout** | Transaction pending | Webhook delayed | Reconciliation job | Retry + idempotency |
| **Oversell Bug** | Data corruption | Monitoring alert | Manual correction + refund | CAS + constraints |
| **Coordinator Crash** | Reservation delays | Leader election timeout | Raft re-election (2-5s) | Redundant nodes (N=3 or 5) |
| **Network Partition** | Split-brain risk | Consensus failure | Quorum-based recovery | Distributed consensus |
| **TTL Worker Failure** | Seats stuck in HELD | Expiry backlog metric | Redundant workers | Multiple worker instances |

### 🔄 **Retry Strategy**

```python
from tenacity import retry, stop_after_attempt, wait_exponential

@retry(
    stop=stop_after_attempt(3),
    wait=wait_exponential(multiplier=1, min=1, max=10)
)
def call_payment_gateway(payment_data):
    response = stripe.charge.create(**payment_data)
    return response

# Exponential backoff
# Attempt 1: immediate
# Attempt 2: wait 1s
# Attempt 3: wait 2s
# Attempt 4: fail
```

### 🔁 **Circuit Breaker**

```python
from circuitbreaker import circuit

@circuit(failure_threshold=5, recovery_timeout=60)
def call_external_service(data):
    response = requests.post(external_api_url, json=data)
    return response.json()

# States:
# - CLOSED: Normal operation
# - OPEN: Too many failures, reject requests immediately
# - HALF_OPEN: Test if service recovered
```

### 📊 **Health Checks**

```yaml
Kubernetes Liveness Probe:
  path: /health/live
  interval: 10s
  timeout: 2s
  failure_threshold: 3
  
Kubernetes Readiness Probe:
  path: /health/ready
  interval: 5s
  timeout: 2s
  failure_threshold: 2

Health Check Endpoints:
  /health/live:
    - Service is running
    - Returns 200 OK
    
  /health/ready:
    - Database connection: OK
    - Redis connection: OK
    - Kafka connection: OK
    - Dependency services: OK
```

---

## 📊 Monitoring & Observability

### 📈 **Key Metrics**

```yaml
Business Metrics:
  - Reservation Success Rate (target: >95%)
  - Average Checkout Time (target: <30s)
  - Revenue per Hour
  - Ticket Sales Velocity
  - Cart Abandonment Rate
  - Customer Satisfaction Score

Technical Metrics:
  - Request Throughput (req/sec)
  - Latency Percentiles (p50, p95, p99)
  - Error Rate (4xx, 5xx)
  - Database Query Time
  - Cache Hit Ratio (target: >90%)
  - Queue Depth
  - Worker Lag

Infrastructure Metrics:
  - CPU Utilization
  - Memory Usage
  - Network I/O
  - Disk I/O
  - Connection Pool Saturation
```

### 🚨 **Alerting Rules**

```yaml
Critical Alerts (PagerDuty):
  - Overselling Detected:
      condition: oversell_count > 0
      severity: P1
      
  - Payment Success Rate < 90%:
      condition: payment_success_rate < 0.9
      window: 5m
      severity: P1
      
  - API Error Rate > 5%:
      condition: error_rate > 0.05
      window: 2m
      severity: P1

Warning Alerts (Slack):
  - High Latency:
      condition: p95_latency > 1s
      window: 5m
      severity: P2
      
  - Cache Hit Rate < 80%:
      condition: cache_hit_rate < 0.8
      window: 10m
      severity: P3
      
  - Queue Depth > 1000:
      condition: queue_depth > 1000
      severity: P2
```

### 📊 **Dashboards**

```yaml
Real-Time Operations Dashboard:
  - Live sales counter
  - Active reservation count
  - Current queue depth
  - System health status
  - Top selling events

Performance Dashboard:
  - Request rate (time series)
  - Latency distribution (heatmap)
  - Error rate by endpoint
  - Database query performance

Business Intelligence Dashboard:
  - Revenue trends
  - Popular events
  - Geographic distribution
  - Customer segments
  - Conversion funnel
```

### 🔍 **Distributed Tracing**

```yaml
Tracing Stack:
  - Instrumentation: OpenTelemetry
  - Backend: Jaeger / Tempo
  - Sampling: 1% production, 100% errors

Trace Example:
  Request ID: abc123-def456
  │
  ├─ API Gateway (5ms)
  │  │
  │  ├─ Auth Middleware (2ms)
  │  └─ Rate Limit Check (1ms)
  │
  ├─ Reservation Service (450ms)
  │  │
  │  ├─ Check Cache (5ms) - MISS
  │  │
  │  ├─ Database Query (200ms)
  │  │
  │  ├─ Acquire Lock (50ms)
  │  │
  │  └─ CAS Update (180ms)
  │
  └─ Total: 455ms
```

### 📝 **Structured Logging**

```json
{
  "timestamp": "2024-01-15T10:30:00.123Z",
  "level": "INFO",
  "service": "reservation-service",
  "trace_id": "abc123-def456",
  "span_id": "xyz789",
  "event": "reservation_created",
  "user_id": 987654,
  "event_id": 12345,
  "seat_ids": [1001, 1002],
  "duration_ms": 450,
  "metadata": {
    "client_ip": "203.0.113.45",
    "user_agent": "Mozilla/5.0...",
    "region": "us-east-1"
  }
}
```

---

## 🧪 Testing Strategy

### 🎯 **Testing Pyramid**

```
                    ╱╲
                   ╱  ╲
                  ╱ E2E╲          (10% - End-to-End Tests)
                 ╱──────╲
                ╱        ╲
               ╱Integration╲      (30% - Integration Tests)
              ╱────────────╲
             ╱              ╲
            ╱  Unit Tests    ╲    (60% - Unit Tests)
           ╱──────────────────╲
          ╱____________________╲
```

### 🧩 **Test Categories**

#### 1️⃣ **Unit Tests** (60%)
```python
# Example: Testing CAS logic
def test_optimistic_locking_success():
    seat = create_test_seat(status='AVAILABLE', version=1)
    result = reserve_seat(seat.id, user_id=123, expected_version=1)
    
    assert result.success == True
    assert seat.status == 'HELD'
    assert seat.version == 2

def test_optimistic_locking_conflict():
    seat = create_test_seat(status='AVAILABLE', version=1)
    
    # Simulate concurrent update (version changed)
    update_seat_version(seat.id, version=2)
    
    result = reserve_seat(seat.id, user_id=123, expected_version=1)
    
    assert result.success == False
    assert result.error == 'version_mismatch'
```

**Coverage Target**: > 80%

#### 2️⃣ **Integration Tests** (30%)
```python
@pytest.mark.integration
def test_reservation_to_payment_flow():
    # Create event and seats
    event = create_test_event()
    seats = create_test_seats(event.id, count=5)
    
    # Step 1: Reserve seats
    response = api_client.post(f'/events/{event.id}/reservations', {
        'seat_ids': [seats[0].id, seats[1].id],
        'ttl_seconds': 300
    })
    assert response.status_code == 201
    reservation_id = response.json()['reservation_id']
    
    # Step 2: Process payment
    payment_response = api_client.post(
        f'/reservations/{reservation_id}/commit',
        {'payment_method_id': 'pm_test_card'}
    )
    assert payment_response.status_code == 200
    
    # Step 3: Verify seats are booked
    seat_status = get_seat_status([seats[0].id, seats[1].id])
    assert all(s.status == 'BOOKED' for s in seat_status)
```

#### 3️⃣ **End-to-End Tests** (10%)
```javascript
// Example: Cypress E2E test
describe('Complete Booking Flow', () => {
  it('should book tickets successfully', () => {
    // Login
    cy.login('user@example.com', 'password123');
    
    // Browse events
    cy.visit('/events');
    cy.contains('Taylor Swift').click();
    
    // Select seats
    cy.get('[data-seat-id="A-10"]').click();
    cy.get('[data-seat-id="A-11"]').click();
    cy.contains('Reserve Seats').click();
    
    // Complete payment
    cy.get('input[name="card-number"]').type('4242424242424242');
    cy.get('input[name="expiry"]').type('12/25');
    cy.get('input[name="cvc"]').type('123');
    cy.contains('Complete Purchase').click();
    
    // Verify confirmation
    cy.contains('Booking Confirmed').should('be.visible');
    cy.get('[data-testid="ticket-qr"]').should('exist');
  });
});
```

### 🔥 **Load Testing**

```yaml
Tool: K6 (Grafana)

Scenarios:
  1. Browse Events:
     - Virtual Users: 10,000
     - Duration: 5 minutes
     - Expected p95: < 200ms
     
  2. Reserve Seats (Flash Sale):
     - Virtual Users: 50,000
     - Ramp-up: 30 seconds
     - Duration: 2 minutes
     - Expected: 20K req/sec peak
     - Success rate: > 80%
     
  3. Payment Processing:
     - Virtual Users: 5,000
     - Duration: 10 minutes
     - Expected p99: < 2s
     - Success rate: > 95%

Sample K6 Script:
```

```javascript
import http from 'k6/http';
import { check, sleep } from 'k6';

export let options = {
  stages: [
    { duration: '30s', target: 10000 },  // Ramp up
    { duration: '2m', target: 50000 },   // Peak load
    { duration: '30s', target: 0 },      // Ramp down
  ],
  thresholds: {
    http_req_duration: ['p95<500', 'p99<2000'],
    http_req_failed: ['rate<0.05'],
  },
};

export default function () {
  // Reserve seats
  const payload = JSON.stringify({
    client_reservation_id: `${__VU}-${__ITER}`,
    seat_ids: [1001, 1002],
    ttl_seconds: 300,
  });
  
  const response = http.post(
    'https://api.example.com/events/12345/reservations',
    payload,
    { headers: { 'Content-Type': 'application/json' } }
  );
  
  check(response, {
    'status is 201': (r) => r.status === 201,
    'reservation created': (r) => r.json('reservation_id') !== undefined,
  });
  
  sleep(1);
}
```

### 🧨 **Chaos Engineering**

```yaml
Tool: Chaos Mesh / Litmus

Experiments:
  1. Pod Failure:
     - Kill random service pods
     - Expected: Auto-recovery via Kubernetes
     - Downtime: < 30 seconds
     
  2. Network Latency:
     - Inject 500ms delay to database
     - Expected: Graceful degradation
     - User impact: Minimal
     
  3. Database Failover:
     - Terminate primary database node
     - Expected: Automatic failover to replica
     - Downtime: < 1 minute
     
  4. Cache Flush:
     - Clear all Redis cache
     - Expected: Performance degradation (no errors)
     - Recovery: Auto-repopulation
     
  5. Payment Gateway Timeout:
     - Simulate gateway unavailability
     - Expected: Retry mechanism + user notification
```

### ✅ **Contract Testing**

```yaml
Tool: Pact

Purpose: Ensure API contract compatibility

Example:
  Consumer: Frontend App
  Provider: Reservation Service
  
  Contract:
    - POST /reservations
      Request: { seat_ids: [int], ttl_seconds: int }
      Response: { reservation_id: string, expires_at: datetime }
```

---

## 🚀 Deployment Architecture

### ☸️ **Kubernetes Deployment**

```yaml
# reservation-service-deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: reservation-service
  namespace: ticketing-prod
spec:
  replicas: 5
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 2
      maxUnavailable: 1
  selector:
    matchLabels:
      app: reservation-service
  template:
    metadata:
      labels:
        app: reservation-service
        version: v1.5.2
    spec:
      containers:
      - name: reservation-service
        image: ticketing/reservation-service:v1.5.2
        ports:
        - containerPort: 8080
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: db-credentials
              key: url
        - name: REDIS_URL
          valueFrom:
            configMapKeyRef:
              name: cache-config
              key: redis-url
        resources:
          requests:
            memory: "512Mi"
            cpu: "500m"
          limits:
            memory: "1Gi"
            cpu: "1000m"
        livenessProbe:
          httpGet:
            path: /health/live
            port: 8080
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /health/ready
            port: 8080
          initialDelaySeconds: 10
          periodSeconds: 5
---
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: reservation-service-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: reservation-service
  minReplicas: 5
  maxReplicas: 30
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 75
  - type: Resource
    resource:
      name: memory
      target:
        type: Utilization
        averageUtilization: 80
  behavior:
    scaleUp:
      stabilizationWindowSeconds: 60
      policies:
      - type: Percent
        value: 100
        periodSeconds: 30
    scaleDown:
      stabilizationWindowSeconds: 300
      policies:
      - type: Pods
        value: 2
        periodSeconds: 60
```

### 🔄 **CI/CD Pipeline**

```yaml
# .github/workflows/deploy.yml
name: Deploy to Production

on:
  push:
    branches: [main]
    paths:
      - 'services/**'

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Run Unit Tests
        run: |
          npm install
          npm run test:unit
          
      - name: Run Integration Tests
        run: npm run test:integration
        
      - name: Code Coverage
        run: npm run coverage
        
  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Build Docker Image
        run: |
          docker build -t ticketing/reservation-service:${{ github.sha }} .
          
      - name: Security Scan
        run: |
          trivy image ticketing/reservation-service:${{ github.sha }}
          
      - name: Push to Registry
        run: |
          docker push ticketing/reservation-service:${{ github.sha }}
          
  deploy-staging:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to Staging
        run: |
          kubectl set image deployment/reservation-service \
            reservation-service=ticketing/reservation-service:${{ github.sha }} \
            -n ticketing-staging
            
      - name: Run E2E Tests
        run: npm run test:e2e:staging
        
  deploy-production:
    needs: deploy-staging
    runs-on: ubuntu-latest
    environment: production
    steps:
      - name: Blue-Green Deployment
        run: |
          # Deploy to green environment
          kubectl apply -f k8s/green-deployment.yaml
          
          # Wait for health checks
          kubectl wait --for=condition=ready pod \
            -l version=green -n ticketing-prod --timeout=300s
          
          # Switch traffic
          kubectl patch service reservation-service \
            -p '{"spec":{"selector":{"version":"green"}}}'
          
          # Monitor for 5 minutes
          sleep 300
          
          # If successful, delete blue
          kubectl delete deployment reservation-service-blue
```

### 🔵🟢 **Blue-Green Deployment**

```
Current State (Blue Active):
┌─────────────────────────────────────────┐
│ Load Balancer                           │
│ Routes 100% traffic to BLUE             │
└──────────────┬──────────────────────────┘
               │
               ▼
┌──────────────────────┐  ┌──────────────┐
│ BLUE (v1.5.1) ✅     │  │ GREEN (idle) │
│ • Active             │  │ • Standby    │
│ • Serving traffic    │  │              │
└──────────────────────┘  └──────────────┘

Deployment Step 1 (Deploy Green):
┌─────────────────────────────────────────┐
│ Load Balancer                           │
│ Routes 100% traffic to BLUE             │
└──────────────┬──────────────────────────┘
               │
               ▼
┌──────────────────────┐  ┌──────────────────────┐
│ BLUE (v1.5.1) ✅     │  │ GREEN (v1.5.2) 🆕    │
│ • Active             │  │ • Deploying          │
│ • Serving traffic    │  │ • Health checks      │
└──────────────────────┘  └──────────────────────┘

Deployment Step 2 (Switch Traffic):
┌─────────────────────────────────────────┐
│ Load Balancer                           │
│ Routes 100% traffic to GREEN ✅         │
└──────────────────────────────┬──────────┘
                               │
                               ▼
┌──────────────────────┐  ┌──────────────────────┐
│ BLUE (v1.5.1)        │  │ GREEN (v1.5.2) ✅    │
│ • Standby (rollback) │  │ • Active             │
│ • Can rollback       │  │ • Serving traffic    │
└──────────────────────┘  └──────────────────────┘

If GREEN fails → Instant rollback to BLUE
If GREEN succeeds → Delete BLUE after 30 min
```

### 🗄️ **Database Migration Strategy**

```python
# Using Alembic for migrations
# migrations/versions/001_add_version_column.py

def upgrade():
    # Add version column with default value
    op.add_column('seats', 
        sa.Column('version', sa.BigInteger(), 
                  nullable=False, 
                  server_default='0'))
    
    # Create index
    op.create_index('idx_seat_version', 'seats', ['id', 'version'])

def downgrade():
    op.drop_index('idx_seat_version')
    op.drop_column('seats', 'version')
```

**Migration Process:**
1. Deploy backward-compatible code
2. Run migration script
3. Deploy new code using new schema
4. Monitor for 24 hours
5. Remove backward-compatibility code

---

## 🔐 Security Measures

### 🛡️ **Security Layers**

```
┌─────────────────────────────────────────────────┐
│ Layer 1: Network Security                       │
│ • DDoS Protection (Cloudflare)                  │
│ • WAF (Web Application Firewall)                │
│ • Rate Limiting (IP-based)                      │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│ Layer 2: Authentication & Authorization         │
│ • JWT tokens (RS256)                            │
│ • OAuth 2.0 / OIDC                              │
│ • Role-Based Access Control (RBAC)              │
│ • Multi-Factor Authentication (MFA)             │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│ Layer 3: Application Security                   │
│ • Input Validation & Sanitization               │
│ • SQL Injection Prevention (Prepared Statements)│
│ • XSS Protection (Content Security Policy)      │
│ • CSRF Tokens                                   │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│ Layer 4: Data Security                          │
│ • Encryption at Rest (AES-256)                  │
│ • Encryption in Transit (TLS 1.3)               │
│ • PII Data Masking                              │
│ • Secure Key Management (AWS KMS / Vault)       │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│ Layer 5: Infrastructure Security                │
│ • VPC Isolation                                 │
│ • Security Groups / Network Policies            │
│ • Secrets Management (HashiCorp Vault)          │
│ • Regular Security Patches                      │
└─────────────────────────────────────────────────┘
```

### 🔑 **Authentication Flow**

```
1. User Login Request
   │
   ├─→ Username/Password or OAuth
   │
   ▼
2. Verify Credentials
   │
   ├─ ✅ Valid → Generate JWT Token
   │  │
   │  ├─ Token contains:
   │  │  • user_id
   │  │  • roles: ["customer", "verified"]
   │  │  • exp: 1 hour
   │  │  • Signed with RS256 private key
   │  │
   │  └─→ Return: { access_token, refresh_token }
   │
   └─ ❌ Invalid → Return 401 Unauthorized

3. Subsequent Requests
   │
   ├─→ Include: Authorization: Bearer <jwt_token>
   │
   ▼
4. API Gateway validates token
   │
   ├─ Verify signature with public key
   ├─ Check expiration
   ├─ Extract user info
   │
   └─→ Forward request with user context
```

### 🔒 **PCI DSS Compliance**

```yaml
Payment Data Handling:
  Card Data Storage: NEVER stored
  Tokenization: Payment gateway (Stripe/PayPal)
  PCI Scope: Reduced (SAQ-A)
  
  Security Requirements:
    - TLS 1.3 for all payment communication
    - No logging of card numbers
    - Regular security audits
    - Penetration testing (quarterly)
    - Employee training
```

### 🕵️ **Audit Logging**

```python
# Every critical action is logged
def create_audit_log(action, user_id, resource, details):
    log_entry = {
        "timestamp": datetime.utcnow(),
        "action": action,  # "reservation_created", "payment_processed"
        "user_id": user_id,
        "resource_type": resource,  # "seat", "order"
        "resource_id": details.get("resource_id"),
        "ip_address": request.remote_addr,
        "user_agent": request.headers.get("User-Agent"),
        "status": details.get("status"),  # "success", "failed"
        "metadata": details
    }
    
    # Store in append-only log
    audit_db.insert(log_entry)
    
    # Also send to SIEM (Security Information and Event Management)
    siem.send(log_entry)
```

### 🚨 **Intrusion Detection**

```yaml
Monitoring:
  - Failed login attempts (> 5 in 5 min) → Alert + IP block
  - Unusual API patterns → Machine learning anomaly detection
  - Privilege escalation attempts → Immediate alert
  - SQL injection attempts → Auto-block + notify security team
  
Tools:
  - Fail2Ban (IP blocking)
  - OSSEC (Host-based IDS)
  - Suricata (Network IDS)
  - Wazuh (Security monitoring)
```

---

## 📚 Technology Stack

### 🎨 **Frontend**

```yaml
Web Application:
  Framework: React 18 / Next.js 14
  State Management: Redux Toolkit / Zustand
  UI Library: Material-UI / Tailwind CSS
  Real-time: Socket.IO client
  Maps: SVG.js for seat maps
  
Mobile Apps:
  iOS: Swift / SwiftUI
  Android: Kotlin / Jetpack Compose
  Cross-platform: React Native / Flutter
  
PWA:
  Service Workers for offline support
  Push Notifications (Web Push API)
```

### ⚙️ **Backend**

```yaml
API Services:
  Language: Node.js (TypeScript) / Go / Python
  Framework: Express.js / Fastify / Gin / FastAPI
  API Standard: REST + GraphQL
  Real-time: WebSocket (Socket.IO / ws)
  
Microservices:
  - Catalog Service (Node.js)
  - Seat Map Service (Go - high performance)
  - Reservation Service (Go - concurrency)
  - Payment Service (Node.js - Stripe SDK)
  - Notification Service (Python - Celery)
  - Analytics Service (Python - data processing)
```

### 🗄️ **Databases**

```yaml
Primary Database:
  Type: PostgreSQL 15
  Configuration: Sharded (16 shards)
  Replication: Master-Slave (streaming)
  Backup: Daily full + hourly incremental
  
Cache:
  Type: Redis 7 Cluster
  Nodes: 8 (master-replica pairs)
  Persistence: RDB snapshots + AOF
  Use Cases: Sessions, rate limiting, pub/sub
  
Search Engine:
  Type: Elasticsearch 8
  Use: Event search, autocomplete
  
Time-Series:
  Type: InfluxDB / TimescaleDB
  Use: Metrics, analytics
  
Document Store:
  Type: MongoDB
  Use: Audit logs, user preferences
```

### 📨 **Message Queue**

```yaml
Event Streaming:
  Type: Apache Kafka
  Partitions: 32
  Replication Factor: 3
  Use Cases:
    - Reservation events
    - Payment events
    - Analytics data
    - Audit logs
    
Task Queue:
  Type: RabbitMQ / Redis Queue
  Use Cases:
    - Email sending
    - Ticket generation
    - Report generation
```

### ☁️ **Infrastructure**

```yaml
Cloud Provider: AWS / GCP / Azure

Compute:
  - Kubernetes (EKS / GKE / AKS)
  - EC2 / Compute Engine (worker nodes)
  - Lambda / Cloud Functions (serverless tasks)
  
Networking:
  - Load Balancer (ALB / Cloud Load Balancing)
  - CDN (CloudFront / Cloudflare)
  - VPC / Virtual Network
  
Storage:
  - S3 / Cloud Storage (tickets, assets)
  - EBS / Persistent Disks (databases)
  
Monitoring:
  - CloudWatch / Cloud Monitoring
  - Prometheus + Grafana
  - Datadog / New Relic
  - Sentry (error tracking)
```

### 🔧 **DevOps Tools**

```yaml
Container Orchestration:
  - Kubernetes 1.28+
  - Helm (package manager)
  - Kustomize (configuration)
  
CI/CD:
  - GitHub Actions / GitLab CI
  - ArgoCD (GitOps)
  - Terraform (IaC)
  
Security:
  - Trivy (container scanning)
  - SonarQube (code quality)
  - HashiCorp Vault (secrets)
  - cert-manager (SSL certificates)
```

---

## 🎓 Learning Resources

### 📖 **System Design**

#### **Books**
- 📘 *Designing Data-Intensive Applications* by Martin Kleppmann
- 📘 *System Design Interview* (Vol 1 & 2) by Alex Xu
- 📘 *Building Microservices* by Sam Newman
- 📘 *Database Internals* by Alex Petrov

#### **Online Courses**
- 🎓 [Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview)
- 🎓 [MIT 6.824: Distributed Systems](https://pdos.csail.mit.edu/6.824/)
- 🎓 [AWS Solutions Architect Professional](https://aws.amazon.com/certification/certified-solutions-architect-professional/)

#### **Case Studies**
- 📄 [Ticketmaster Architecture](https://www.infoq.com/presentations/ticketmaster-architecture/)
- 📄 [BookMyShow Tech Blog](https://blog.bookmyshow.com/)
- 📄 [Uber's Schemaless Datastore](https://eng.uber.com/schemaless-part-one/)

### 🔗 **Relevant Articles**

- [How We Built a Distributed Locking System](https://redis.io/docs/manual/patterns/distributed-locks/)
- [The Saga Pattern Explained](https://microservices.io/patterns/data/saga.html)
- [Optimistic vs Pessimistic Locking](https://martin.kleppmann.com/2016/02/08/how-to-do-distributed-locking.html)
- [CAP Theorem in Practice](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed/)

### 🛠️ **Hands-On Practice**

```yaml
Try Building:
  1. Simplified Ticket Booking API
     - Start with single-node setup
     - Implement basic CRUD
     - Add optimistic locking
     
  2. Add Caching Layer
     - Integrate Redis
     - Implement cache-aside pattern
     - Test performance improvements
     
  3. Implement TTL Expiration
     - Background worker
     - Seat release automation
     - Idempotency handling
     
  4. Payment Integration
     - Stripe test mode
     - Webhook handling
     - Refund logic
     
  5. Scale to Distributed
     - Add load balancer
     - Database sharding
     - Horizontal pod autoscaling
```


## 🤝 Contributing

We welcome contributions! Here's how you can help:

```bash
# 1. Fork the repository
# 2. Create a feature branch
git checkout -b feature/amazing-feature

# 3. Make your changes
git add .
git commit -m "Add amazing feature"

# 4. Push to your fork
git push origin feature/amazing-feature

# 5. Open a Pull Request
```

### 📋 **Contribution Guidelines**
- Follow the existing code style
- Write unit tests for new features
- Update documentation
- Keep commits atomic and well-described

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 💡 Acknowledgments

This system design is inspired by real-world ticketing platforms:
- 🎫 **Ticketmaster** - Global ticketing leader
- 🎬 **BookMyShow** - India's largest entertainment ticketing platform
- 🎵 **Eventbrite** - Event management and ticketing
- ✈️ **Airline Reservation Systems** - Classic distributed booking challenges

Special thanks to the open-source community for tools and libraries that make projects like this possible.

---

## 📞 Contact

**Ashmit Thakur**  
📧 Email: [Your Email]  
💼 LinkedIn: [Your LinkedIn]  
🐙 GitHub: [@AshmitThakur23](https://github.com/AshmitThakur23)

---

<div align="center">

### ⭐ Star this repository if you found it helpful!

**Built with ❤️ for learning distributed systems**

[![GitHub stars](https://img.shields.io/github/stars/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System?style=social)](https://github.com/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System)
[![GitHub forks](https://img.shields.io/github/forks/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System?style=social)](https://github.com/AshmitThakur23/Scalable-Event-Ticketing-and-Seat-Allocation-System)

</div>
