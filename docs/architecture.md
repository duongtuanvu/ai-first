# Project Architecture

## Purpose

High-level architecture and layering guidance for the backend and frontend.

## Technology Stack

- Backend: .NET 6, ASP.NET Core Web API, Entity Framework Core
- Frontend: React, TypeScript, Vite
- Database: SQL Server (or compatible RDBMS)

## Backend Layers (recommended)

- Presentation: Controllers / API endpoints
- Application: Services / Use cases
- Domain: Entities, domain logic, interfaces
- Infrastructure: Repositories, EF Core, external integrations
- Database: physical storage

Typical flow: Controller -> Service -> Repository -> DbContext

Guidelines:
- Keep controllers thin — orchestrate, don't contain business logic.
- Services implement application use-cases and coordinate repositories.
- Domain layer should contain business rules and domain entities.
- Infrastructure contains implementation details (EF mappings, third-party clients).

## Frontend Layers

- Pages / Routes
- Components (presentational and composite)
- Hooks (business logic and data fetching)
- Services / API clients
- API (backend endpoints)

Guidelines:
- Keep components presentational; place logic in hooks/services.
- Use feature-based grouping when the app scales (e.g., `features/products/`).

## Dependency Rules

- Do not skip layers. Each layer may depend only on the layer below it (or abstractions).
- Controllers -> Services -> Repositories -> DbContext (backend)
- Pages -> Components -> Hooks -> Services -> API (frontend)

## Cross-cutting concerns

- Logging, monitoring, error handling, and authentication should be implemented via middleware or shared services.
- Configuration should be centralized and environment-specific (appsettings, env vars).
- Use health checks and metrics endpoints for ops visibility.

## Deployment/Infra notes

- Prefer separate backend and frontend deployments; use a reverse proxy or CDN for frontend assets.
- Use staging and production environments; run CI/CD to deploy builds and migrations.

---

Link to detailed docs in `docs/` for conventions and coding standards.