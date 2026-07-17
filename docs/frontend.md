# Frontend Conventions

## Purpose

Frontend coding conventions for React + TypeScript in this repository.

## Technology stack

- React + TypeScript
- Vite for bundling/dev
- React Query for server state
- React Hook Form for forms

## Folder structure

- `pages/` — top-level routes/pages
- `components/` — presentational and composite components
- `hooks/` — reusable hooks with business logic
- `services/` — API interaction layer (fetch/axios wrappers)
- `types/` — shared TypeScript types
- `utils/` — small helpers

Group by feature when the app grows (e.g., `features/products/`).

## Naming

- Components: `ProductTable.tsx`
- Hooks: `useProducts.ts`
- Services: `productService.ts`
- Types: `Product.ts`

Use PascalCase for components and types, camelCase for functions and hooks.

## Components & Hooks

- Keep components small and presentational; move logic to hooks.
- Prefer composition over prop drilling; use context when needed.
- Extract reusable UI components into `components/ui/`.

## API & Data fetching

- Do not call `fetch` directly in components. Use `services` and `react-query` hooks.
- Centralize API base URL and error handling in the service layer.

Example service method:

```
export async function getProducts(params) {
	return apiClient.get('/api/v1/products', { params });
}
```

## State management

- Use React Query for server state and caching.
- Use local component state for UI-only state.

## Forms & Validation

- Use React Hook Form for forms, validate with Zod or Yup.

## Styling

- Prefer Tailwind CSS for utility-first styling.
- Avoid inline styles; extract style logic where necessary.

## Testing

- Use React Testing Library + Jest for unit/component tests.
- Write small, focused tests for hooks and components.

---

Follow these conventions for consistent, maintainable frontend code.