# Supporting Technology

This page records the planned technology stack for the web application. Technologies marked **Selected** are current project decisions. Technologies marked **Proposed** are candidates that must be confirmed after the application requirements are better defined.

## Stack overview

| Area | Technology | Status | Purpose |
|---|---|---|---|
| Programming language | JavaScript | Selected | Shared language for browser and server development |
| Server runtime | Node.js | Selected | Runs the web server, API, and server-side application logic |
| Package management | npm | Selected | Manages dependencies and project scripts |
| API style | REST-style HTTP API using JSON | Proposed | Provides a clear interface between the web client and server |
| API framework | Express or Fastify | Proposed | Routing, middleware, request validation, and HTTP responses |
| Web client | HTML, CSS, and JavaScript | Selected | Provides the browser-based user interface |
| Frontend framework | React, Vue, or no framework | To be evaluated | Organizes interactive UI components if application complexity requires it |
| Database | PostgreSQL or SQLite | To be evaluated | Stores persistent application data |
| Database access | Query builder or ORM | To be evaluated | Provides migrations, queries, and application-level data models |
| Unit and integration testing | Vitest or Jest | Proposed | Tests client and server modules and API behavior |
| API testing | Supertest or equivalent | Proposed | Exercises HTTP endpoints during automated tests |
| End-to-end testing | Playwright | Proposed | Tests important workflows through a real browser |
| Code quality | ESLint and Prettier | Proposed | Enforces consistent code quality and formatting |
| Version control and collaboration | Git and GitHub | Selected | Tracks source, documentation, issues, and project history |
| Continuous integration | GitHub Actions | Proposed | Runs checks and tests for pushed changes and pull requests |
| Containerization | Docker | Optional | Provides a reproducible development or deployment environment if needed |

## Application structure

The application is planned as two main layers:

1. A browser-based web client built with HTML, CSS, and JavaScript.
2. A Node.js server that exposes an HTTP API, applies business rules, and accesses persistent data.

The client and server will exchange JSON over HTTPS. Keeping the user interface separate from the API allows each layer to be tested independently and makes the API reusable by other clients if the project later requires them.

## API plan

The initial API will follow resource-oriented HTTP conventions:

- endpoints will use nouns that identify application resources;
- HTTP methods such as `GET`, `POST`, `PUT` or `PATCH`, and `DELETE` will express operations;
- request and response bodies will use JSON;
- HTTP status codes will communicate successful and failed results;
- incoming data will be validated before use; and
- errors will use a consistent response structure without exposing sensitive implementation details.

API endpoints and data schemas will be documented after the project domain and core resources are identified. An OpenAPI description may be added if it provides enough value for the project scope.

## Node.js server

Node.js is selected because it supports JavaScript across the full application stack and has a mature ecosystem for web APIs, testing, validation, and database access. The server will be responsible for:

- HTTP routing and API responses;
- validation and sanitization of user input;
- business logic;
- authentication and authorization if required;
- database operations;
- structured error handling; and
- server-side logging.

The API framework will be selected after a small comparison of Express and Fastify. The comparison should consider learning curve, validation support, documentation, plugin maturity, testing, and suitability for the expected workload.

## Web client

The client will use standard HTML, CSS, and JavaScript. A frontend framework is not yet selected. The team should first identify the number and complexity of interactive views, shared state, routing needs, and accessibility requirements. A framework should be introduced only if those requirements justify its additional tooling and complexity.

The interface should use semantic HTML, responsive layouts, keyboard-accessible controls, and clear feedback for loading and error states.

## Data storage

The data requirements are not yet defined, so the database remains an open decision:

- **SQLite** may be appropriate for a small prototype or single-instance deployment.
- **PostgreSQL** may be appropriate when the system needs concurrent access, stronger deployment support, or more advanced relational features.

The final decision will consider the data model, expected workload, hosting environment, backup needs, and capstone timeline.

## Development and quality practices

The repository should provide npm scripts for development, testing, linting, formatting, and production startup. Automated tests should cover business logic, API endpoints, and a small number of critical user workflows. Proposed GitHub Actions checks will run these validations before changes are merged.

Dependencies and secrets must be handled carefully:

- commit a lockfile for reproducible dependency installation;
- keep credentials and secrets out of Git;
- use environment variables for deployment-specific configuration;
- validate all data at trust boundaries; and
- review and update dependencies throughout development.

## Open decisions

- Which API framework best fits the final requirements: Express or Fastify?
- Does the client need a framework, and if so, which one?
- Which database fits the data model and deployment environment?
- Is authentication required, and what roles or permissions will exist?
- Where will the application be hosted?
- Is Docker useful for the selected deployment approach?

