# AI-Assisted System Design Workshop - Design File

## Overview

This repository will serve as the foundation for a **workshop system** that guides users through designing their own software systems using AI-assisted discovery.  
The system leverages:

- Fastify + tRPC backend  
- Prisma + Postgres database  
- React frontend  
- AI assistant (Claude or similar) for:
  - Discovery and exploration of design choices
  - Ambiguity probing
  - Advisor mode for trade-offs and decision support
- Output: Markdown design files for schema, endpoints, components, and notes

---

## Core Concepts

### 1. Discovery Mode
- Users provide a **domain/problem statement**.
- AI generates:
  - Initial models/entities
  - Feature suggestions
  - CRUD endpoints
- AI also surfaces **ambiguities/questions** the user may not know to ask.

### 2. Advisor Mode
- Triggered when user encounters an unresolved question.
- AI provides **options, trade-offs, or explanations**.
- User selects a path or refines requirements.
- Decisions are **merged back into the main design state**.

### 3. Main Session State
- Central JSON object tracking:
  - Models & fields
  - Endpoints
  - Frontend components
  - Unresolved questions
  - Assumptions and decisions

### 4. Output
- Once all ambiguities are resolved, AI generates **Markdown design files**:
  - `schema.md` – database models
  - `endpoints.md` – tRPC/REST endpoints
  - `components.md` – frontend components
  - `notes.md` – assumptions, design decisions, trade-offs
  - Optional diagrams (Mermaid)

---

## Example Session (Task Manager App)

### Discovery Phase
- User: "I want to build a task manager app with projects, tasks, and users."
- AI suggests:
  - User, Project, Task entities
  - Initial endpoints
  - Questions about priorities, deletion behavior, roles, versioning

### Advisor Mode Examples
- **Task Priority:** Enum ['low','medium','high']
- **Project Deletion:** Soft-delete projects, keep tasks
- **User Roles:** Owner/Admin only
- **Task History:** createdAt / updatedAt only

### Final Main Session State

```json
{
  "models": {
    "User": ["id","email","password","createdAt"],
    "Project": ["id","name","ownerId","createdAt","deletedAt"],
    "Task": ["id","title","description","dueDate","completed","projectId","assignedUserId","priority","createdAt","updatedAt"]
  },
  "endpoints": [
    "User: register, login, me",
    "Project: list, create, update, delete (soft-delete)",
    "Task: list, create, update, delete"
  ],
  "components": [
    "LoginForm",
    "RegisterForm",
    "ProjectList",
    "ProjectDetail",
    "TaskList",
    "TaskForm"
  ],
  "assumptions": [
    "Task priority as enum",
    "Soft-delete projects",
    "Owner/admin roles only",
    "Task history: createdAt/updatedAt only"
  ]
}
