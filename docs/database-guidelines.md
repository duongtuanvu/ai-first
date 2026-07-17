# Database Guidelines

## Purpose

Database guidelines for schema design, migrations, performance, and operations.

## Schema Design

- Model aggregates around business boundaries.
- Normalize to avoid duplication, denormalize selectively for read performance.
- Use meaningful, singular table names (e.g., `Product`, `Order`).

## Naming Conventions

- Tables: PascalCase or snake_case consistently across the project.
- Columns: use clear names like `CreatedAt`, `UpdatedAt`, `IsDeleted`.
- Primary keys: use `Id` (GUID or bigint) consistently.

## Migrations

- Manage schema changes via EF Core migrations.
- Keep migrations small and focused.
- Review generated SQL for heavy operations (index creation, large updates).

## Indexing

- Add indexes for frequently filtered or sorted columns.
- Use composite indexes when multiple columns are commonly queried together.
- Monitor index usage and avoid over-indexing.

## Queries & Performance

- Prefer parameterized queries and async DB calls.
- Use `AsNoTracking()` for read-only queries.
- Avoid N+1 problems; use `Include` or explicit joins when needed.
- Consider read replicas or caching for heavy read workloads.

## Transactions

- Keep transactions short and focused.
- Use explicit transactions for multi-repository operations that must be atomic.

## Seeding & Test Data

- Provide deterministic seed data for local/dev environments.
- Use separate scripts or migrations for seed data.

## Backups & Migrations Policy

- Ensure regular backups for production databases.
- Test restore procedures periodically.

## Security

- Least-privilege for DB users.
- Encrypt sensitive columns as required.

---

Reference database examples in repository or infra docs when available.
