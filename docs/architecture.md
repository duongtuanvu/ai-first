# Project Architecture

## Technology

Backend

- .NET 6
- ASP.NET Core Web API
- Entity Framework Core

Frontend

- React
- TypeScript
- Vite

Database

- SQL Server

---

# Backend Layers

Presentation

Controllers

↓

Application

Services

↓

Domain

Entities

Interfaces

↓

Infrastructure

Repositories

EF Core

↓

Database

---

# Frontend Layers

Pages

↓

Components

↓

Hooks

↓

Services

↓

API

---

# Dependency Rules

Backend

Controller

↓

Service

↓

Repository

↓

DbContext

Frontend

Page

↓

Component

↓

Hook

↓

API

Do not skip layers.

Controllers should not access DbContext directly.

React components should not call fetch directly.