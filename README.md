# CI и CD проекта api_yamdb

## Проект доступен по адресу:

http://62.84.127.180/admin/

## Описание

CI и CD проекта api_yamdb

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

- Войдите на свой удаленный сервер в облаке

- Установите docker:
```
sudo apt install docker.io
```

- Установите docker-compose
```
https://docs.docker.com/compose/install/
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
