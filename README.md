# GateShield

### Secure API Gateway & Observability Platform

GateShield is a full-stack platform that provides a secure gateway layer between clients and backend services. It centralizes API access control, traffic management, request tracking, and service-performance monitoring in one place.

Instead of allowing clients to communicate directly with individual backend services, GateShield acts as a controlled entry point where requests can be authenticated, rate-limited, logged, forwarded, and analyzed.

---

## ✨ Why GateShield?

Modern applications often have multiple backend services that need to be protected and monitored.

GateShield provides a centralized layer for:

**Authenticate → Control → Route → Record → Analyze**

This makes it easier to manage API traffic while gaining visibility into service health and performance.

---

## 🚀 Core Capabilities

### 🔐 Access & Security

* JWT-based authentication
* Role-based access control
* API-key creation and management
* Protected administrative routes
* Secure handling of API credentials
* Environment-based configuration for sensitive values

### 🌐 API Gateway

* Centralized API entry point
* Reverse proxy support
* Request forwarding to target services
* Service-based gateway configuration
* Controlled communication between clients and backend services

### 🚦 Traffic Management

* Redis-powered rate limiting
* Per-API-key traffic control
* Rate-limit violation tracking
* Protection against excessive API requests

### 📝 Request Observability

* Request and response logging
* HTTP status-code tracking
* Endpoint-level monitoring
* Service-level traffic information
* Recent request inspection

### 📊 Analytics & Monitoring

GateShield provides an analytics layer for understanding API usage and performance.

It tracks metrics such as:

* Total requests
* Successful requests
* Failed requests
* Error percentage
* HTTP status-code distribution
* Service traffic
* API-key usage
* Request latency
* Recent gateway activity
* Rate-limit activity

### ⚡ Performance Metrics

Response-time analysis includes:

* Minimum latency
* Average latency
* P50 latency
* P95 latency
* P99 latency
* Maximum latency

These metrics help identify slow endpoints and performance bottlenecks.

---

## 🏗️ System Architecture

```text
                    ┌──────────────────┐
                    │      Client      │
                    └────────┬─────────┘
                             │
                             ▼
                 ┌───────────────────────┐
                 │     GateShield        │
                 │     API Gateway       │
                 ├───────────────────────┤
                 │ Authentication        │
                 │ API-Key Validation    │
                 │ Rate Limiting         │
                 │ Request Logging       │
                 │ Request Routing       │
                 └───────────┬───────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │   Target API    │
                    │    Service      │
                    └────────┬────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │ PostgreSQL + Redis   │
                  └──────────┬───────────┘
                             │
                             ▼
                  ┌──────────────────────┐
                  │ Dashboard & Analytics│
                  └──────────────────────┘
```

---

## 🔄 Request Flow

A typical request passes through the gateway as follows:

```text
Client
  │
  ▼
Authentication
  │
  ▼
API-Key Validation
  │
  ▼
Rate Limiting
  │
  ▼
Request Logging
  │
  ▼
Gateway Routing
  │
  ▼
Target Service
  │
  ▼
Response
  │
  ▼
Metrics & Logs
  │
  ▼
Dashboard
```

This centralized flow allows GateShield to enforce security and traffic policies before requests reach backend services.

---

## 📈 Analytics

The dashboard provides visibility into API activity and service performance.

### Traffic Analytics

```text
Requests
├── Total Requests
├── Successful Requests
├── Failed Requests
├── Error Rate
└── Status-Code Distribution
```

### Service Analytics

```text
Services
├── Request Volume
├── Endpoint Activity
├── Response Performance
└── Error Information
```

### API-Key Analytics

```text
API Keys
├── Request Usage
├── Traffic Distribution
└── Rate-Limit Activity
```

### Latency Analytics

```text
Response Time
├── Minimum
├── Average
├── P50
├── P95
├── P99
└── Maximum
```

---

## 🔌 Analytics Endpoints

The backend exposes dedicated endpoints for dashboard analytics.

| Endpoint                            | Purpose                   |
| ----------------------------------- | ------------------------- |
| `/api/v1/analytics/summary`         | Overall API activity      |
| `/api/v1/analytics/status-codes`    | HTTP status distribution  |
| `/api/v1/analytics/services`        | Service-level statistics  |
| `/api/v1/analytics/top-api-keys`    | API-key usage             |
| `/api/v1/analytics/response-times`  | Latency statistics        |
| `/api/v1/analytics/daily`           | Daily traffic information |
| `/api/v1/analytics/error-rate`      | Error-rate statistics     |
| `/api/v1/analytics/monitoring`      | Gateway monitoring        |
| `/api/v1/analytics/rate-limits`     | Rate-limit activity       |
| `/api/v1/analytics/recent-requests` | Recent gateway requests   |

