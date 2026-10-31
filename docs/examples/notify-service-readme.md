# README сервиса notify-service

## Назначение

Сервис notify-service отправляет пользователям уведомления по электронной почте и в Telegram. Другие сервисы передают ему события через REST API.

## Требования

- Go 1.22 или новее.
- PostgreSQL 15 или новее.
- Docker 24 или новее — для локального запуска базы данных.

## Быстрый старт

```bash
git clone https://github.com/<организация>/notify-service.git
cd notify-service
cp .env.example .env
go run ./cmd/notify-service
```

Где `<организация>` — имя организации на GitHub, в которой лежит репозиторий.

Подробная инструкция — в документе [«Как запустить notify-service локально»](notify-service-local-run.md).

## Конфигурация

| Переменная | Описание | Обязательная | По умолчанию |
| --- | --- | --- | --- |
| `DATABASE_URL` | Строка подключения к PostgreSQL | Да | — |
| `SMTP_HOST` | Адрес SMTP-сервера для отправки писем | Да | — |
| `TELEGRAM_TOKEN` | Токен бота Telegram | Нет | — |
| `HTTP_PORT` | Порт, на котором сервис принимает запросы | Нет | `8080` |
| `LOG_LEVEL` | Уровень логирования: `debug`, `info`, `warn`, `error` | Нет | `info` |

## Проверка результата

Отправьте запрос к методу проверки состояния:

```bash
curl http://localhost:8080/health
```

Сервис вернёт ответ:

```text
{"status":"ok"}
```
