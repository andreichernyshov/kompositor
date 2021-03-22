# образ на основе которого создаём контейнер
FROM python:3.9.2-alpine

# рабочая директория внутри проекта
WORKDIR /usr/src/app

# переменные окружения для python
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Устанавливаем зависимости для Postgres
RUN apk update \
    && apk add postgresql-dev gcc python3-dev musl-dev
# RUN apt-get update
# RUN apt-list --upgradable
# RUN apt-get -y upgrade
# RUN pip install --upgrade postgresql-dev
# RUN pip install --upgrade gcc
# RUN pip install --upgrade python3-dev
# RUN pip install --upgrade musl-dev

# устанавливаем зависимости
RUN pip install --upgrade pip setuptools
COPY requirements.txt .
RUN pip install -r requirements.txt

# копируем содержимое текущей папки в контейнер
COPY . .
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]
