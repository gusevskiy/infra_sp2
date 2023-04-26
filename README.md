### REST API для сервиса YaMDb — базы отзывов о фильмах, книгах и музыке. (Коллективный проект 3х студентов Яндекс.Практикум)

## Технологический стек
[![Python](https://img.shields.io/badge/Python-3.9-blue)](https://www.python.org/)
[![Python](https://img.shields.io/badge/Django-3.2-green)](https://www.djangoproject.com/)
[![Django REST Framework](https://img.shields.io/badge/DRF-3.12.4-red)](https://www.django-rest-framework.org/)

[![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-464646?style=flat&logo=PostgreSQL&logoColor=56C0C0&color=008080)](https://www.postgresql.org/)
[![JWT](https://img.shields.io/badge/-JWT-464646?style=flat&color=008080)](https://jwt.io/)
[![Nginx](https://img.shields.io/badge/-NGINX-464646?style=flat&logo=NGINX&logoColor=56C0C0&color=008080)](https://nginx.org/ru/)
[![gunicorn](https://img.shields.io/badge/-gunicorn-464646?style=flat&logo=gunicorn&logoColor=56C0C0&color=008080)](https://gunicorn.org/)
[![Docker](https://img.shields.io/badge/-Docker-464646?style=flat&logo=Docker&logoColor=56C0C0&color=008080)](https://www.docker.com/)
[![Docker-compose](https://img.shields.io/badge/-Docker%20compose-464646?style=flat&logo=Docker&logoColor=56C0C0&color=008080)](https://www.docker.com/)
[![Docker Hub](https://img.shields.io/badge/-Docker%20Hub-464646?style=flat&logo=Docker&logoColor=56C0C0&color=008080)](https://www.docker.com/products/docker-hub)
[![GitHub%20Actions](https://img.shields.io/badge/-GitHub%20Actions-464646?style=flat&logo=GitHub%20actions&logoColor=56C0C0&color=008080)](https://github.com/features/actions)
[![Yandex.Cloud](https://img.shields.io/badge/-Yandex.Cloud-464646?style=flat&logo=Yandex.Cloud&logoColor=56C0C0&color=008080)](https://cloud.yandex.ru/)


## Как развернуть проект в Docker container локально:

Клонируйте репозиторий в нужную вам папку:
```
https://github.com/gusevskiy/infra_sp2.git
```
Создайте файл .env в директории `infra` добавьте в него переменные окружения для работы с базой данных:
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```

Соберите контейнеры:
```
docker-compose up -d --build
```
Выполните команды по очереди:
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input 
```
Можно заполнить БД тестовыми данными:
```bash
python3 manage.py load_csv_data
python manage.py loaddata infra/fixtures.json
```


## Ссылки
### Документация к проектуAPI YaMDb - будет доступна на эндпойнт:
```json
localhost/redoc/
```

### [Описание функционала приложения](https://github.com/gusevskiy/api_yamdb)
