# API Guidelines

## Purpose

This document describes conventions and best practices for designing and implementing HTTP APIs in this repository.

## Versioning

- Use path versioning: `/api/v1/...`.
- Increment major version for breaking changes.

## Authentication & Authorization

- Prefer JWT bearer tokens for service-to-service and user authentication.
- Validate scopes/roles in the service layer, not in controllers.

## HTTP Conventions

- Use standard HTTP methods: GET, POST, PUT, PATCH, DELETE.
- Return appropriate status codes (200/201/204/400/401/403/404/409/500).
- Use `application/json` for request and response bodies.

## Request & Response Shape

- Use DTOs for all external contracts (Requests / Responses).
- Keep responses consistent: wrap errors in a standard error object.

Example success response:

{
	"data": { ... },
	"meta": { /* pagination, etc. */ }
}

Example error response:

{
	"error": {
		"code": "VALIDATION_ERROR",
		"message": "Validation failed",
		"details": [ ... ]
	}
}

## Pagination, Filtering, Sorting

- Use `page`/`pageSize` or cursor-based pagination for large collections.
- Support filtering via query parameters (e.g., `?status=active`).
- Support sorting using a `sort` parameter (e.g., `?sort=-createdAt,name`).

## Validation

- Validate incoming requests using FluentValidation (backend) or schema validation on the client.
- Return `400 Bad Request` with error details for validation failures.

## Error Handling

- Centralize error handling in middleware.
- Map known domain errors to appropriate HTTP status codes.

## Rate Limiting & Throttling

- Apply rate limits at the gateway or API layer as required.

## Documentation & OpenAPI

- Maintain an OpenAPI/Swagger spec for public endpoints.
- Keep the spec up-to-date with code; generate from controllers when possible.

## Testing

- Unit-test controllers, services, and mappers.
- Add contract tests for important endpoints.

---

Keep API contracts small and versioned. Link to examples in code when available.
