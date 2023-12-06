# Проект YaMDB

![Status](https://github.com/SowaSova/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

Проект YaMDb собирает __отзывы (Review)__ пользователей на __произведения (Titles)__. Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список __категорий (Category)__ может быть расширен (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).


### Шаблон наполнения env-файла:
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

### Как запустить проект:
Клонируем репозиторий:
```
git clone https://github.com/SowaSova/yamdb_final.git
cd yamdb_final
cd api_yamdb
```
Переходим в директорию с файлом docker_compose.yaml:
```
cd infra
```
Собираем контейнеры и запускаем их:
```
docker-compose up -d --build 
```
Выполняем миграции:
```
docker-compose exec web python manage.py migrate
```
Создаем суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
Собираем статику:
```
docker-compose exec web python manage.py collectstatic --no-input 
```
Заполняем базу данных:
```
docker-compose exec web python manage.py loaddata fixtures.json
```
