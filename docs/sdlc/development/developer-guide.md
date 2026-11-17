# Developer Guide

> Maintained by QuorQ AI SDLC. Text between `sdlc:auto` markers is regenerated; anything outside them is yours and is kept.

<!-- sdlc:auto:start status -->
_Up to date._
<!-- sdlc:auto:end status -->

<!-- sdlc:auto:start source -->
Generated from commit `806cefc` · model `claude-sonnet-5`
<!-- sdlc:auto:end source -->

<!-- sdlc:auto:start overview -->
Basic caluculator is a Quorq-generated project containing two independently run applications in one repo: a Vite + React 19 single-page frontend whose screens were approved in design and currently render seeded sample data, and a FastAPI backend that is still a bare scaffold (SQLAlchemy models, Pydantic schemas, and a CORS-enabled app factory) exposing only a `/health` liveness route. The backend defaults to a local SQLite file so it runs with no database server, while `docker-compose.yml` can stand up a Postgres 16 instance matching the approved stack. The frontend talks to the API through a small fetch wrapper (`src/lib/api.ts`) that is wired but not yet called by any screen.
<!-- sdlc:auto:end overview -->

<!-- sdlc:auto:start prerequisites -->
- Node.js (for npm/Vite 6, React 19, TypeScript 5.6 toolchain)
- Python 3.12 (matches backend/Dockerfile base image)
- pip
- Docker and Docker Compose (optional, for the Postgres 16 service and container build)
<!-- sdlc:auto:end prerequisites -->

