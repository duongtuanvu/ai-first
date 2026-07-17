# Backend Conventions

## Folder Structure

# Backend Conventions

## Purpose

Conventions for backend code structure, naming, API behavior, and data access patterns.

## Folder structure

- `Controllers/` — API controllers only
- `Services/` — business logic
- `Repositories/` — data access
- `Models/` — domain models/entities
- `DTOs/` — request/response DTOs
- `Mappings/` — AutoMapper or manual mappers
- `Interfaces/` — abstractions for services/repositories

Keep folders shallow and group by feature when the codebase grows (feature-first layout).

## Naming conventions

- Controllers: `ProductController`
- Services: `ProductService`, interface `IProductService`
- Repositories: `ProductRepository`, interface `IProductRepository`
- DTOs: `CreateProductRequest`, `UpdateProductRequest`, `ProductResponse`

Follow PascalCase for types and methods. Use clear, descriptive names.

## API controllers

- Controllers should: validate input, call a service, and return an appropriate `IActionResult`.
- Do not put business logic in controllers.
- Consistently return problem details for errors (`ProblemDetails` / RFC7807) when applicable.

## Services

- Business logic belongs in services. Services can orchestrate multiple repositories and other services.
- Keep service methods focused and unit-testable.

## Repositories

- Repositories handle only data access (queries, inserts, updates, deletes).
- Avoid embedding business rules in repositories.

## Validation

- Use FluentValidation for complex validation rules; DataAnnotations are acceptable for simple cases.
- Return `400 Bad Request` with validation details when validation fails.

## Entity Framework / Data access

- Use async methods (e.g., `ToListAsync`, `FirstOrDefaultAsync`).
- Use `AsNoTracking()` for read-only queries.
- Avoid N+1 queries; prefer explicit `Include` or optimized projections.
- Prefer projections (select into DTO) for large result sets.
- Always pass `CancellationToken` from controller to service to repository when available.

## Dependency Injection

- Register services and repositories in DI (e.g., `AddScoped`, `AddTransient`, `AddSingleton`) as appropriate.
- Do not new-up dependencies; use constructor injection.

## Examples

Controller action example:

```
[HttpPost]
public async Task<IActionResult> Create(CreateProductRequest req, CancellationToken ct)
{
	var result = await _productService.CreateAsync(req, ct);
	return CreatedAtAction(nameof(GetById), new { id = result.Id }, result);
}
```

Service example responsibilities:
- Validate business invariants
- Call repositories
- Publish domain events (if used)

---

Keep conventions pragmatic; prefer consistency across the codebase.