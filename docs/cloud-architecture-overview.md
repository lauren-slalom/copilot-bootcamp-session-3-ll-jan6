# Cloud Architecture Overview

This document provides a simple system context diagram for the TODO App monorepo, showing the React frontend, Express API, and in-memory data store.

```mermaid
flowchart LR
  user[User Browser]
  fe[React Frontend (React + MUI)]
  api[Express API Server]
  db[(In-Memory SQLite)]

  user --> fe
  fe -- HTTP/JSON --> api
  api -- SQL Queries --> db
```

Notes
- Frontend communicates with the API via HTTP JSON requests.
- The API uses an in-memory SQLite database (ephemeral per process) for data persistence during runtime.
- In development, the frontend proxy to the backend is configured (see frontend package.json `proxy`).

## Sequence: Create a TODO

```mermaid
sequenceDiagram
  participant U as User
  participant FE as React Frontend
  participant API as Express API
  participant DB as In-Memory SQLite

  U->>FE: Open app and fill TaskForm
  FE->>API: POST /api/tasks { title, description, due_date }
  API->>API: Validate title; normalize optional due_date
  API->>DB: INSERT INTO tasks (...)
  DB-->>API: New task row (id, timestamps)
  API-->>FE: 201 Created { task }
  FE->>FE: Update list; reset form
```
