# RU Super Scheduler — Backend

This directory contains the Flask backend that provides REST APIs for course data, student records, requirement checks, planning, SPN requests and more.

Contents
- `app.py` — application entry point
- `db.py` — database helpers
- `routes/` — Flask route handlers (API endpoints)
- `services/` — business logic and services used by routes
- `models/` — data models and domain objects
- `scripts/` — helper scripts for seeding data and administrative actions
- `tests/` — unit and integration tests (pytest)

System requirements
- Python 3.8+ (recommend 3.10 or later)
- pip for installing dependencies

Install dependencies

1. Create a virtual environment and activate it (macOS / zsh):

```bash
python3 -m venv .venv
source .venv/bin/activate
```

2. Install packages:

```bash
pip install -r requirements.txt
```

Configuration
- The backend reads configuration (database connection, JWT secret, etc.) from environment variables. Create a `.env` file or export variables in your shell. Common variables:

- `DATABASE_URL` — SQLAlchemy / DB connection string (e.g., `sqlite:///dev.db` or postgres URL)
- `JWT_SECRET` — secret key used for signing JWT tokens
- `FLASK_ENV` — `development` or `production`

Database
- Schema is in `schema.sql`. To initialize a fresh SQLite database you can run a small script or use `sqlite3` to import `schema.sql` then run `data.sql` to seed data. Example (sqlite):

```bash
sqlite3 dev.db < schema.sql
sqlite3 dev.db < data.sql
```

For Postgres, run the schema and seed SQL against your database, or change `scripts/add_courses.py` / other scripts to use your connection string.

Running the server

With the virtualenv active and environment variables set:

```bash
# from backend/
export FLASK_APP=app.py
export FLASK_ENV=development
flask run --host=127.0.0.1 --port=5000
```

Or run directly with python:

```bash
python app.py
```

API
- Routes are defined in `routes/`. Example endpoints (not exhaustive):

- `POST /login` — user authentication
- `POST /register` — create an account
- `GET /courses` — list courses
- `GET /sections` — list sections for a course/term
- `POST /spn` — submit SPN requests

Running tests

From the `backend/` directory:

```bash
pytest -q
```

Notes and developer tips
- The codebase uses a service-layer pattern: prefer adding logic to `services/` and keep routes thin.
- Seed scripts are in `scripts/`. Use them to populate the DB with sample students or courses.
- If you add new dependencies, update `requirements.txt` (pin versions if possible).

Troubleshooting
- If tests fail due to DB state, remove or re-create the local DB file and re-run schema/data SQL.
- If JWT auth fails, ensure `JWT_SECRET` matches what the frontend uses in development or adjust the auth helper.

Next improvements (suggested)
- Add `docker-compose.yml` to run backend + DB quickly.
- Add `.env.example` containing sample environment variables.
