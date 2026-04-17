# Smart Home Sensor API (Monolith)

Учебный backend-проект на Go: REST API для управления датчиками умного дома с хранением данных в PostgreSQL и интеграцией с внешним Temperature API.

## Что реализовано

- CRUD для датчиков (`/api/v1/sensors`).
- Healthcheck (`/health`).
- Получение и обновление температурных данных через отдельный сервис.
- Слоистая структура: `handlers` -> `services` -> `db` -> `models`.

## Технологии

- Go
- Gin
- PostgreSQL
- Docker / Docker Compose
- Postman (коллекция для проверки API)

## Структура репозитория

- `apps/smart_home` - основное Go-приложение.
- `apps/smarthome-api.postman_collection.json` - коллекция запросов.
- `apps/docker-compose.yml` - локальный запуск окружения.
- `apps/init.sh` - helper-скрипт старта.

## Быстрый старт

```bash
cd apps
docker-compose up -d
```

После запуска API доступен на `http://localhost:8080`.

## Основные эндпоинты

- `GET /health`
- `GET /api/v1/sensors`
- `GET /api/v1/sensors/:id`
- `POST /api/v1/sensors`
- `PUT /api/v1/sensors/:id`
- `DELETE /api/v1/sensors/:id`
- `PATCH /api/v1/sensors/:id/value`

## Что можно улучшить

- Закончить конфигурацию `temperature-api` и `postgres` в `apps/docker-compose.yml`.
- Добавить unit/integration тесты.
- Добавить OpenAPI-спецификацию.
- Вынести конфигурацию в `.env` и добавить централизованное логирование.
