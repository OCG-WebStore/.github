
# OCG WebStore
A scalable, event-driven high-end fashion platform built with Java (Spring Boot) and Scala (Play Framework). Implements modern microservices patterns including CQRS, event sourcing, and real-time communication.

## Important notice:
### At this time this serves just as a project plan for OCG WebStore and most of the content referenced here is not yet implemented. <br>
### Key changes might be made during the process of implementation. Some of the service repositories are not yet available on GitHub. <br>
### Currently under development: <br>
#### Product Inventory: https://github.com/OCG-WebStore/product-inventory

## Key Features:

#### Microservices Architecture: 8 services with isolated responsibilities. <br> Event-Driven Workflows: Apache Kafka for order processing, price negotiations, and inventory updates.<br>Security: JWT/OAuth2 authentication, RBAC, and secrets management.<br>Infrastructure-as-Code: Terraform + Kubernetes deployment (AWS/GCP).<br>Observability: Grafana dashboards, Loki logging, and distributed tracing.


### Tech Stack:
<img src="https://img.shields.io/badge/Scala-DF3E36?logo=scala&logoColor=white" alt="Scala"> <img src="https://img.shields.io/badge/Play_Framework-000000?logo=playframework&logoColor=white" alt="Play"> <br>
<img src="https://img.shields.io/badge/Java-ED8B00?logo=openjdk&logoColor=white" alt="Java"> <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?logo=springboot&logoColor=white" alt="Spring Boot"> <br>
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white" alt="PostgreSQL"> <img src="https://img.shields.io/badge/Redis-FF0000?logo=redis&logoColor=white" alt="Redis"> 
<img src="https://img.shields.io/badge/MongoDB-13aa52?logo=mongodb&logoColor=white" alt="MongoDB"> <br>
<img src="https://img.shields.io/badge/Kafka-231F20?logo=apachekafka&logoColor=white" alt="Kafka">


## Architecture Diagram
![There should be a diagram here](https://github.com/OCG-WebStore/.github/blob/main/profile/Architecture.png?raw=true)

# Service Repositories:
## 1. Product Inventory
Manages product catalog, inventory, and image storage. Exposes GraphQL (read) and REST (admin CRUD) APIs.

### Tech Stack:

- Language: Scala
- Framework: Play Framework
- Database: PostgreSQL (Slick ORM)
- Integrations: Redis (cache), AWS S3 (pre-signed URLs), Kafka (product events)

### Key Features:

- GraphQL schema with filters (price range, category)
- Admin RBAC enforcement via JWT claims
- Event sourcing for product lifecycle tracking

```bash
  git clone https://github.com/OCG-WebStore/product-inventory
```
## 2. User Managment
Central authentication service with JWT/OAuth2 support. Manages user roles (admin/customer/designer).

### Tech Stack:

- Language: Java
- Framework: Spring Boot
- Database: PostgreSQL (Spring Data JPA)
- Integrations: Keycloak (OAuth2), Redis (token revocation)

### Key Features:

- Social logins (Google/GitHub)
- Refresh token rotation
- Passwordless authentication workflows

```bash
  git clone https://github.com/yourusername/user-management
```
## 3. Order Service
Handles order lifecycle, price negotiations, event sourcing and a unique customer-oriented order panel.

### Tech Stack:

- Language: Scala
- Framework: Play Framework
- Database: PostgreSQL (Slick)
- Integrations: Kafka Streams, Payment Service, Product Inventory

### Key Features:

- State machines for order status transitions
- Circuit breakers for payment service resilience
- Materialized views for fast GraphQL queries

```bash
    git clone https://github.com/yourusername/order-service
```
## 4. Chat Service
Real-time order negotiation system with WebSocket support.

### Tech Stack:

- Language: Scala
- Framework: Play Framework (Akka Actors)
- Database: MongoDB (ReactiveMongo)
- Integrations: Kafka (price change events)

### Key Features:

- WebSocket sessions with JWT authentication
- Auto-deletion of chats 48 hours after order completion
- System messages for price change approvals

```bash
    git clone https://github.com/yourusername/chat-service
```
## 5. Payment Service
Idempotent payment processing with support for Stripe/PayPal.

### Tech Stack:

- Language: Java
- Framework: Spring Boot
- Database: PostgreSQL
- Integrations: Stripe API, Order Service

### Key Features:

- Idempotency keys for duplicate request prevention
- Audit logs for compliance
- Refund workflows with SLA tracking

```bash
    git clone https://github.com/yourusername/payment-service
```
## 6. OCGate
OCG WebStore API Gateway. Unified entry point with JWT validation and GraphQL federation.

### Tech Stack:

- Language: Java
- Framework: Spring Cloud Gateway
- Integrations: GraphQL Apollo Federation

### Key Features:

- Rate limiting (Redis)
- Request/response logging
- Circuit breaker patterns

```bash
    git clone https://github.com/yourusername/ocgate
```
## 7. Admin Service
Backend for admin dashboard.

### Tech Stack:

- Language: Scala
- Framework: Play Framework
- Integrations: Grafana, Loki

### Key Features:

- Bulk product imports/exports (CSV/Excel)
- User role management
- System health monitoring

```bash
  git clone https://github.com/yourusername/admin-service
```
## 8. Notification Service
Handles real-time user notifications across critical e-commerce workflows. Subscribes to Kafka events to trigger alerts for inventory changes, order milestones, and pending actions.

### Tech Stack:

- Language: Scala
- Framework: Play Framework (Akka Streams for Kafka integration)
- Database: PostgreSQL (Slick ORM for notification history)
- Integrations: Kafka, Firebase Cloud Messaging (mobile), WebSocket

### Key Features:

- Event-driven notifications for:
  - Inventory stock updates (low stock/restock alerts)<br>
  - Order creation/completion status 
  - Customization approval reminders (24h timeout)
- Multi-channel delivery (email, WebSocket, mobile push)
- Notification templating with user personalization
- Deduplication to prevent event replay duplicates

```bash
    git clone https://github.com/yourusername/notification-service
```