# DSCommerce | Spring Professional Challenge 05

A commerce REST API developed as an exercise in DevSuperior's Spring Professional course. This repository records my implementation and practice with application layers, persistence, validation, authentication, and authorization.

## Stack

- Java 21 and Spring Boot 3.4.3.
- Spring Web, Spring Data JPA, and Bean Validation.
- Spring Security, OAuth2 Authorization Server, and JWT resource server.
- H2 in-memory database for the default `test` profile.
- Maven Wrapper.

## Implementation

The application separates controllers, services, repositories, entities, and DTOs. Its domain includes products, categories, users, roles, orders, order items, and payments.

- Product lookup, paginated search by name, and CRUD operations.
- Category listing and authenticated user information.
- Order creation and retrieval.
- Role-based access rules for administrator and client operations.
- Request validation and centralized exception handling.

The security configuration includes a custom password grant as part of the course exercise. The default client configuration and sample database are intended for local study.

## Main endpoints

| Method | Path | Purpose |
| --- | --- | --- |
| GET | `/products` | Paginated product search, with an optional `name` parameter. |
| GET | `/products/{id}` | Product details. |
| POST | `/products` | Create a product, administrator role required. |
| PUT | `/products/{id}` | Update a product, administrator role required. |
| DELETE | `/products/{id}` | Delete a product, administrator role required. |
| GET | `/categories` | List categories. |
| GET | `/users/me` | Information about the authenticated user. |
| POST | `/orders` | Create an order, client role required. |
| GET | `/orders/{id}` | Retrieve an order, administrator role required. |
| POST | `/oauth2/token` | Issue an access token through the configured authorization server. |

## Run locally

Install a JDK compatible with Java 21, then clone the repository:

```bash
git clone https://github.com/MarcusCSPereira/SpringProfessional_desafio05.git
cd SpringProfessional_desafio05
bash mvnw spring-boot:run
```

On Windows, use `mvnw.cmd spring-boot:run`. The default profile uses H2 and loads the sample data in `src/main/resources/import.sql`.

With the default Spring Boot port, a product request is:

```bash
curl 'http://localhost:8080/products?name=&page=0&size=10'
```

Application settings are in `src/main/resources/application.properties`. Supported environment overrides include `APP_PROFILE`, `CLIENT_ID`, `CLIENT_SECRET`, `JWT_DURATION`, and `CORS_ORIGINS`.

## Checks

```bash
bash mvnw test
```

The repository currently contains an application context test. It does not yet provide a comprehensive automated test suite for the business rules.

## Learning context

This is a course exercise, not a production commerce service. The course base and challenge come from [DevSuperior](https://devsuperior.com.br/). My development history is available in the repository's commits.