<!-- sdlc:auto:start setup -->
1. Clone the repository.
2. Backend: cd backend && pip install -r requirements.txt
3. (Optional) Set DATABASE_URL to point at a real database; otherwise the backend uses a local SQLite file (sqlite:///./app.db) created automatically on startup.
4. (Optional) Set ALLOWED_ORIGINS (comma-separated) to the frontend's origin; defaults to http://localhost:5173 and http://127.0.0.1:5173 for local dev.
5. Start the backend: uvicorn app.main:app --reload
6. In a separate shell, frontend: cd frontend && npm install
7. (Optional) Set VITE_API_BASE_URL to the backend URL (defaults to http://localhost:8000) and VITE_API_SECRET_KEY if the API requires a bearer token.
8. Start the frontend: npm run dev
9. (Optional) To run Postgres instead of SQLite: docker compose up -d db, then set DATABASE_URL accordingly.
<!-- sdlc:auto:end setup -->

<!-- sdlc:auto:start run -->
| Name | Command | Description |
|---|---|---|
| frontend dev | `cd frontend && npm run dev` | Starts the Vite dev server for the React SPA. |
| frontend build | `cd frontend && npm run build` | Bundles the app with Vite (no type-checking). |
| frontend preview | `cd frontend && npm run preview` | Serves the production build locally. |
| backend dev | `cd backend && uvicorn app.main:app --reload` | Runs the FastAPI app with auto-reload; creates SQLite tables on startup. |
| db up | `docker compose up -d db` | Starts the Postgres 16 container defined in docker-compose.yml. |
<!-- sdlc:auto:end run -->

<!-- sdlc:auto:start structure -->
| Path | Purpose |
|---|---|
| `backend` | FastAPI service: app/main.py (entrypoint, CORS, /health), app/database.py (engine/session), app/models.py (SQLAlchemy models, currently empty), app/schemas.py (Pydantic schemas incl. StubResponse), app/routers/ (per-component routers, currently empty), tests/. |
| `backend/app` | Application package: main.py, database.py, models.py, schemas.py, routers/. |
| `backend/tests` | pytest suite split into unit/ and integration/ (includes test_health.py). |
| `frontend` | Vite + React SPA: src/, e2e/, config files (vite, tsconfig, eslint, prettier, playwright). |
| `frontend/src` | App source: main.tsx entrypoint, lib/ (api.ts fetch client, ui.tsx, icons.tsx, navigate.ts), index.css, test-setup.ts. |
| `frontend/e2e` | Playwright end-to-end specs and support helpers (admin.ts). |
| `.devcontainer` | Dev container configuration (devcontainer.json). |
| `.quorq` | Platform metadata (handoff.json) produced by the Quorq SDLC tooling. |
<!-- sdlc:auto:end structure -->

<!-- sdlc:auto:start conventions -->
- Backend routes are generated as stubs returning a typed StubResponse until a handler is implemented, keeping the service startable and OpenAPI-complete.
- One FastAPI router per architecture component that owns endpoints (backend/app/routers/).
- SQLAlchemy models all inherit from the shared Base in app/database.py; tables are created via Base.metadata.create_all in the app lifespan, not migrations.
- Backend configuration (DATABASE_URL, ALLOWED_ORIGINS) is read from environment variables with safe local defaults (SQLite, localhost origins).
- Frontend screens live under src/screens/ and are written against the shared UI/icon vocabulary in src/lib/ui.tsx and src/lib/icons.tsx; screens currently render seeded sample data rather than calling the API.
- All backend calls from the frontend should go through the single apiFetch helper in src/lib/api.ts, which attaches a bearer token (session token first, else the shared API secret).
- Vitest component tests live beside the components they test under src/; Playwright e2e specs live separately under e2e/.
<!-- sdlc:auto:end conventions -->

<!-- sdlc:auto:start testing -->
| Name | Command | Description |
|---|---|---|
| backend tests | `cd backend && pytest` | Runs the pytest suite (tests/unit, tests/integration) with pythonpath set to the backend root. |
| backend lint | `cd backend && ruff check .` | Lints the backend code with Ruff. |
| backend format | `cd backend && ruff format .` | Formats backend code with Ruff. |
| frontend unit tests | `cd frontend && npm test` | Runs Vitest component tests (jsdom, with v8 coverage). |
| frontend lint | `cd frontend && npm run lint` | Runs ESLint over the frontend; used as a gate during development. |
| frontend typecheck | `cd frontend && npm run typecheck` | Runs tsc --noEmit; not run by npm run build. |
| frontend e2e install | `cd frontend && npm run test:e2e:install` | Installs the Chromium browser Playwright needs. |
| frontend e2e | `cd frontend && npm run test:e2e` | Runs Playwright acceptance tests; without E2E_BASE_URL it boots the backend (from backend/.venv) and builds/serves the frontend itself. |
<!-- sdlc:auto:end testing -->

<!-- sdlc:auto:start troubleshooting -->
| Problem | Solution |
|---|---|
| Frontend requests to the backend are blocked by the browser (CORS error). | Set ALLOWED_ORIGINS on the backend to the frontend's exact origin, or rely on the dev defaults (http://localhost:5173 / http://127.0.0.1:5173) when running both with npm run dev / uvicorn --reload. |
| Backend fails to install psycopg or cannot connect to Postgres. | For local development you don't need Postgres: leave DATABASE_URL unset to use the default SQLite file, or run docker compose up -d db and point DATABASE_URL at it. |
| pytest run from backend/ fails with 'ModuleNotFoundError: app'. | Run pytest from the backend/ directory so pytest.ini's pythonpath = . is honored, or run it as a module (python -m pytest) from that directory. |
| npm run test:e2e fails to start the backend. | Playwright's webServer config expects a Python virtualenv at backend/.venv with dependencies installed; create it (python -m venv .venv && .venv/bin/pip install -r requirements.txt) before running the e2e suite, or set E2E_BASE_URL to test against an already-deployed app. |
| Stale or corrupted local data during backend development. | Delete the SQLite file (backend/app.db) and restart uvicorn; the schema is recreated from app/models.py on startup. |
| Frontend build succeeds but the app is broken (type errors not caught). | npm run build does not typecheck; run npm run typecheck separately and fix tsc errors before relying on a production build. |
<!-- sdlc:auto:end troubleshooting -->
