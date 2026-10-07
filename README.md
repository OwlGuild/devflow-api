# devflow-api

REST API for **DevFlow**, the open-source team task-management product. Part of
[OwlGuild](https://github.com/OwlGuild).

[![CI](https://github.com/OwlGuild/devflow-api/actions/workflows/ci.yml/badge.svg)](https://github.com/OwlGuild/devflow-api/actions/workflows/ci.yml)
[![Python](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/)
[![Django](https://img.shields.io/badge/django-5.0-092E20.svg)](https://www.djangoproject.com/)
[![DRF](https://img.shields.io/badge/DRF-3.18-brightgreen.svg)](https://www.django-rest-framework.org/)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)

## Why this exists

Task tools fail on two fronts: they are slow to respond, or they are a black box about what
your team is doing. This API keeps the data model small enough to reason about and the
endpoints boring on purpose, so the hard part stays the product logic rather than the plumbing.

## Quickstart

```bash
git clone https://github.com/OwlGuild/devflow-api.git
cd devflow-api
cp .env.example .env
docker compose -f docker-compose.dev.yml up --build
```

Local health check:

```bash
curl http://localhost:8000/health/
# {"status": "ok", "service": "devflow-api"}
```

## API

| Method | Path | Description |
|---|---|---|
| `GET` | `/health/` | liveness probe used by CI and uptime checks |

Endpoints are added behind the same contract: JSON in, JSON out, explicit status codes, and
a test for every behaviour change.

## Stack

| Layer | Choice |
|---|---|
| Runtime | Python 3.12 |
| Framework | Django 5 + Django REST Framework |
| Database | PostgreSQL 16 |
| Queue | Celery + Redis |
| Server | Gunicorn behind Nginx |
| Container | Docker + docker-compose |

## Testing

```bash
pip install -r requirements.txt
pytest -q
```

The suite covers contract behaviour (status codes, response shape, routing) rather than
implementation details, so refactors do not fail the build while a broken API would.

## Ownership

Both maintainers of [OwlGuild](https://github.com/OwlGuild) commit here.

| Area | Maintainer |
|---|---|
| Domain models, endpoints, migrations | [@MarziehAkrami](https://github.com/MarziehAkrami) |
| Client integration | [@AhmadGolbooee](https://github.com/AhmadGolbooee) |
| CI, Docker, docs | shared |

## License

[MIT](LICENSE).