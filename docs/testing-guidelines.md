# Testing Guidelines

## Purpose

Standards and practices for unit, integration, and end-to-end testing in this repository.

## Test Types

- Unit tests: fast, isolated tests of services, utilities, and small components.
- Integration tests: verify interactions between components (e.g., service+repository+DB in-memory).
- End-to-end (E2E): full-stack tests that simulate user flows (frontend + backend).

## Tools

- Backend (.NET): xUnit, NUnit or MSTest; use FluentAssertions for readable assertions.
- Frontend: React Testing Library + Jest for unit/component tests; Playwright or Cypress for E2E.

## Test Structure & Naming

- Place backend tests in a parallel test project `src/ProjectName.Tests`.
- Name tests using the `MethodUnderTest_StateUnderTest_ExpectedBehavior` pattern.

## Mocking & Isolation

- Mock external dependencies for unit tests (e.g., repositories, HTTP clients).
- Use in-memory databases (e.g., SQLite in-memory) for integration tests where possible.

## CI & Coverage

- Run tests in CI pipeline on every PR.
- Set a reasonable coverage threshold and track coverage trends.

## Flaky Tests

- Fix flaky tests promptly; do not silence failures.
- Add diagnostics/logging when tests fail intermittently.

## Test Data

- Keep test data deterministic and small.
- Use builders or factories to create test objects.

## Performance

- Keep unit tests fast (<100ms each where possible).
- Run slower integration or E2E suites on schedules or gated jobs.

## Documentation

- Document how to run tests locally in `README.md` or `docs/`.

---

Follow these guidelines to keep the test suite reliable and fast. Link to CI configuration when available.
