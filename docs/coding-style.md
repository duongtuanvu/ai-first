# Coding Style

## Purpose

Readable, consistent coding practices for backend and frontend code in this repository.

## General principles

- Prioritize readability and clarity.
- Prefer composition over inheritance.
- Avoid duplicated code; extract common utilities.
- Keep functions and components small and focused.

## Naming

- Use meaningful, descriptive names.
- Prefer full words over abbreviations (e.g., `ProductRepository` not `ProdRepo`).
- Use PascalCase for types/classes and camelCase for variables/functions.

## Comments & Documentation

- Comment only to explain why (not what) when business rules are non-obvious.
- Keep XML/doc comments for public APIs and libraries.

## Error handling & logging

- Throw or return meaningful errors; avoid swallowing exceptions silently.
- Log unexpected errors with sufficient context for debugging.

## Clean code & SOLID

- Apply Single Responsibility Principle; keep classes focused.
- Prefer small methods (<~50 lines) and extract helpers for complex logic.

## Language-specific notes

- C#/.NET: follow Microsoft C# conventions (naming, async suffix for async methods, nullability annotations).
- TypeScript/React: use strict types, prefer `unknown` over `any`, keep component props typed.

## PR & Review

- Keep PRs small and focused.
- Include a short description of changes and testing steps.
- Add unit tests for new logic where applicable.

---

Follow repository-specific rules in `backend-conventions.md` and `frontend-conventions.md` for more detail.