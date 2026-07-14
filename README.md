# Shopping Cart Microservice Project

A scalable, event-driven microservices project for an online shopping cart system, covering product and inventory management, order processing, service discovery, and secure API access.

## Features

- **Product & Inventory Management** — full CRUD operations for products and stock levels, with inventory checks tied into the order flow.
- **Order Service** — creates and manages customer orders, validating inventory availability before confirming a purchase.
- **Service Discovery** — a Eureka server registers and discovers all microservice instances, enabling dynamic scaling without hardcoded service locations.
- **API Gateway** — a single entry point that routes external requests to the correct downstream service, keeping internal service URLs hidden from clients.
- **Authentication & Authorization** — secured with Spring Security and OAuth 2.0, so protected endpoints require a valid access token.
- **Event-Driven Communication** — Kafka (backed by Zookeeper) streams real-time events between services, e.g. order-created or inventory-updated events, decoupling services from direct synchronous calls.
- **Circuit Breaking & Fault Tolerance** — Resilience4j wraps inter-service calls so a failing downstream service degrades gracefully instead of cascading failures.
- **Distributed Tracing** — requests are traced across services with Spring Cloud Sleuth/Brave and visualized in Zipkin, making it easier to debug latency and failures in a multi-service call chain.
- **Monitoring & Metrics** — Prometheus scrapes service metrics and Grafana dashboards visualize system health in real time.
- **Persistence** — Spring Data JPA with a MySQL backend for data storage, with each service managing its own schema.
- **Containerization** — Docker support for running supporting infrastructure (Kafka, Zookeeper, MySQL, monitoring stack) consistently across environments.

## Tech Stack

- Java 21
- Spring Boot 3.x
- Spring Security
- Lombok
- Spring Data JPA
- MySQL Driver
- Maven 3.x
- Spring Cloud Eureka (server and discovery client)
- Spring Cloud API Gateway
- Spring Cloud Sleuth/Brave tracer, Zipkin UI
- Spring Cloud Resilience4j circuit breaker
- Zookeeper and Kafka 3.x
- Prometheus & Grafana
- Docker
- OAuth 2.0

## Prerequisites

- [Java 21](https://www.oracle.com/java/technologies/downloads/)
- [Maven 3.x](https://maven.apache.org/download.cgi)
- [MySQL Workbench](https://dev.mysql.com/downloads/workbench/)
- [IntelliJ IDEA](https://www.jetbrains.com/idea/download/) (or any Java IDE)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

## Getting Started

1. Clone the repository:
   ```bash
   git clone <repository-url>
   ```
2. Navigate to the project directory:
   ```bash
   cd shopping-cart-microservice
   ```
3. Build the application:
   ```bash
   mvn clean package
   ```
4. Build and start the Docker containers:
   ```bash
   docker compose up -d
   ```
5. Update the database connection settings in each service's `application.properties` file.
6. Run the application:
   - Start the discovery server first and wait until it's up.
   - Start the remaining services, including the API Gateway.
   - Services are not yet containerized individually, so run each one separately.

## Architecture

The project follows a microservices architecture:

- **Discovery Server (Eureka)** — central registry all services register with on startup.
- **API Gateway** — routes and load-balances incoming requests to the appropriate service.
- **Product/Inventory Service** — owns product catalog and stock data.
- **Order Service** — owns order lifecycle, consulting inventory before confirming orders.
- **Kafka/Zookeeper** — message broker enabling asynchronous, event-driven communication between services.
- **Zipkin** — collects and visualizes distributed traces across the service call chain.
- **Prometheus/Grafana** — collects and visualizes service-level metrics for monitoring.

## License

No license specified.
