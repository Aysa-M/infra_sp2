# Групповой проект. Спринт 10. Яндекс.Практикум.
## Описание проекта API для YaMDB.
* API для проекта YaMDB - проекта соц.сети, в котором пользователи могут размещать обзоры на произведения в разных категориях (фильмы, музыка, кино) и жанрах, после чего на основании оценок формируется рейтинг произведений. 
* API проекта позволяет: 
- регистрироваться пользователям;
- управлять списком категорий, жанров, произведений;
- получать, размещать изменять и удалять отзывы, комментарии к ним;
- а еще у нас есть рейтинг произведений и неплохая админка!
* Скоро релиз!
* Примечание. Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

# Технологии (основные инструменты):
- Python==3.7
- Django==2.2.16
- djangorestframework==3.12.4
- djangorestframework-simplejwt==5.1.0
- gunicorn==20.0.4
- psycopg2-binary==2.8.6 (в идеале psycopg2)
- PyJWT==2.1.0
- pytest==6.2.4
- python-dotenv==0.20.0
- Docker

## Деплой в Dev режиме:
- Клонируйте репозиторий:
```$ git clone https://github.com/Aysa-M/api_yamdb.git```
 
- Создайте виртуальное окружение (venv) - должен быть флажок в начале строки:
```$ python -m venv venv```
 
- Установите зависимости:
```$ pip install -r requirements.txt```

- Создайте и примените миграции:
```$ python manage.py makemigrations``` и ```$ python manage.py migrate```

- Запустите django сервер:
```$ python manage.py runserver```

## Деплой проекта с помощью Docker:
- Необходимо установить Docker для дальнейшего развертывания проекта.

- Клонируйте репозиторий:
```$ git clone https://github.com/Aysa-M/infra_sp2.git```

- Перейдите в директорию приложения /api_yamdb и запустите сборку образа проекта
```$ docker build -t infra_sp2 ./yamdb```

- Перейдите в директорию инфраструктуры /infra и запустите контейнеры (3 контейнера:
postgre, web, nginx):
```$ docker-compose up```

- Создайте и примените миграции внутри основного контейнера - web:
```$ docker-compose exec web python manage.py makemigrations``` и
```$ docker-compose exec web python manage.py migrate```

- Соберите статику для корректного отображения сайта http://localhost/admin/
```$ docker-compose exec web python manage.py collectstatic --no-input```

Успех! Теперь вы можете использовать код! Надеемся, что вы будете использовать
его только во благо и желаем вам удачи в начинаниях!

## Документация к API:
После запуска проекта 
по адресу `http://localhost/redoc/` доступна документация для API **YaMDB**.

#### Авторы:
Kuzin Anatoliy, Zhirkov Pavel, Matsakova Aysa