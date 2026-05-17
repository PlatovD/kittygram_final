# Kittygram

Контейнеризированное веб-приложение для публикации фотографий котов с достижениями. Автоматическое тестирование и деплой
через GitHub Actions.

## Функции

- Создание карточек котов (имя, год рождения, цвет, фото)
- Добавление достижений
- Аутентификация пользователей (JWT)
- Пагинация списка карточек
- Адаптивный интерфейс

## Технологии

**Backend:** Django, DRF, PostgreSQL, Gunicorn, JWT  
**Frontend:** React, React Router, CSS Modules  
**DevOps:** Docker, Docker Compose, Nginx, GitHub Actions, Docker Hub

## Контейнеры

| Контейнер | Образ                | Назначение |
|-----------|----------------------|------------|
| backend   | `kittygram_backend`  | Django API |
| frontend  | `kittygram_frontend` | React SPA  |
| gateway   | `kittygram_gateway`  | Nginx      |
| db        | `postgres:13`        | PostgreSQL |

**Тома:** `pg_data`, `static`, `media`

## Быстрый запуск

### 1. Клонирование

```bash
git clone https://github.com/ваш_логин/kittygram_final.git
cd kittygram_final
```

### Шаг 2: Настройка переменных окружения
Создайте файл .env в корне проекта:

```bash
cp .env.example .env
```

### 2. Отредактируйте .env файл, указав свои значения:

```bash
# Настройки Postgres
POSTGRES_DB=django
POSTGRES_USER=django_user
POSTGRES_PASSWORD=django_password

# Настройки Django
DB_NAME=django
DB_HOST=db
DB_PORT=5432
SECRET_KEY=qwertqweryqwertqweryqwertqweryqwertqweryqwertqweryqwertqwery
```

### 3. Запуск проекта

```bash
# Сборка и запуск всех контейнеров
docker-compose up -d --build

# Создание суперпользователя (администратора)
docker-compose exec backend python manage.py createsuperuser
```

### 4: Проверка работы

Проект будет доступен по адресу:

- Фронтенд: http://localhost:9000
- API: http://localhost:9000/api/
- Админка Django: http://localhost:9000/admin/