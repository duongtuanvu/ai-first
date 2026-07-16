# Frontend Conventions

## Technology

React

TypeScript

Vite

## Folder Structure

pages/

components/

hooks/

services/

types/

utils/

## Naming

Component

ProductTable.tsx

Hook

useProducts.ts

Service

productService.ts

Type

Product.ts

## Components

Components should be small.

Extract reusable UI.

Avoid duplicated JSX.

## Hooks

Business logic belongs in hooks.

Components should remain presentational when possible.

## API

Never call fetch directly inside components.

Always use service layer.

## State

Prefer React Query for server state.

Use local state only for UI.

## Forms

Use React Hook Form.

Validation via Zod or Yup.

## Styling

Prefer Tailwind.

Avoid inline styles unless necessary.