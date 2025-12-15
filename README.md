# Base MVP Project

A small starter full‑stack project:

- Backend: FastAPI (Python)
- Frontend: Next.js
- Database: PostgreSQL
- Dev: Docker Compose

## Features
- FastAPI + Pydantic / SQLModel
- JWT auth and secure password hashing
- Playwright E2E tests
- Docker Compose development workflow

## Quick start
Start everything for development:
```bash
docker compose watch
```

Or run in detached mode:
```bash
docker compose up -d --build
```

## Local URLs
- Backend API: http://localhost:8000
- API docs (Swagger UI): http://localhost:8000/docs
- Frontend: http://localhost:3000
- Adminer (DB UI): http://localhost:8080

> If a service is not reachable, check ports and service status (see Troubleshooting).

## Useful commands
- Show services and ports:
  docker compose ps
- Follow logs:
  docker compose logs -f backend
  docker compose logs -f frontend
- Recreate a service (apply compose overrides such as ports):
  docker compose up -d --force-recreate <service>
- Run migrations / prestart scripts:
  docker compose run --rm prestart bash -lc "bash scripts/prestart.sh"

## Troubleshooting
- Port missing after change? Recreate the container:
  docker compose up -d --force-recreate adminer frontend
- Service crashes? Check logs:
  docker compose logs -f <service>
- App reachable inside container but not on host:
  docker compose exec <service> curl -v http://127.0.0.1:<port>/...
  netstat -aon | findstr ":<port>"   # on Windows to find conflicts
- If image build errors due to tag collisions, remove local tag and rebuild:
  docker image rm <imagename>:<tag>
  docker compose up --build -d

## Development notes
- Frontend uses environment vars prefixed with NEXT_PUBLIC_ for browser usage (set in .env or pass build args).
- Backend settings are read from .env (see config.py for required vars).

## Tests
- Backend tests:
  docker compose run --rm backend pytest
- Frontend tests (Playwright):
  npm run test (in frontend or via appropriate docker task)

---

Keep .env values secure for production (change SECRET_KEY, DB passwords, etc.).
```// filepath: d:\private\base-mvp-project\README.md
# Base MVP Project

A small starter full‑stack project:

- Backend: FastAPI (Python)
- Frontend: Next.js
- Database: PostgreSQL
- Dev: Docker Compose

## Features
- FastAPI + Pydantic / SQLModel
- JWT auth and secure password hashing
- Playwright E2E tests
- Docker Compose development workflow

## Quick start
Start everything for development:
```bash
docker compose watch
```

Or run in detached mode:
```bash
docker compose up -d --build
```

## Local URLs
- Backend API: http://localhost:8000
- API docs (Swagger UI): http://localhost:8000/docs
- Frontend: http://localhost:3000
- Adminer (DB UI): http://localhost:8080

> If a service is not reachable, check ports and service status (see Troubleshooting).

## Useful commands
- Show services and ports:
  docker compose ps
- Follow logs:
  docker compose logs -f backend
  docker compose logs -f frontend
- Recreate a service (apply compose overrides such as ports):
  docker compose up -d --force-recreate <service>
- Run migrations / prestart scripts:
  docker compose run --rm prestart bash -lc "bash scripts/prestart.sh"

## Troubleshooting
- Port missing after change? Recreate the container:
  docker compose up -d --force-recreate adminer frontend
- Service crashes? Check logs:
  docker compose logs -f <service>
- App reachable inside container but not on host:
  docker compose exec <service> curl -v http://127.0.0.1:<port>/...
  netstat -aon | findstr ":<port>"   # on Windows to find conflicts
- If image build errors due to tag collisions, remove local tag and rebuild:
  docker image rm <imagename>:<tag>
  docker compose up --build -d

## Development notes
- Frontend uses environment vars prefixed with NEXT_PUBLIC_ for browser usage (set in .env or pass build args).
- Backend settings are read from .env (see config.py for required vars).

## Tests
- Backend tests:
  docker compose run --rm backend pytest
- Frontend tests (Playwright):
  npm run test (in frontend or via appropriate docker task)

---

Keep .env values secure for production (change SECRET_KEY, DB passwords, etc.).