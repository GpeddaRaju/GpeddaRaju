# 🚀 Enterprise Microservices Architecture

[![Java](https://img.shields.io/badge/Java-17+-orange.svg)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2+-green.svg)](https://spring.io/projects/spring-boot)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

> A scalable, production-ready microservices architecture built with Java, Spring Boot, and Spring Cloud ecosystem.

**Designed & Developed by:** [Gadige Peddaraju](https://github.com/yourusername)  
**Tech Stack:** Java, Spring Boot, Oracle, Docker, Kubernetes

---

## 📋 Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Microservices](#microservices)
- [Technology Stack](#technology-stack)
- [Getting Started](#getting-started)
- [API Documentation](#api-documentation)
- [Deployment](#deployment)
- [Monitoring & Observability](#monitoring--observability)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

This project demonstrates a **production-grade microservices architecture** implementing industry best practices for building scalable, resilient, and maintainable distributed systems. It showcases:

✅ **Service Discovery** with Netflix Eureka  
✅ **API Gateway** for centralized routing & authentication  
✅ **Distributed Configuration** with Spring Cloud Config  
✅ **Inter-service Communication** via REST & messaging  
✅ **Containerization** with Docker & orchestration with Kubernetes  
✅ **Observability** through monitoring, logging, and tracing  
✅ **Security** with JWT-based authentication & authorization  

---

## 🏗️ Architecture

### System Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                        Client Layer                          │
│              (Web, Mobile, Third-party Apps)                 │
└────────────────────┬────────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────────┐
│                      API Gateway                             │
│         (Routing, Auth, Rate Limiting, Load Balancing)       │
└─┬──────────┬──────────┬──────────┬──────────┬──────────────┘
  │          │          │          │          │
  ▼          ▼          ▼          ▼          ▼
┌───────┐ ┌────────┐ ┌───────┐ ┌─────────┐ ┌──────────────┐
│ User  │ │Product │ │ Order │ │ Payment │ │Notification  │
│Service│ │Service │ │Service│ │ Service │ │   Service    │
└───┬───┘ └───┬────┘ └───┬───┘ └────┬────┘ └──────┬───────┘
    │         │          │          │             │
    ▼         ▼          ▼          ▼             ▼
┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐  ┌─────────┐
│User DB │ │Prod DB │ │Order DB│ │Pay DB  │  │ Kafka/  │
│(Oracle)│ │(MySQL) │ │(Oracle)│ │(Oracle)│  │RabbitMQ │
└────────┘ └────────┘ └────────┘ └────────┘  └─────────┘
     │          │          │          │            │
     └──────────┴──────────┴──────────┴────────────┘
                         │
                         ▼
            ┌──────────────────────────┐
            │  Infrastructure Layer     │
            ├──────────────────────────┤
            │ • Service Discovery       │
            │ • Config Server          │
            │ • Redis Cache            │
            │ • Monitoring (Prometheus)│
            │ • Logging (ELK Stack)    │
            └──────────────────────────┘
```

### Key Design Patterns

- **API Gateway Pattern**: Single entry point for all clients
- **Database per Service**: Each microservice owns its database
- **Event-Driven Architecture**: Asynchronous communication via message queues
- **Circuit Breaker**: Resilience4j for fault tolerance
- **CQRS**: Separate read/write operations for scalability
- **Saga Pattern**: Distributed transaction management

---

## 🔧 Microservices

### 1. **API Gateway Service**
- **Port**: 8080
- **Responsibilities**: 
  - Request routing to appropriate microservices
  - Authentication & authorization (JWT validation)
  - Rate limiting & throttling
  - Load balancing
- **Tech**: Spring Cloud Gateway, JWT

### 2. **User Service**
- **Port**: 8081
- **Responsibilities**: 
  - User registration & authentication
  - Profile management
  - Role-based access control (RBAC)
  - Password encryption (BCrypt)
- **Database**: Oracle / PostgreSQL
- **Endpoints**:
  - `POST /api/users/register` - Register new user
  - `POST /api/users/login` - User authentication
  - `GET /api/users/{id}` - Get user profile
  - `PUT /api/users/{id}` - Update user profile

### 3. **Product Service**
- **Port**: 8082
- **Responsibilities**: 
  - Product catalog management
  - Inventory tracking
  - Product search & filtering
  - Category management
- **Database**: MySQL / Oracle
- **Caching**: Redis for frequently accessed products
- **Endpoints**:
  - `GET /api/products` - Get all products (paginated)
  - `GET /api/products/{id}` - Get product details
  - `POST /api/products` - Create product (Admin)
  - `PUT /api/products/{id}` - Update product (Admin)
  - `DELETE /api/products/{id}` - Delete product (Admin)

### 4. **Order Service**
- **Port**: 8083
- **Responsibilities**: 
  - Order creation & validation
  - Order status management
  - Inventory reservation
  - Integration with Payment & Notification services
- **Database**: PostgreSQL / Oracle
- **Messaging**: Kafka for order events
- **Endpoints**:
  - `POST /api/orders` - Create new order
  - `GET /api/orders/{id}` - Get order details
  - `GET /api/orders/user/{userId}` - Get user orders
  - `PUT /api/orders/{id}/status` - Update order status

### 5. **Payment Service**
- **Port**: 8084
- **Responsibilities**: 
  - Payment processing
  - Payment gateway integration (Stripe, PayPal, Razorpay)
  - Transaction history
  - Refund management
- **Database**: Oracle
- **Security**: PCI-DSS compliant
- **Endpoints**:
  - `POST /api/payments/process` - Process payment
  - `GET /api/payments/{id}` - Get payment details
  - `POST /api/payments/{id}/refund` - Initiate refund

### 6. **Notification Service**
- **Port**: 8085
- **Responsibilities**: 
  - Email notifications (via SendGrid/SMTP)
  - SMS notifications (via Twilio)
  - Push notifications
  - Event-driven notifications
- **Messaging**: Kafka consumer for order/payment events
- **Endpoints**:
  - `POST /api/notifications/email` - Send email
  - `POST /api/notifications/sms` - Send SMS

---

## 💻 Technology Stack

### Backend
- **Java**: 17+ (LTS)
- **Spring Boot**: 3.2+
- **Spring Cloud**: 2023.x
- **Spring Data JPA**: Database interactions
- **Hibernate**: ORM
- **Maven**: Build & dependency management

### Databases
- **Oracle**: Primary relational database
- **PostgreSQL**: Alternative RDBMS
- **MySQL**: Product catalog
- **MongoDB**: Document store (optional)
- **Redis**: In-memory cache & session store

### Messaging
- **Apache Kafka**: Event streaming
- **RabbitMQ**: Message queue (alternative)

### Security
- **Spring Security**: Authentication & authorization
- **JWT**: Stateless authentication tokens
- **OAuth 2.0**: Third-party authentication
- **BCrypt**: Password hashing

### DevOps & Infrastructure
- **Docker**: Containerization
- **Kubernetes**: Container orchestration
- **Jenkins**: CI/CD pipeline
- **Git**: Version control
- **Nginx**: Reverse proxy & load balancing

### Monitoring & Logging
- **Prometheus**: Metrics collection
- **Grafana**: Metrics visualization
- **ELK Stack**: Centralized logging
  - Elasticsearch: Log storage
  - Logstash: Log processing
  - Kibana: Log visualization
- **Zipkin/Jaeger**: Distributed tracing

### Testing
- **JUnit 5**: Unit testing
- **Mockito**: Mocking framework
- **TestContainers**: Integration testing
- **Postman**: API testing

---

## 🚀 Getting Started

### Prerequisites

```bash
# Required software
- Java 17 or higher
- Maven 3.8+
- Docker & Docker Compose
- Kubernetes (Minikube/Kind for local)
- Oracle Database (or PostgreSQL)
- Redis
- Kafka
```

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/microservices-architecture.git
cd microservices-architecture
```

2. **Build all services**
```bash
mvn clean install -DskipTests
```

3. **Start infrastructure services using Docker Compose**
```bash
docker-compose up -d
```

This will start:
- Eureka Server (http://localhost:8761)
- Config Server (http://localhost:8888)
- Kafka & Zookeeper
- Redis
- Databases (Oracle, MySQL, PostgreSQL)

4. **Run individual microservices**

```bash
# User Service
cd user-service
mvn spring-boot:run

# Product Service
cd product-service
mvn spring-boot:run

# Order Service
cd order-service
mvn spring-boot:run

# Payment Service
cd payment-service
mvn spring-boot:run

# Notification Service
cd notification-service
mvn spring-boot:run

# API Gateway
cd api-gateway
mvn spring-boot:run
```

5. **Access the application**
- API Gateway: http://localhost:8080
- Eureka Dashboard: http://localhost:8761
- Config Server: http://localhost:8888

---

## 📚 API Documentation

### Authentication

All protected endpoints require JWT token in the Authorization header:

```http
Authorization: Bearer <your-jwt-token>
```

### Sample API Requests

#### 1. User Registration
```bash
curl -X POST http://localhost:8080/api/users/register \
  -H "Content-Type: application/json" \
  -d '{
    "username": "johndoe",
    "email": "john@example.com",
    "password": "SecurePass123",
    "firstName": "John",
    "lastName": "Doe"
  }'
```

#### 2. User Login
```bash
curl -X POST http://localhost:8080/api/users/login \
  -H "Content-Type: application/json" \
  -d '{
    "username": "johndoe",
    "password": "SecurePass123"
  }'
```

#### 3. Get Products
```bash
curl -X GET http://localhost:8080/api/products?page=0&size=10 \
  -H "Authorization: Bearer <token>"
```

#### 4. Create Order
```bash
curl -X POST http://localhost:8080/api/orders \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{
    "userId": 1,
    "items": [
      {"productId": 101, "quantity": 2},
      {"productId": 102, "quantity": 1}
    ],
    "shippingAddress": "123 Main St, City, Country"
  }'
```

**Full API Documentation**: Available at http://localhost:8080/swagger-ui.html

---

## 🐳 Deployment

### Docker Deployment

Build Docker images for all services:

```bash
# Build images
docker build -t user-service:1.0 ./user-service
docker build -t product-service:1.0 ./product-service
docker build -t order-service:1.0 ./order-service
docker build -t payment-service:1.0 ./payment-service
docker build -t notification-service:1.0 ./notification-service
docker build -t api-gateway:1.0 ./api-gateway

# Run with Docker Compose
docker-compose up -d
```

### Kubernetes Deployment

```bash
# Create namespace
kubectl create namespace microservices

# Deploy infrastructure
kubectl apply -f k8s/infrastructure/

# Deploy services
kubectl apply -f k8s/services/

# Verify deployments
kubectl get pods -n microservices
kubectl get services -n microservices
```

### Environment Variables

Create `.env` file for each service:

```env
# Database Configuration
DB_HOST=localhost
DB_PORT=1521
DB_NAME=microservicesdb
DB_USERNAME=admin
DB_PASSWORD=secure_password

# Redis Configuration
REDIS_HOST=localhost
REDIS_PORT=6379

# Kafka Configuration
KAFKA_BOOTSTRAP_SERVERS=localhost:9092

# JWT Configuration
JWT_SECRET=your-secret-key-here
JWT_EXPIRATION=86400000

# Email Configuration
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USERNAME=your-email@gmail.com
SMTP_PASSWORD=your-password
```

---

## 📊 Monitoring & Observability

### Prometheus Metrics
Access metrics at: http://localhost:9090

Key metrics monitored:
- Request rate & latency
- Error rates (4xx, 5xx)
- JVM memory & CPU usage
- Database connection pool stats
- Cache hit/miss ratio

### Grafana Dashboards
Access dashboards at: http://localhost:3000 (admin/admin)

Pre-configured dashboards:
- Service health overview
- API Gateway metrics
- Database performance
- Kafka consumer lag
- JVM monitoring

### Centralized Logging (ELK)
Access Kibana at: http://localhost:5601

Log aggregation from all services with:
- Request/response logs
- Error stack traces
- Performance metrics
- Audit logs

### Distributed Tracing
Access Zipkin at: http://localhost:9411

Trace requests across microservices to identify:
- Latency bottlenecks
- Service dependencies
- Error propagation

---

## 🧪 Testing

### Run Unit Tests
```bash
mvn test
```

### Run Integration Tests
```bash
mvn verify -P integration-tests
```

### Run All Tests with Coverage
```bash
mvn clean verify jacoco:report
```

View coverage report at: `target/site/jacoco/index.html`

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please ensure:
- Code follows Java coding standards
- All tests pass
- Documentation is updated
- Commit messages are descriptive

---

## 📝 Project Structure

```
microservices-architecture/
├── api-gateway/              # API Gateway service
├── user-service/             # User management service
├── product-service/          # Product catalog service
├── order-service/            # Order processing service
├── payment-service/          # Payment processing service
├── notification-service/     # Notification service
├── eureka-server/            # Service discovery
├── config-server/            # Centralized configuration
├── common-library/           # Shared utilities & DTOs
├── k8s/                      # Kubernetes manifests
│   ├── infrastructure/       # Infrastructure components
│   └── services/             # Service deployments
├── docker-compose.yml        # Local development setup
├── pom.xml                   # Parent POM
└── README.md                 # This file
```

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Gadige Peddaraju**

- 🎓 B.Tech in Electrical & Electronics Engineering
- 📧 Email: gadigeraju2003@gmail.com
- 📱 Phone: +91 9390891145
- 🔗 LinkedIn: [linkedin.com/in/yourprofile](https://linkedin.com/in/yourprofile)
- 💻 GitHub: [github.com/yourusername](https://github.com/yourusername)

---

## 🙏 Acknowledgments

- Spring Boot & Spring Cloud teams for excellent frameworks
- Open source community for amazing tools
- Industry best practices from Martin Fowler, Chris Richardson, and others

---

## 📚 Additional Resources

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Cloud Documentation](https://spring.io/projects/spring-cloud)
- [Microservices Patterns](https://microservices.io/patterns/)
- [Docker Documentation](https://docs.docker.com/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)

---

## 🎯 Roadmap

- [x] Basic microservices architecture
- [x] Service discovery & API gateway
- [x] Centralized configuration
- [x] Monitoring & logging
- [ ] GraphQL API support
- [ ] Advanced security (OAuth 2.0, RBAC)
- [ ] Auto-scaling with Kubernetes HPA
- [ ] Multi-region deployment
- [ ] Performance optimization
- [ ] Cloud deployment (AWS/Azure/GCP)

---

<div align="center">

**⭐ Star this repository if you find it helpful!**

Made with ❤️ by Gadige Peddaraju

</div>