---

## 🛠️ Technology Stack

| Layer            | Technology             |
| ---------------- | ---------------------- |
| Frontend         | React, Vite            |
| UI               | Tailwind CSS           |
| Data Fetching    | TanStack Query         |
| Backend          | Node.js, Express.js    |
| Database         | PostgreSQL             |
| ORM              | Prisma                 |
| Cache            | Redis                  |
| Authentication   | JWT                    |
| Gateway          | Express-based Gateway  |
| Reverse Proxy    | Nginx                  |
| Containerization | Docker, Docker Compose |

---

## 📁 Project Structure

```text
GateShield/
│
├── Backend/
│   ├── middleware/
│   │   ├── apiKey.middleware.js
│   │   ├── auth.middleware.js
│   │   ├── authorize.middleware.js
│   │   ├── rateLimiter.middleware.js
│   │   └── requestLogger.middleware.js
│   │
│   └── modules/
│       ├── analytics/
│       ├── apikey/
│       ├── auth/
│       ├── gateway/
│       └── workspace/
│
├── Frontend/
│   └── src/
│       ├── api/
│       └── features/
│           ├── dashboard/
│           └── analytics/
│
├── docker-compose.yml
├── Dockerfiles
├── nginx/
└── README.md
```

---

## ⚙️ Getting Started

### Prerequisites

Make sure the following are installed:

* Node.js
* npm
* PostgreSQL
* Redis
* Docker
* Docker Compose

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd GateShield
```

### 2. Configure the Backend

```bash
cd Backend
npm install
```

Create the required environment configuration.

Example:

```env
DATABASE_URL=
REDIS_URL=
JWT_SECRET=
PORT=5000
CORS_ORIGIN=
```

Do not commit real credentials or secrets to the repository.

### 3. Start the Backend

```bash
npm run dev
```

### 4. Start the Frontend

Open another terminal:

```bash
cd Frontend
npm install
npm run dev
```

The Vite development server will provide the frontend URL in the terminal.

---

## 🐳 Running with Docker

GateShield can also be started using Docker Compose.

```bash
docker compose up --build
```

The containerized setup can include:

```text
┌─────────────────┐
│     Nginx       │
└────────┬────────┘
         │
 ┌───────┴────────┐
 │                │
 ▼                ▼
Frontend        Backend
                  │
          ┌───────┴───────┐
          ▼               ▼
      PostgreSQL         Redis
```

This provides a consistent environment for running the application and its supporting services.

---

## 🔒 Security Design

GateShield uses multiple layers of protection:

* JWT-protected application routes
* Role-based authorization
* API-key authentication
* Redis-based rate limiting
* Environment-based secrets
* Controlled API responses
* ORM-based database access
* Safe API-key representation
* Separation of authentication and gateway responsibilities

The gateway provides a centralized point where access and traffic policies can be enforced.

---

## 🧪 Testing Checklist

Important scenarios to validate include:

### Authentication

* Valid login
* Invalid credentials
* Unauthorized requests
* Role-based access restrictions

### API Keys

* Valid API key
* Invalid API key
* Missing API key
* API-key usage tracking

### Gateway

* Successful proxy request
* Invalid target service
* Failed target request
* Response forwarding

### Rate Limiting

* Requests within limit
* Rate-limit threshold reached
* `429 Too Many Requests`
* Rate-limit analytics

### Monitoring

* Request logging
* Status-code tracking
* Error-rate calculation
* Latency calculation
* P95/P99 calculation
* Dashboard data consistency

---

## 🔮 Future Enhancements

Potential improvements include:

* Custom analytics date ranges
* Exportable analytics reports
* Configurable API performance alerts
* Latency threshold notifications
* Error-rate alerts
* Endpoint latency history
* Advanced API-key quotas
* Automated end-to-end testing
* Production deployment workflows
* Distributed gateway support

---

## 🎯 Project Objective

GateShield is designed around four major goals:

```text
          ┌─────────────┐
          │   Secure    │
          │    APIs     │
          └──────┬──────┘
                 │
                 ▼
          ┌─────────────┐
          │   Control   │
          │   Traffic   │
          └──────┬──────┘
                 │
                 ▼
          ┌─────────────┐
          │   Monitor   │
          │   Services  │
          └──────┬──────┘
                 │
                 ▼
          ┌─────────────┐
          │   Analyze   │
          │ Performance │
          └─────────────┘
```

**GateShield — Secure the gateway. Control the traffic. Observe the system.**
