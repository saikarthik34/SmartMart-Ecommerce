# SmartMart – Full-Stack E-Commerce Application

SmartMart is an e-commerce application built with an Angular frontend and a Java Spring Boot backend. This repository is an adapted version of the upstream [Rohith2201/SmartMart](https://github.com/Rohith2201/SmartMart) project. The upstream project is distributed under the MIT License; see [LICENSE](LICENSE) and retain the original attribution when reusing or distributing the code.

## Features present in the source

- Product catalogue and product administration
- User registration, login and JWT-based authentication
- Role-protected administrator routes
- Shopping cart and order workflows
- Feedback submission and administration
- Payment page integration
- Spring Data JPA persistence and PostgreSQL driver
- API documentation through Springdoc OpenAPI
- Log4j2 application logging

> Feature availability and external integrations depend on valid local configuration. This repository does not include production credentials or guarantee that third-party services are active.

## Technology stack

| Area | Technology |
|---|---|
| Frontend | Angular 10, TypeScript, Angular Material |
| Backend | Java 17, Spring Boot 3.0.1, Spring Security |
| Persistence | Spring Data JPA / Hibernate |
| Database driver | PostgreSQL |
| API documentation | Springdoc OpenAPI |
| Build tools | npm and Maven Wrapper |

## Repository structure

```text
SmartMart-Ecommerce/
├── angularapp/                 # Angular frontend
│   └── src/app/                # Components, services, models and routes
├── springapp/                  # Spring Boot backend
│   ├── src/main/java/          # Controllers, services, repositories and models
│   └── src/main/resources/     # Application configuration and logging
├── .gitignore
├── LICENSE
└── README.md
```

## Prerequisites

- Java 17
- Node.js and npm compatible with Angular 10 / its older build tooling
- PostgreSQL database
- Git (optional, for version control)

Because this project uses Angular 10 and older build dependencies, use a compatible Node.js LTS release if the latest Node.js version produces OpenSSL or dependency errors.

## Configure the backend

The backend reads database credentials from environment variables. Create a PostgreSQL database, then set these variables in the terminal before starting Spring Boot:

| Variable | Description | Example (placeholder) |
|---|---|---|
| `DB_URL` | JDBC connection URL | `jdbc:postgresql://localhost:5432/smartmart` |
| `DB_USERNAME` | Database username | `postgres` |
| `DB_PASSWORD` | Database password | `your_local_password` |

Do not commit real passwords, tokens, or private API credentials.

### Start the backend

From the repository root:

**Windows PowerShell**

```powershell
$env:DB_URL="jdbc:postgresql://localhost:5432/smartmart"
$env:DB_USERNAME="postgres"
$env:DB_PASSWORD="your_local_password"
cd springapp
.\mvnw.cmd spring-boot:run
```

**macOS / Linux**

```bash
export DB_URL="jdbc:postgresql://localhost:5432/smartmart"
export DB_USERNAME="postgres"
export DB_PASSWORD="your_local_password"
cd springapp
chmod +x mvnw
./mvnw spring-boot:run
```

The backend is configured for `http://localhost:8080`. API documentation is configured at `/swagger-ui.html` (when the application starts successfully).

## Start the frontend

Open a second terminal:

```bash
cd angularapp
npm install
npm start
```

The Angular development server is configured for `http://localhost:8081`.

If the legacy Angular build tooling reports an OpenSSL error on a newer Node.js release, use a Node.js version compatible with Angular 10 rather than changing dependencies blindly.

## Before deploying

- Configure database credentials as environment variables or through your hosting provider's secret manager.
- Review and restrict payment-provider client IDs and third-party chatbot configuration in `angularapp/src/index.html`.
- Configure allowed frontend origins in the backend CORS configuration.
- Replace development URLs with the deployed API URL.
- Use HTTPS and production-grade database credentials.
- Review authentication, authorization, validation and payment flows before accepting real users or payments.
- Add screenshots and deployment URLs only after verifying that they work.

## Development notes

The frontend and backend are separate applications and must both be running for the complete local experience. Some integrations require external account setup and may not work with placeholder or expired credentials.

## License and attribution

This project retains the upstream MIT License. See [LICENSE](LICENSE) for the license text and the upstream repository for original project history: [Rohith2201/SmartMart](https://github.com/Rohith2201/SmartMart).
