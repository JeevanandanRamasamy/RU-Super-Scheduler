# RU Super Scheduler

A course scheduling and degree-planning assistant for Rutgers University (RU). This repository contains a Python backend (Flask) providing APIs for courses, student records, scheduling suggestions, SPN requests and a React + Vite frontend that provides the user interface used by students and admins.

This README describes the project, architecture, local development setup, testing, and useful notes for contributors.

## Repository layout

- `backend/` — Flask API, database schema, services, routes, and tests
- `frontend/` — React + Vite single-page app used by students and admins

## Quick links

- Backend README: `backend/README.md`
- Frontend README: `frontend/README.md`

## Goals

- Help students plan degree progress by analyzing requirements and completed courses
- Suggest schedules and courses for upcoming semesters
- Provide administrative utilities such as SPN (Special Permission Number) management and course uploads

## Architecture overview

- Backend: Python 3 (Flask). The backend exposes REST endpoints under `routes/` and internal services in `services/`. Data models live in `models/`. Tests use `pytest` and are split into `unit` and `integration`.
- Frontend: React + Vite. UI components are under `src/components` and pages under `src/pages`. The frontend consumes the backend REST API.
- Database: Schema defined in `backend/schema.sql` and seeded data in `backend/data.sql`. A small local SQLite or Postgres instance may be used depending on environment (see backend README).

## Running locally (overview)

1. Set up and run the backend (see `backend/README.md`).
2. Set up and run the frontend (see `frontend/README.md`).
3. Open the frontend in your browser (default Vite port is 5173) and test flows.

## Development notes

- Environment variables: backend expects JWT and DB configuration (see `backend/README.md`).
- Tests: Backend tests are in `backend/tests/` and can be run with `pytest`.
- Seed data and scripts: `backend/scripts/` contains helpers to add sample courses, students, and generate prerequisites.

## Contributing

1. Fork the repository and create a topic branch.
2. Run tests and make sure new code includes tests for new behavior when appropriate.
3. Open a PR with a clear description and test results.

Suggested improvements:
- Add Dockerfiles and docker-compose for one-command local development
- Add CI workflow to run backend tests and frontend lint/build
- Provide an `.env.example` for both backend and frontend

---

See `backend/README.md` and `frontend/README.md` for per-subsystem setup and developer commands.
