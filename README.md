# RapidBoot

RapidBoot accelerates Spring Boot application development with a visual entity modeler, real-time collaboration, and automatic API documentation for a smooth idea-to-scaffold workflow [web:13][web:1]. It combines Vue 3, Vuetify, and Vue Flow on the frontend with Spring Boot, OpenAPI, WebSocket/STOMP, and MySQL on the backend to provide code generation, schema visualization, and strong developer ergonomics out of the box [web:16][web:9]. 

## Features

- Visual entity modeling with nodes and edges in Vue Flow, including zoom, pan, selection, and edge connections for fast schema design [web:13][web:19].  
- Automatic REST API scaffolding and OpenAPI 3 documentation with Swagger UI for discoverability and contract-first workflows [web:2][web:1].  
- Real-time multi-user collaboration via STOMP/WebSocket channels for synchronized diagram edits and live updates [web:9][web:12].  
- Database visualization and documentation powered by the same model, enabling ER-style schema views and artifact generation [web:13][web:19].  
- Integration testing ready with Testcontainers MySQL to validate JPA and repository behavior against a real engine when needed [web:46][web:74].  
- Migration-friendly with Flyway versioned scripts to keep environments reproducible and changes auditable [web:56][web:50].  
- Contribution-ready with Conventional Commits and Semantic Versioning for consistent history and predictable releases [web:21][web:32].  

## Architecture Overview

The frontend is a Vue 3 application that uses Vue Flow for interactive graph editing, wiring node and edge state through composables for a responsive modeler UI [web:13][web:19]. The backend is a Spring Boot service exposing REST endpoints documented with springdoc-openapi and real-time STOMP endpoints for collaboration, backed by MySQL with migration control [web:1][web:9]. 

## Tech Stack

| Area | Technology |
| --- | --- |
| Frontend | Vue 3 + Vue Flow for graph modeling and editor UX [web:13]. |
| Backend | Spring Boot REST + springdoc-openapi for OpenAPI 3 [web:2]. |
| Realtime | STOMP/WebSocket with simple broker and topic/app prefixes [web:9]. |
| Database | MySQL as primary datastore [web:46]. |
| Migrations | Flyway versioned SQL migrations [web:56]. |
| Testing | Testcontainers MySQL and Spring Boot built-in support [web:74]. |
| Standards | Conventional Commits and SemVer [web:21][web:32]. |
| Community | GitHub community health files and contribution templates [web:27]. |

## Screenshots

Add UI screenshots or short GIFs of the modeler and generated docs here to help users understand the workflow at a glance following README best practices [web:94][web:97]. 

## Getting Started

### Prerequisites

- Java 17, Maven, Node.js, and a Docker-compatible runtime for optional Testcontainers workflows during integration testing [web:74][web:62].  
- A local or containerized MySQL instance if not using Testcontainers in development [web:46][web:62].  

### Installation

- Clone the repository and install dependencies for both the frontend and backend to prepare for development and local runs, following common README structure guidance [web:94][web:92].  
- Configure environment variables and application properties for database connectivity and ports before starting services to avoid connection errors [web:94][web:97].  

### Quick Start

- Backend: run the Spring Boot application to expose REST APIs, OpenAPI docs, and STOMP endpoints for collaboration [web:1][web:9].  
- Frontend: start the Vue dev server and open the UI to begin modeling entities and relationships using Vue Flow [web:13][web:19].  

## Configuration

