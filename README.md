# CI и CD проекта api_yamdb

## Проект доступен по адресу:

http://62.84.127.180/admin/

## Описание

CI и CD проекта api_yamdb:
```
-автоматический запуск тестов,
-обновление образов на Docker Hub,
-автоматический деплой на боевой сервер при пуше в главную ветку main.
```

## Статус workflow

[![Django-app workflow](https://github.com/TatianaVKim/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/TatianaVKim/yamdb_final/actions/workflows/yamdb_workflow.yml)

## Установка и запуск

- Клонировать репозиторий и перейти в него в командной строке:
```
git clone https://github.com/TatianaVKim/yamdb_final.git
cd yamdb_final
```

- Cоздать и активировать виртуальное окружение:
```
python -m venv env
source env/bin/activate
```

- Установить зависимости из файла requirements.txt:
```
python -m pip install --upgrade pip
pip install -r requirements.txt
```

- Копируйте файл fixtures.json с локального компьютера на сервер:
```
scp fixtures.json <ваш_username>@<IP-адрес_сервера>:<путь-на-сервере>
```

- Войдите на свой удаленный сервер в облаке
```
ssh <<ваш_username>@<IP-адрес_сервера>
```

- Обновите индекс пакетов APT:
```
sudo apt update
```

- Обновите установленные в системе пакеты и установите обновления безопасности:
```
sudo apt upgrade -y
```

- Установите необходимые для работы PostgreSQL пакеты:
```
sudo apt install postgresql postgresql-contrib -y
```

- Установите docker:
```
sudo apt install docker.io
```

- Установите docker-compose
```
https://docs.docker.com/compose/install/
```

- Выполните миграции, создайте суперюзера:
```
sudo docker-compose exec web python manage.py migrate
sudo docker-compose exec web python manage.py createsuperuser
```

- Команды для переноса данных с SQLite на PostgreSQL:
```
python3 manage.py shell
>>> from django.contrib.contenttypes.models import ContentType
>>> ContentType.objects.all().delete()
>>> quit()
python manage.py loaddata fixtures.json
```

- Скопируйте файлы docker-compose.yaml и nginx/default.conf из вашего проекта на сервер в home/<ваш_username>/docker-compose.yaml и home/<ваш_username>/nginx/default.conf соответственно

- Добавьте в Secrets GitHub Actions переменные окружения для работы базы данных

- Для запуска workflow выполните:
```
git push
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

## Автор:

[Татьяна Ким](https://github.com/TatianaVKim)
