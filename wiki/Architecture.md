# Architecture

This page is the living description of the proposed system architecture. It should explain the system at a high level before documenting implementation details.

## Status

**Phase:** Background research and requirements discovery  
**Architecture status:** Initial web application structure proposed

The current plan is a browser-based JavaScript client connected to a Node.js HTTP API. See [[Supporting Technology]] for the stack plan and the status of individual technology decisions.

## Architectural goals

The architecture should be evaluated against the project's confirmed requirements. Likely quality concerns include:

- maintainability and clear separation of responsibilities;
- security and privacy appropriate to the data involved;
- reliability and useful error handling;
- performance appropriate to expected workloads;
- accessibility and usability for intended users; and
- feasibility within the capstone schedule and team resources.

These are provisional until the project scope and stakeholders are defined.

## System context

Document the following when the project topic is selected:

- primary users and other stakeholders;
- external systems, services, and data sources;
- the system boundary;
- important inputs and outputs; and
- trust boundaries or privacy constraints.

## Proposed components

| Component | Responsibility | Inputs | Outputs | Technology | Status |
|---|---|---|---|---|---|
| Web client | Present the user interface and collect user input | User actions and API responses | Rendered views and API requests | HTML, CSS, and JavaScript | Selected |
| Application API | Expose application operations and coordinate requests | HTTPS requests containing JSON | JSON responses and HTTP status codes | Node.js with Express or Fastify | Proposed |
| Business-logic layer | Apply application rules independently of HTTP and storage details | Validated application data | Results or domain errors | JavaScript modules | Proposed |
| Data-access layer | Read and write persistent application data | Queries or repository calls | Stored or retrieved records | PostgreSQL or SQLite with a query builder or ORM | To be evaluated |

## Data

Describe the data model, ownership, storage, retention, validation, and any sensitive information handled by the system.

## Interfaces and data flow

The initial request flow is:

1. A user performs an action in the browser.
2. The web client sends an HTTPS request to the Node.js API.
3. The API validates the request and invokes the appropriate business logic.
4. The business-logic layer reads or writes data through the data-access layer when necessary.
5. The API returns a JSON response and an appropriate HTTP status code.
6. The web client updates the interface or presents a useful error message.

The exact endpoints and data schemas will be defined after the domain resources are identified.

## Deployment

Document target environments, build and deployment processes, configuration, observability, backups, and external dependencies.

## Security and privacy

Record authentication, authorization, secrets management, encryption, input validation, dependency risks, and relevant privacy constraints.

## Architecture decisions

Major decisions should record the context, considered alternatives, decision, rationale, and consequences.

| Date | Decision | Status | Rationale | Consequences |
|---|---|---|---|---|
| _To be determined_ | | Proposed | | |

## Open questions

- What are the confirmed functional and non-functional requirements?
- Which users and external systems are inside the initial scope?
- What data will the system process, and where will it originate?
- Which architectural constraints follow from the capstone timeline?
- Which API framework, frontend approach, and database best fit the confirmed requirements?
