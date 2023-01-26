[![Typing SVG](https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=500&size=30&pause=1000&color=14A6F7&width=435&lines=%D0%9F%D1%80%D0%BE%D0%B5%D0%BA%D1%82+YaMDb-final)](https://git.io/typing-svg)

[![Python](https://img.shields.io/badge/-Python-464641?style=flat-square&logo=Python)](https://www.python.org/)
[![Django](https://img.shields.io/badge/-Django-464646?style=flat-square&logo=Django)](https://www.djangoproject.com/)
[![HTML5](https://img.shields.io/badge/-HTML5-464646?style=flat-square&logo=html5)](https://en.wikipedia.org/wiki/HTML5)
[![CSS](https://img.shields.io/badge/-CSS-464646?style=flat-square&logo=css3)](https://en.wikipedia.org/wiki/CSS)
[![Docker](https://img.shields.io/badge/Docker-464646?style=flat-square&logo=docker)](https://www.docker.com/)
[![Pytest](https://img.shields.io/badge/-Pytest-464646?style=flat-square&logo=pytest)](https://docs.pytest.org/en/6.2.x/)

![example workflow](https://github.com/GrWo1/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Описание

Проект `YaMDb` собирает отзывы пользователей

- В файле docker-compose.yaml описаны инструкции для трёх контейнеров: `web, db, nginx`.
- Настроены volumes для базы данных, статики и медиа (файлов, загружаемых пользователями).
- Директория .github/workflows содержит корректный workflow в файле yamdb_workflow.yaml.
- Проект развёрнут и запущен на боевом ![сервере](http://84.201.161.226/admin).
- При пуше в ветку main код автоматически проверяется, тестируется, деплоится на сервер.
- В файле settings.py для переменных из env-файла указаны валидные значения по умолчанию.

<details>
<summary> <b>Установка</b></summary>
   


1. Проверить наличие Docker

   Прежде чем приступать к работе, убедиться что Docker установлен, для этого ввести команду:

   ```bash
   docker -v
   ```

   В случае отсутствия, скачать [Docker Desktop](https://www.docker.com/products/docker-desktop) 
для Mac или Windows. [Docker Compose](https://docs.docker.com/compose) будет установлен 
автоматически.

   В Linux проверить, что установлена последняя версия 
[Compose](https://docs.docker.com/compose/install/).

   Также можно воспользоваться официальной [инструкцией](https://docs.docker.com/engine/install/).

2. Клонировать репозиторий на локальный компьютер

   ```bash
   git clone https://github.com/egorcoders/infra_sp2.git
   ```

3. В корневой директории создать файл `.env`, согласно примеру:

   ```bash
   DB_ENGINE=django.db.backends.postgresql
   DB_NAME=postgres
   POSTGRES_USER=postgres
   POSTGRES_PASSWORD=postgres
   DB_HOST=db
   DB_PORT=5432
   ```

4. Запустить `docker-compose`

   Выполнить из корневой директории команду:

   ```bash
   docker-compose up -d
   ```

5. Заполнить БД

   Создать и выполнить миграции:

   ```bash
   docker-compose exec web python manage.py makemigrations --noinput
   docker-compose exec web python manage.py migrate --noinput
   ```

6. Подгрузить статику

   ```bash
   docker-compose exec web python manage.py collectstatic --no-input
   ```

7. Заполнить БД тестовыми данными

   Для заполнения базы использовать файл `fixtures.json`, в директории `infra_sp2`. Выполните 
команду:

   ```bash
   docker-compose exec web python manage.py dumpdata > fixtures.json
   ```

8. Создать суперпользователя

   ```bash
   docker-compose exec web python manage.py createsuperuser
   ```

9. Остановить работу всех контейнеров

   ```bash
   docker-compose down
   ```

10. Пересобрать и запустить контейнеры

    ```bash
    docker-compose up -d --build
    ```

11. Мониторинг запущенных контейнеров

    ```bash
    docker stats
    ```

12. Остановить и удалить контейнеры, тома и образы

    ```bash
    docker-compose down -v
    ```
</details>

### :fire: Мой статус :
[![GitHub Streak](http://github-readme-streak-stats.herokuapp.com?user=grwo1&theme=dark&background=000000)](https://git.io/streak-stats)