- Database: set MySQL connection properties for development and CI; alternatively, use the Testcontainers JDBC URL for disposable DBs during tests \(e.g., jdbc:tc:mysql:8.0.x:///dbname\) [web:46][web:81].  
- OpenAPI: configure springdoc properties as needed, with defaults serving /v3/api-docs and Swagger UI for browsing the API [web:2][web:1].  

## Usage

### Model Entities

Use Vue Flow to create nodes for entities and edges for relationships, leveraging built-in controls and event hooks for editing and persistence of diagram state [web:13][web:19]. Save and load graph JSON to map diagram elements to backend entity definitions prior to generation [web:13][web:19]. 

### Generate Code

Generate Spring Boot entities, repositories, services, and controllers aligned with the modeled schema, and verify endpoint coverage and payloads in Swagger UI [web:2][web:1]. Commit generated artifacts along with migration scripts to ensure reproducibility across environments [web:56][web:50]. 

### Visualize & Document

Render ER-style diagrams from the data model in the UI and export documentation artifacts that accompany the OpenAPI-generated reference to keep schema and API docs synchronized [web:13][web:2]. Ensure updates to entities propagate to the diagram and the API spec to minimize drift in documentation [web:1][web:19]. 

### Real-time Collaboration

Enable live editing using STOMP/WebSocket with application destinations \(e.g., /app/…\) and topic subscriptions \(e.g., /topic/…\) for collaborative sessions and change broadcasting [web:9][web:12]. Configure the message broker with conventional prefixes to keep client and server aligned [web:9][web:12]. 

## API and Docs

- OpenAPI: the API specification is generated automatically and exposed under /v3/api-docs in JSON and YAML formats for client generation and testing [web:2][web:1].  
- Swagger UI: a browsable UI is served to explore endpoints, parameters, and models for faster verification during development [web:2][web:14].  

## Testing

- Unit tests: cover business logic without external dependencies to keep feedback fast during early development cycles [web:94][web:97].  
- Integration tests: use Testcontainers MySQL to validate JPA mappings and repository queries against a real engine, optionally via jdbc:tc for zero-setup ephemeral databases [web:46][web:81].  
- Spring Boot support: Boot’s built-in Testcontainers integration simplifies lifecycle and configuration for containerized dependencies in tests and local runs [web:74][web:69].  

## Database Migrations

- Use Flyway versioned scripts \(e.g., V1__init.sql\) to apply schema changes deterministically, with an immutable history and new scripts for subsequent modifications [web:56][web:50].  
- Run migrations on application startup in all environments, including tests, to keep code and schema evolving together without manual steps [web:56][web:50].  

## Security

Secure WebSocket endpoints using Spring’s WebSocketMessageBrokerConfigurer and integrate with Spring Security to protect STOMP destinations and subscriptions [web:12]. Prefer application destinations for inbound messages and topic destinations for pub-sub broadcasting to align with recommended patterns [web:9]. 

## Project Structure

A typical layout separates the Vue frontend and Spring Boot backend, includes a migration directory for Flyway, and a tests module for integration tests using Testcontainers, alongside a docs directory for API artifacts and schema documentation [web:56][web:74]. Provide a CONTRIBUTING guide and templates at the repo root or via a .github folder for easy discovery [web:27]. 

## Contributing

- Use Conventional Commits for commit messages and Semantic Versioning for releases to maintain clean history and predictable versioning [web:21][web:32].  
- Include CONTRIBUTING, CODE_OF_CONDUCT, and issue/PR templates via community health files to streamline onboarding and set expectations [web:27][web:30].  

## Roadmap

- MVP: visual modeler, code generation, OpenAPI docs, and basic schema visualization for end-to-end scaffolding [web:1][web:13].  
- V1.0: real-time collaboration over STOMP/WebSocket for multi-user editing with synchronized updates in the UI [web:9][web:12].  
- Future: expanded database support, richer templates, and deeper testing coverage with Testcontainers patterns and Flyway workflows [web:46][web:56].  

## FAQ

- Is Testcontainers required in pre-development stage? Not strictly, but adding a minimal setup when the first DB-backed feature lands prevents environment drift and H2-vs-MySQL mismatches while staying low-friction with Boot’s built-in integration and jdbc:tc usage [web:74][web:81].  

## License

Add your chosen license file and reference it here to set clear usage and contribution expectations following README best practices [web:94][web:97]. 

## Acknowledgments

This project incorporates and is inspired by Vue Flow, springdoc-openapi, Spring’s STOMP guide, Testcontainers, and Flyway documentation which inform architecture and implementation choices [web:13][web:1]. 
