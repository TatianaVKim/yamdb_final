# yamdb_final

## Описание

YaMDb - отправляем проект в контейнере
[![Actions Status](https://github.com/TatianaVKim/yamdb_final/workflows/Django-app%20workflow/badge.svg)](https://github.com/TatianaVKim/yamdb_final/actions)

## Технологии

- Python 3;
- Django REST Framework;
- SQLlite.

## Установка Запуск приложения в контейнерах

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/TatianaVKim/infra_sp2.git
cd infra_sp2
```

В директории api_yamdb с файлом Dockerfile выполните сборку образа:
```
docker build -t <название_образа>
```

Запустите docker-compose, выполните сборку и запустите контейнеры:
```
docker-compose up
```

Выполните миграции:
```
docker-compose exec web python manage.py migrate
```

Создайте суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```

Соберите статические файлы в один каталог:
```
docker-compose exec web python manage.py collectstatic --no-input
```

## Шаблон наполнения env-файла:

```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```

## Заполнение базы данными

Перейдите в директорию infra_sp2/infra/ с файлом fixtures.json

Скопируйте базу
```
docker cp fixtures.json <ID контейнера>:/app
```

Загрузите базу
```
docker-compose exec web python manage.py loaddata fixtures.json
```

## Перейдите по адресу:

http://localhost/admin/
