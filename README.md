# Shopping Cart Microservice Project

A scalable microservice project for CRUD product and inventory management and order service.

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
   git clone https://github.com/ahmadhakimi/shopping-cart-microservice.git
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

The project follows a microservices architecture with service discovery (Eureka), centralized routing (API Gateway), distributed tracing (Zipkin), circuit breaking (Resilience4j), and event streaming (Kafka).

## License

No license specified.
