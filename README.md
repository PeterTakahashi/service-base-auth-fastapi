# Service Base FastAPI

## Frontend Repository
https://github.com/PeterTakahashi/service-base-auth-react-vite

## Key Dependencies

This project uses several well-known Python libraries to build a scalable and secure authentication service:

- **FastAPI** (>=0.115.12): A modern, high-performance web framework for building APIs with Python 3.7+ based on standard Python type hints.
- **SQLAlchemy** (>=2.0.40): The SQL toolkit and ORM used for database access and schema management.
- Alembic (>=1.15.2): A lightweight database migration tool for use with SQLAlchemy.
- **FastAPI Users** (>=14.0.1): Extensible user management for FastAPI, including authentication and OAuth support.
- **Uvicorn (>=0.34.2)**: A lightning-fast ASGI server used to run FastAPI in production.
- **Pydantic (>=2.11.3)**: Used for data validation and settings management with type annotations.
- **Pytest (==7.2.2)**: A mature testing framework used with additional plugins for testing asynchronous code.

## Installation

### Local setup

#### Docker

```bash
docker exec -it service-base-web bash
source .venv/bin/activate

pytest --cov=app --cov-report=term-missing --cov-report=html
open htmlcov/index.html # if you wanna see cov report

open http://localhost:1080 # open mail log
open http://127.0.0.1:8000/app/v1/docs # open api docs

```

#### create db migration file

```bash
alembic revision --autogenerate -m ""
```

#### db migrate

```bash
alembic upgrade head
```

#### reset table

```bash
docker compose down -v
```

#### create schema

```bash
python -m scripts.create_schema
```

#### code formatter

```
black .
ruff check . --fix
```

#### code checker

```
ruff check .
mypy --config-file mypy.ini .
```

#### OpenAPI

html
http://0.0.0.0:8000/app/v1/docs#/

json
http://0.0.0.0:8000/app/v1/openapi.json

##### API docs

<img src='docs/img/openapi_1.png' width="600" />
<img src='docs/img/openapi_2.png' width="600" />

<img src='docs/img/redoc_1.png' width="600" />
<img src='docs/img/redoc_2.png' width="600" />
