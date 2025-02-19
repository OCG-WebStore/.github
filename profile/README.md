
# OCG WebStore
A scalable, event-driven high-end fashion platform built with Java (Spring Boot) and Scala (Play Framework). Implements modern microservices patterns including CQRS, event sourcing, and real-time communication.

## Key Features:

#### Microservices Architecture: 6+ services with isolated responsibilities.
#### Event-Driven Workflows: Apache Kafka for order processing, price negotiations, and inventory updates.
#### Security: JWT/OAuth2 authentication, RBAC, and secrets management.
#### Observability: Grafana dashboards, Loki logging, and distributed tracing.
#### Infrastructure-as-Code: Terraform + Kubernetes deployment (AWS/GCP).

### Tech Stack:
<img src="https://img.shields.io/badge/Scala-DF3E36?logo=scala&logoColor=white" alt="Scala"> <img src="https://img.shields.io/badge/Java-ED8B00?logo=java&logoColor=white" alt="Java"> <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?logo=springboot&logoColor=white" alt="Spring Boot"> <img src="https://img.shields.io/badge/Play_Framework-000000?logo=playframework&logoColor=white" alt="Play">
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white" alt="PostgreSQL"> <img src="https://img.shields.io/badge/Kafka-231F20?logo=apachekafka&logoColor=white" alt="Kafka"> <img src="https://img.shields.io/badge/Redis-FF0000?logo=redis&logoColor=white" alt="Redis">

mermaidjs
## Architecture Diagram
![There should be a diagram here](https://github.com/OCG-WebStore/.github/blob/main/profile/Architecture.png?raw=true)

# Service Repositories:
## 1. Product Service
Manages product catalog, inventory, and image storage. Exposes GraphQL (read) and REST (admin CRUD) APIs.

### Tech Stack:

Language: Scala

Framework: Play Framework

Database: PostgreSQL (Slick ORM)

Integrations: Redis (cache), AWS S3 (pre-signed URLs), Kafka (product events)

### Key Features:

GraphQL schema with filters (price range, category)

Admin RBAC enforcement via JWT claims

Event sourcing for product lifecycle tracking

```bash
  git clone https://github.com/OCG-WebStore/product-service
```
## 2. User Service
Central authentication service with JWT/OAuth2 support. Manages user roles (admin/customer/designer).

### Tech Stack:

Language: Java

Framework: Spring Boot

Database: PostgreSQL (Spring Data JPA)

Integrations: Keycloak (OAuth2), Redis (token revocation)

### Key Features:

Social logins (Google/GitHub)

Refresh token rotation

Passwordless authentication workflows

```bash
  git clone https://github.com/yourusername/user-service
```
## 3. Order Service
Handles order lifecycle, price negotiations, event sourcing and a unique customer-oriented order panel.

### Tech Stack:

Language: Scala

Framework: Play Framework

Database: PostgreSQL (Slick)

Integrations: Kafka Streams, Payment Service, Product Service

### Key Features:

State machines for order status transitions

Circuit breakers for payment service resilience

Materialized views for fast GraphQL queries

```bash
    git clone https://github.com/yourusername/order-service
```
## 4. Chat Service
Real-time order negotiation system with WebSocket support.

### Tech Stack:

Language: Scala

Framework: Play Framework (Akka Actors)

Database: MongoDB (ReactiveMongo)

Integrations: Kafka (price change events)

### Key Features:

WebSocket sessions with JWT authentication

Auto-deletion of chats 48 hours after order completion

System messages for price change approvals

```bash
    git clone https://github.com/yourusername/chat-service
```
## 5. Payment Service
Idempotent payment processing with support for Stripe/PayPal.

### Tech Stack:

Language: Java

Framework: Spring Boot

Database: PostgreSQL

Integrations: Stripe API, Order Service

### Key Features:

Idempotency keys for duplicate request prevention

Audit logs for compliance

Refund workflows with SLA tracking

```bash
    git clone https://github.com/yourusername/payment-service
```
## 6. API Gateway
Unified entry point with JWT validation and GraphQL federation.

### Tech Stack:

Language: Java

Framework: Spring Cloud Gateway

Integrations: GraphQL Apollo Federation

### Key Features:

Rate limiting (Redis)

Request/response logging

Circuit breaker patterns

```bash
    git clone https://github.com/yourusername/api-gateway
```
## 7. Admin Service
Backend for admin dashboard.

### Tech Stack:

Language: Scala

Framework: Play Framework

Integrations: Grafana, Loki

### Key Features:

Bulk product imports/exports (CSV/Excel)

User role management

System health monitoring

```bash
  git clone https://github.com/yourusername/admin-service
```