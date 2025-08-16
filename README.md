# Knowledge Hub – Full-Stack Notes App

A full-stack web application for managing personal notes. Users can register, log in, and create, edit, and delete notes securely. Built to explore modern frontend, backend, database, DevOps, and cloud practices in one integrated project.

---

## Goals

- Demonstrate end-to-end engineering: frontend, backend, database, security, testing, DevOps
- Show design artifacts: architecture diagrams, ER models, user stories/boards
- Provide a clean developer experience: one-command local run, clear docs, tests

## Architecture (Phase 1)

Frontend (React/TS) → Backend (Express/TS) → PostgreSQL
All three run in Docker containers via `docker-compose`.

_Additional docs/diagrams live in_ `./docs/`:

- **System diagram**: FE ↔ API ↔ DB
- **ERD**: `users(1)–(n)notes`

## Tech Stack

**Frontend**: React + TypeScript, Vite, (Tailwind or MUI)  
**Backend**: Node.js + Express + TypeScript, JWT Auth, bcrypt  
**Database**: PostgreSQL (SQL migrations)  
**DevOps**: Docker, Docker Compose, GitHub Actions (later)  
**Docs & PM**: Diagrams (Draw.io/Miro/Figma), Jira/Azure DevOps (optional)  
**Testing** (later in Phase 1+): Jest, React Testing Library, Playwright/Cypress

## Getting Started

### Prereqs

- Docker & Docker Compose
- Node.js 20+ (for local dev convenience)

### First run (containers)

```bash
docker-compose up --build
# Frontend: http://localhost:3000
# Backend:  http://localhost:5000/health
# Postgres: localhost:5432 (user: app, pass: app, db: appdb)

### Local dev (optional)
- `apps/backend`: `npm run dev` (nodemon)
- `apps/frontend`: `npm run dev` (Vite)

---

## Project Structure

```

knowledge-hub/
├─ apps/
│ ├─ backend/ # Express + TypeScript API
│ └─ frontend/ # React + TypeScript UI
├─ infra/
│ └─ db/ # migrations/seed scripts
├─ docs/ # diagrams (arch, ERD, ADRs)
├─ ops/
│ ├─ docker/ # alternative Docker assets
│ └─ ci/ # CI scripts
├─ .github/workflows/ # GitHub Actions
├─ docker-compose.yml
├─ .gitignore
├─ README.md
└─ LICENSE

```

---

## Environment

- Backend uses:
  - `DATABASE_URL=postgres://app:app@db:5432/appdb`
  - `JWT_SECRET=change-me-in-prod`
- Create a `.env` file for local dev if needed (never commit secrets).

---

## Testing (later in Phase 1)

- **Backend**: Jest unit + integration (spin up ephemeral Postgres via Docker)
- **Frontend**: React Testing Library for components; Cypress/Playwright for e2e

---

## Roadmap

- [ ] MVP: Auth (register/login), notes CRUD, basic UI
- [ ] Tests: backend unit/integration, frontend component/e2e
- [ ] CI: GitHub Actions build & test on PRs
- [ ] Docs: system diagram, ERD, sequence diagram, ADRs
- [ ] Env: staging/prod config, container hardening
- [ ] Deploy: cloud (Render/Railway/Azure Web Apps), then Kubernetes (AKS/GKE/EKS)
- [ ] Observability: Prometheus/Grafana, logs, dashboards

---

## Contributing

Use trunk-based development with short-lived branches and Conventional Commits:
- `feat(auth): add JWT login`
- `fix(notes): return 403 for non-owner update`
- `chore(ci): add backend test workflow`
```
