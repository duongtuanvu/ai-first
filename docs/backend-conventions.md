# Backend Conventions

## Folder Structure

Controllers/

Services/

Repositories/

Models/

DTOs/

Mappings/

Interfaces/

## Naming

Controller

ProductController

Service

ProductService

Repository

ProductRepository

Interface

IProductService

IProductRepository

DTO

CreateProductRequest

UpdateProductRequest

ProductResponse

## API

GET

POST

PUT

DELETE

Return IActionResult

Validation uses FluentValidation (or DataAnnotations)

## Repository

Repositories contain database access only.

No business logic.

## Service

Business logic lives here.

Services may call multiple repositories.

## Controller

Controllers

- validate request
- call service
- return response

No business logic.

## Entity Framework

Use async methods.

Use AsNoTracking() for read-only queries.

Avoid N+1 queries.

Prefer Include only when necessary.

Always use CancellationToken if available.

## Dependency Injection

Register all services and repositories using DI.

Never instantiate dependencies manually.