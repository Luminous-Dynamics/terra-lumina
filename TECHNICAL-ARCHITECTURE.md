# Terra Lumina Technical Architecture
## Platform Architecture & Implementation Plan

> **Status**: Architecture designed, development starting upon Pre-Seed funding
> **Last Updated**: January 2025

---

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [System Architecture Overview](#system-architecture-overview)
3. [Technology Stack](#technology-stack)
4. [Core Components](#core-components)
5. [Data Architecture](#data-architecture)
6. [Security & Compliance](#security--compliance)
7. [Scalability & Performance](#scalability--performance)
8. [Development Roadmap](#development-roadmap)
9. [Infrastructure & DevOps](#infrastructure--devops)
10. [Integration Architecture](#integration-architecture)

---

## Executive Summary

### Architecture Principles

**1. Security-First**
- End-to-end encryption for sensitive data
- SOC 2 Type II compliance target
- Multi-layered security architecture
- Regular third-party audits

**2. Scalability by Design**
- Microservices architecture
- Horizontal scaling capability
- Cloud-native infrastructure
- Auto-scaling based on demand

**3. Regulatory Compliance**
- Built for SEC/FINRA compliance
- GDPR and CCPA compliant from day one
- Audit trail for all transactions
- Configurable compliance rules engine

**4. User-Centric Design**
- Mobile-first responsive design
- Accessibility (WCAG 2.1 AA)
- Sub-3-second page loads
- Offline-capable PWA

**5. API-First Architecture**
- RESTful APIs for all functionality
- GraphQL for complex queries
- Webhook support for integrations
- Comprehensive API documentation

---

## System Architecture Overview

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Client Layer                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Web App    │  │  Mobile App  │  │  Admin Panel │      │
│  │  (React PWA) │  │ (React Native)│  │   (React)    │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                            ↓ HTTPS/WSS
┌─────────────────────────────────────────────────────────────┐
│                   API Gateway Layer                          │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Kong API Gateway / AWS API Gateway                  │   │
│  │  - Rate limiting  - Authentication  - Load balancing │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                 Microservices Layer                          │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│  │   User      │ │  Project    │ │ Investment  │           │
│  │  Service    │ │  Service    │ │  Service    │           │
│  └─────────────┘ └─────────────┘ └─────────────┘           │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│  │  Payment    │ │   Legal     │ │  Analytics  │           │
│  │  Service    │ │  Service    │ │  Service    │           │
│  └─────────────┘ └─────────────┘ └─────────────┘           │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│  │Notification │ │   AI/ML     │ │   Audit     │           │
│  │  Service    │ │  Service    │ │  Service    │           │
│  └─────────────┘ └─────────────┘ └─────────────┘           │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                    Data Layer                                │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐        │
│  │  PostgreSQL  │ │    Redis     │ │  Elasticsearch│        │
│  │  (Primary DB)│ │   (Cache)    │ │   (Search)   │        │
│  └──────────────┘ └──────────────┘ └──────────────┘        │
│  ┌──────────────┐ ┌──────────────┐                         │
│  │     S3       │ │   MongoDB    │                         │
│  │ (Documents)  │ │ (Logs/Events)│                         │
│  └──────────────┘ └──────────────┘                         │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│              External Integration Layer                      │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│  │   Stripe    │ │   Plaid     │ │  DocuSign   │           │
│  │  (Payment)  │ │   (Bank)    │ │   (Legal)   │           │
│  └─────────────┘ └─────────────┘ └─────────────┘           │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐           │
│  │   SendGrid  │ │   Twilio    │ │  Auth0      │           │
│  │   (Email)   │ │   (SMS)     │ │   (Auth)    │           │
│  └─────────────┘ └─────────────┘ └─────────────┘           │
└─────────────────────────────────────────────────────────────┘
```

### Architecture Patterns

**Microservices**: Independent, scalable services
**Event-Driven**: Asynchronous communication via message queue
**CQRS**: Separate read/write models for performance
**API Gateway**: Single entry point, security, rate limiting
**Service Mesh**: Inter-service communication and monitoring

---

## Technology Stack

### Frontend

**Web Application**
- **Framework**: React 18+ with TypeScript
- **State Management**: Redux Toolkit + RTK Query
- **UI Components**: Material-UI (MUI) v5
- **Charts/Viz**: D3.js, Recharts
- **Forms**: React Hook Form + Yup validation
- **PWA**: Workbox for offline support
- **Testing**: Jest, React Testing Library, Playwright

**Mobile Application** (Phase 2)
- **Framework**: React Native with TypeScript
- **Navigation**: React Navigation v6
- **State**: Redux (shared with web)
- **Testing**: Jest, Detox

**Admin Dashboard**
- **Framework**: React with TypeScript
- **UI**: Custom admin template (Material-UI)
- **Real-time**: WebSocket connection for live updates

### Backend

**Core Services**
- **Runtime**: Node.js 20 LTS
- **Framework**: NestJS (TypeScript)
- **API Style**: RESTful + GraphQL
- **Validation**: class-validator, class-transformer
- **Documentation**: OpenAPI/Swagger

**Alternative Stack** (Under Evaluation)
- **Runtime**: Python 3.11+
- **Framework**: FastAPI
- **Async**: AsyncIO
- **Use Case**: AI/ML services, data processing

### Databases

**Primary Database**
- **Type**: PostgreSQL 15+
- **Use**: User data, transactions, projects
- **ORM**: Prisma (Node.js) or SQLAlchemy (Python)
- **Replication**: Primary-replica setup
- **Backup**: Daily automated backups with point-in-time recovery

**Cache Layer**
- **Type**: Redis 7+
- **Use**: Session management, API caching, rate limiting
- **Clustering**: Redis Cluster for high availability

**Search Engine**
- **Type**: Elasticsearch 8+
- **Use**: Project search, full-text search, analytics
- **Features**: Fuzzy matching, geolocation search, faceted search

**Document Store**
- **Type**: MongoDB 6+ (optional)
- **Use**: Event logs, activity streams, audit trails
- **Alternative**: PostgreSQL JSONB columns

**File Storage**
- **Type**: AWS S3 / Cloudflare R2
- **Use**: Documents, images, reports
- **CDN**: CloudFront / Cloudflare CDN

### Infrastructure

**Cloud Provider**: AWS (primary) with multi-cloud capability
- **Compute**: ECS Fargate (containerized services)
- **Serverless**: Lambda for event processing
- **Networking**: VPC, ALB, Route 53
- **Security**: AWS WAF, Shield, Secrets Manager

**Container Orchestration**
- **Development**: Docker Compose
- **Production**: AWS ECS / Kubernetes (future)
- **Registry**: AWS ECR / Docker Hub

**CI/CD**
- **Version Control**: GitHub
- **CI/CD**: GitHub Actions
- **Deployment**: Blue-green deployments
- **Monitoring**: Rollback on error detection

### Third-Party Services

**Authentication & Identity**
- **Provider**: Auth0 / AWS Cognito
- **Features**: SSO, MFA, social login
- **Compliance**: SOC 2, ISO 27001

**Payment Processing**
- **Provider**: Stripe Connect
- **Features**: ACH, wire, card processing
- **Compliance**: PCI DSS Level 1

**Banking Integration**
- **Provider**: Plaid
- **Use**: Bank account verification, balance checks
- **Alternative**: Yodlee, Finicity

**E-Signature**
- **Provider**: DocuSign
- **Use**: Investment agreements, legal documents
- **Alternative**: HelloSign, Adobe Sign

**Communication**
- **Email**: SendGrid / AWS SES
- **SMS**: Twilio
- **Push Notifications**: Firebase Cloud Messaging
- **In-App Chat**: Stream Chat / Sendbird

**Analytics & Monitoring**
- **Application**: New Relic / Datadog
- **User Analytics**: Mixpanel / Amplitude
- **Error Tracking**: Sentry
- **Logging**: CloudWatch / ELK Stack

---

## Core Components

### 1. User Service

**Responsibilities**
- User registration and authentication
- Profile management (investor, developer, admin)
- KYC/AML verification workflow
- Accreditation verification (for Reg D)
- User preferences and settings

**Key Features**
- Multi-factor authentication (MFA)
- Social login (Google, LinkedIn)
- Email verification
- Password reset flow
- Role-based access control (RBAC)

**API Endpoints**
- `POST /users/register`
- `POST /users/login`
- `GET /users/profile`
- `PUT /users/profile`
- `POST /users/verify-identity`

**Database Schema**
```sql
users (
  id UUID PRIMARY KEY,
  email VARCHAR UNIQUE NOT NULL,
  password_hash VARCHAR,
  role ENUM('investor', 'developer', 'admin'),
  kyc_status ENUM('pending', 'verified', 'rejected'),
  accredited BOOLEAN DEFAULT false,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

---

### 2. Project Service

**Responsibilities**
- Project creation and management
- Project listing and discovery
- Due diligence document management
- Project status tracking
- Geographic and category search

**Key Features**
- Rich project profiles (description, financials, timeline)
- Document vault (prospectus, contracts, permits)
- Image and video upload
- Project milestones tracking
- Developer dashboard

**API Endpoints**
- `POST /projects`
- `GET /projects` (with filters)
- `GET /projects/:id`
- `PUT /projects/:id`
- `POST /projects/:id/documents`
- `GET /projects/search?q=solar&location=california`

**Database Schema**
```sql
projects (
  id UUID PRIMARY KEY,
  developer_id UUID REFERENCES users(id),
  name VARCHAR NOT NULL,
  description TEXT,
  category ENUM('hydroelectric', 'solar', 'wind', 'geothermal'),
  target_raise DECIMAL,
  minimum_investment DECIMAL,
  expected_irr DECIMAL,
  location GEOGRAPHY,
  status ENUM('draft', 'active', 'funded', 'closed'),
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

---

### 3. Investment Service

**Responsibilities**
- Investment transaction processing
- Portfolio management
- Investment limits and compliance checks
- Investment history and reporting
- Distribution calculations

**Key Features**
- Secure payment processing
- Investment confirmation workflow
- Compliance checks (accreditation, limits)
- Fractional investments
- Investment cancellation (during review period)

**API Endpoints**
- `POST /investments`
- `GET /investments` (user's portfolio)
- `GET /investments/:id`
- `POST /investments/:id/cancel`
- `GET /investments/distributions`

**Database Schema**
```sql
investments (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  project_id UUID REFERENCES projects(id),
  amount DECIMAL NOT NULL,
  status ENUM('pending', 'confirmed', 'funded', 'cancelled'),
  payment_method VARCHAR,
  payment_status ENUM('pending', 'completed', 'failed'),
  signed_agreement_url VARCHAR,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

---

### 4. Payment Service

**Responsibilities**
- Payment method management
- Transaction processing (ACH, wire, card)
- Escrow account management
- Disbursement to project developers
- Distribution to investors

**Key Features**
- Stripe Connect integration
- Bank account verification (Plaid)
- PCI compliance
- Failed payment retry logic
- Payment reconciliation

**API Endpoints**
- `POST /payments/methods`
- `GET /payments/methods`
- `POST /payments/charge`
- `GET /payments/history`
- `POST /payments/refund`

**Security**
- Tokenization of payment methods
- Encryption at rest and in transit
- PCI DSS compliance
- Fraud detection (Stripe Radar)

---

### 5. Legal Service

**Responsibilities**
- Investment agreement generation
- Document signing workflow (DocuSign)
- Compliance rule engine
- Regulatory reporting
- Investor suitability checks

**Key Features**
- Template-based document generation
- E-signature integration
- Compliance questionnaires
- Reg CF/Reg D/Reg A+ support
- Audit trail for all legal actions

**API Endpoints**
- `POST /legal/agreements`
- `GET /legal/agreements/:id`
- `POST /legal/sign/:id`
- `GET /legal/compliance-check`

**Compliance Rules Engine**
```javascript
// Example rule
{
  rule: "reg_cf_limit",
  check: investor.annual_income < 107000
    ? investment <= min(2200, 0.05 * investor.annual_income)
    : investment <= 0.10 * investor.annual_income,
  message: "Investment exceeds Regulation Crowdfunding limits"
}
```

---

### 6. Analytics Service

**Responsibilities**
- User behavior tracking
- Investment analytics
- Project performance metrics
- Platform health monitoring
- Business intelligence dashboards

**Key Features**
- Real-time analytics
- Custom reports
- Investor/developer dashboards
- Cohort analysis
- Funnel tracking

**Metrics Tracked**
- Platform volume (daily, monthly, cumulative)
- Conversion rates (visitor → investor)
- Average investment size
- Project success rate
- User retention/churn

---

### 7. AI/ML Service

**Responsibilities**
- Project discovery and scoring
- Risk assessment
- Fraud detection
- Personalized recommendations
- Predictive analytics

**Key Features**
- Project scoring algorithm
- Investor-project matching
- Anomaly detection
- Natural language processing (project analysis)
- Market trend prediction

**ML Models**
- **Project Quality Score**: Random Forest classifier
- **Investment Risk**: Gradient boosting model
- **Fraud Detection**: Isolation Forest (anomaly detection)
- **Recommendation**: Collaborative filtering

**Technology Stack**
- **Framework**: TensorFlow / PyTorch
- **Training**: AWS SageMaker / Google Vertex AI
- **Inference**: Real-time API / Batch processing
- **MLOps**: MLflow for model versioning

---

### 8. Notification Service

**Responsibilities**
- Multi-channel notifications (email, SMS, push, in-app)
- Notification preferences management
- Template management
- Delivery tracking and retries

**Key Features**
- Event-driven notifications
- Customizable templates
- Delivery scheduling
- Unsubscribe management
- A/B testing for messaging

**Notification Types**
- Investment confirmations
- Project updates
- Payment notifications
- Regulatory reminders
- Marketing communications

---

### 9. Audit Service

**Responsibilities**
- Complete audit trail for all actions
- Compliance reporting
- Suspicious activity monitoring
- Data retention policies

**Key Features**
- Immutable audit logs
- Regulatory reporting exports
- Real-time alerting
- Log retention (7 years for financial records)

**Audit Events**
- User actions (login, profile changes)
- Financial transactions
- Document access
- Admin actions
- System events

---

## Data Architecture

### Data Flow

**Investment Flow Example**
```
1. User initiates investment (Web/Mobile)
   ↓
2. API Gateway validates request
   ↓
3. Investment Service checks compliance
   ↓
4. Legal Service generates agreement
   ↓
5. User signs agreement (DocuSign)
   ↓
6. Payment Service processes payment
   ↓
7. Investment confirmed, project funded
   ↓
8. Notification Service sends confirmation
   ↓
9. Analytics Service tracks metrics
   ↓
10. Audit Service logs all actions
```

### Event-Driven Architecture

**Message Queue**: RabbitMQ / AWS SQS
**Event Bus**: Event Bridge / Custom

**Event Examples**
```javascript
{
  eventType: "investment.created",
  timestamp: "2025-01-14T10:30:00Z",
  userId: "uuid",
  projectId: "uuid",
  amount: 50000,
  metadata: { ... }
}
```

**Subscribers**
- Analytics Service: Track metrics
- Notification Service: Send confirmation email
- Legal Service: Generate documents
- Audit Service: Log event

---

### Data Models

**Entity Relationship Overview**

```
users (1) ─────< (M) investments (M) >───── (1) projects
  │                      │
  │                      │
  └────< (M) kyc_verifications
                         │
                         └────< (M) documents
```

### Caching Strategy

**Redis Cache Layers**

1. **API Response Cache**
   - TTL: 5 minutes for project listings
   - TTL: 1 hour for static content
   - Cache invalidation on data updates

2. **Session Cache**
   - User sessions stored in Redis
   - TTL: 7 days (sliding expiration)

3. **Rate Limiting**
   - Token bucket algorithm
   - Limits: 100 req/min per user, 1000 req/min per IP

---

## Security & Compliance

### Security Layers

**1. Network Security**
- VPC with private subnets for databases
- Security groups and NACLs
- DDoS protection (AWS Shield)
- WAF rules for common attacks

**2. Application Security**
- Input validation on all endpoints
- SQL injection prevention (parameterized queries)
- XSS protection (content security policy)
- CSRF tokens for state-changing requests
- Rate limiting and throttling

**3. Data Security**
- Encryption at rest (AES-256)
- Encryption in transit (TLS 1.3)
- Database encryption (AWS RDS encryption)
- Field-level encryption for PII
- Secrets management (AWS Secrets Manager)

**4. Authentication & Authorization**
- JWT tokens with refresh rotation
- Multi-factor authentication (TOTP, SMS)
- Role-based access control (RBAC)
- OAuth 2.0 / OpenID Connect
- Session timeout (30 minutes inactivity)

### Compliance Framework

**SOC 2 Type II** (Target: Year 2)
- Security, availability, confidentiality
- Third-party audit
- Continuous monitoring

**GDPR Compliance**
- Right to access, rectify, erase data
- Data portability
- Consent management
- Privacy by design

**CCPA Compliance**
- Consumer data rights
- Do not sell opt-out
- Privacy policy disclosure

**Securities Regulations**
- SEC Reg CF compliance
- Reg D (506b, 506c) support
- Reg A+ readiness
- Investor limits enforcement
- Accreditation verification

**PCI DSS** (via Stripe)
- No card data stored directly
- PCI Level 1 service provider (Stripe)
- Tokenization for all payments

### Security Testing

**Automated**
- Daily dependency scanning (Snyk, Dependabot)
- Static code analysis (SonarQube)
- Secret scanning (GitHub Advanced Security)

**Manual**
- Quarterly penetration testing
- Annual security audit
- Bug bounty program (Year 2)

---

## Scalability & Performance

### Scaling Strategy

**Horizontal Scaling**
- Stateless services (scale via container replication)
- Load balancing (ALB)
- Auto-scaling based on CPU/memory/request count

**Database Scaling**
- Read replicas for PostgreSQL
- Connection pooling (PgBouncer)
- Database sharding (future, >10M users)

**Caching**
- Multi-level caching (browser, CDN, Redis, database)
- Cache warming for popular content

### Performance Targets

| Metric | Target | Measurement |
|--------|--------|-------------|
| API Response Time (p95) | <200ms | New Relic |
| Page Load Time (p95) | <3s | Lighthouse |
| Database Query Time (p95) | <50ms | Slow query log |
| Uptime | 99.9% | StatusPage |
| Concurrent Users | 10,000+ | Load testing |

### Load Testing

**Tools**: k6, Artillery, Gatling
**Scenarios**:
- 1,000 concurrent users browsing projects
- 100 simultaneous investments
- 10,000 API requests per second
- Database connection pool saturation

**Targets**:
- Handle 10x current traffic
- Graceful degradation under load
- No data loss under failure

---

## Development Roadmap

### Phase 1: MVP (Months 1-3)

**Core Features**
- User registration and authentication
- Basic project listing
- Simple investment flow
- Stripe payment integration
- Basic compliance checks

**Tech Stack**
- React frontend
- NestJS backend
- PostgreSQL database
- Redis cache
- Deployed on AWS ECS

**Milestones**
- Week 4: Auth + user management
- Week 8: Project service + listings
- Week 12: Investment flow + payments

---

### Phase 2: Enhanced Platform (Months 4-6)

**New Features**
- Advanced search and filtering
- User dashboards (investor, developer)
- Document management and e-signatures
- Email notifications
- Admin panel

**Enhancements**
- Mobile-responsive PWA
- Performance optimization
- Security hardening
- Monitoring and alerting

**Milestones**
- Month 4: Search + dashboards
- Month 5: Legal workflow
- Month 6: Admin tools + beta launch

---

### Phase 3: Scale & Optimize (Months 7-12)

**New Features**
- Mobile app (React Native)
- Advanced analytics
- AI-powered recommendations
- Secondary market (if regulatory approval)
- International expansion support

**Enhancements**
- Microservices decomposition
- Performance optimization
- Security audit and SOC 2 prep
- Scalability improvements

**Milestones**
- Month 9: Mobile app launch
- Month 12: Series A readiness

---

## Infrastructure & DevOps

### Environments

**Development**
- Local Docker Compose
- Shared dev database
- Mock external services

**Staging**
- Mirror of production
- Subset of production data
- Full integration testing

**Production**
- Multi-AZ deployment
- Auto-scaling enabled
- Production data
- 24/7 monitoring

### CI/CD Pipeline

```
GitHub Push
   ↓
Run Tests (Jest, Playwright)
   ↓
Build Docker Images
   ↓
Push to ECR
   ↓
Deploy to Staging (auto)
   ↓
Run E2E Tests
   ↓
Manual Approval
   ↓
Deploy to Production (blue-green)
   ↓
Health Checks
   ↓
Route Traffic / Rollback
```

### Monitoring & Observability

**Application Monitoring**
- APM: New Relic / Datadog
- Error tracking: Sentry
- Logs: CloudWatch / ELK
- Metrics: Prometheus + Grafana

**Alerts**
- High error rate (>1%)
- Slow response time (>500ms p95)
- High CPU/memory (>80%)
- Failed deployments
- Security events

**On-Call**
- PagerDuty integration
- 24/7 coverage (post-launch)
- Escalation policies
- Incident response playbooks

---

## Integration Architecture

### Payment Integration (Stripe Connect)

**Flow**
```
Investor → Platform → Stripe Connect → Escrow Account
                                             ↓
                                    Project Developer
```

**Features**
- Multi-party payments
- Automatic fee collection
- Payout scheduling
- Refund handling

### Banking Integration (Plaid)

**Use Cases**
- Bank account verification
- Balance checking
- ACH transfers
- Identity verification

### E-Signature (DocuSign)

**Flow**
```
Generate Agreement → Send via DocuSign → Investor Signs
                                              ↓
                                    Webhook Callback
                                              ↓
                                    Complete Investment
```

### Third-Party APIs

**RESTful Integration Pattern**
```javascript
// Example: Plaid integration
const client = new PlaidApi({
  clientId: process.env.PLAID_CLIENT_ID,
  secret: process.env.PLAID_SECRET,
  env: 'production'
});

const response = await client.accountsGet({
  access_token: user.plaid_access_token
});
```

---

## Future Technology Considerations

### Blockchain Integration (Exploratory)

**Potential Use Cases**
- Tokenized project shares
- Smart contract-based distributions
- Transparent transaction ledger
- Secondary market trading

**Technology Options**
- Ethereum / Polygon (EVM-compatible)
- Solana (high throughput)
- Private blockchain (Hyperledger)

**Considerations**
- Regulatory clarity needed
- High implementation cost
- Security audit requirements
- User education challenges

**Timeline**: Not before Year 3, pending regulatory clarity

---

## Technical Team Structure

### Year 1 Team (5 FTEs)

**CTO** (Hire Month 1)
- Architecture decisions
- Technical leadership
- Vendor management

**Senior Full-Stack Developers** (2, Hire Month 1-2)
- React + TypeScript frontend
- NestJS backend
- Database design

**DevOps Engineer** (Hire Month 3)
- Infrastructure setup
- CI/CD pipeline
- Monitoring

**QA Engineer** (Hire Month 4)
- Test automation
- Security testing
- Performance testing

### Year 2 Team (18 FTEs)

- CTO
- Engineering Managers (2)
- Senior Engineers (6)
- Mid-level Engineers (4)
- DevOps Engineers (2)
- QA Engineers (2)
- Data Engineer (1)

---

## Appendix: Technical Decisions Log

### Why Node.js/NestJS?

**Pros**
- JavaScript everywhere (frontend + backend)
- Large ecosystem (npm)
- Good for I/O-heavy operations
- Strong TypeScript support
- NestJS provides structure

**Cons**
- Single-threaded (mitigated with clustering)
- Less performant for CPU-heavy tasks

**Decision**: Use Node.js for API services, Python for AI/ML services

---

### Why PostgreSQL over MySQL?

**Pros**
- Better support for complex queries
- JSON support (JSONB)
- Advanced features (window functions, CTEs)
- Strong community
- Better compliance with SQL standards

**Decision**: PostgreSQL for primary database

---

### Why Microservices?

**Pros**
- Independent scaling
- Technology flexibility
- Team autonomy
- Fault isolation

**Cons**
- Increased complexity
- Network latency
- Distributed tracing needed

**Decision**: Start with modular monolith, extract to microservices as needed (Month 6+)

---

## Questions & Contact

**Technical Questions**: dev@luminousdynamics.org
**Security Questions**: security@luminousdynamics.org
**Architecture Review**: Available in data room (detailed diagrams, sequence diagrams)

---

**Last Updated**: January 2025
**Version**: 1.0
**Status**: Pre-Development (Architecture Complete)

---

*This architecture is designed to be robust, scalable, and compliant while remaining pragmatic for a Pre-Seed startup. We will build incrementally, validating assumptions with real users before over-engineering.*
