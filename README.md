# Application Programming Interface для проекта Yatube
#### В этом проекте реализована API (Application Programming Interface) с помощью DRF(Django Rest Framework). 
Вы можете оставлять, редакрировать и удалять свои посты. Подписываться на других авторов. Оставлять комментарии.

### Как запустить проект:
##### Клонировать репозиторий и перейти в него в командной строке:
```
git clone git@github.com:Hello09Andrey/api_final_yatube.git
```
```
cd api_final_yatube
```
##### Cоздать и активировать виртуальное окружение(Windows):
```
python -m venv venv
```
```
source venv/Scripts/activate
```
##### Установить зависимости из файла requirements.txt:
```
pip install -r requirements.txt
```
##### Выполнить миграции:
```
python manage.py migrate
```
##### Запустить проект:
```
python manage.py runserver
```

### Примеры запросов к API:

##### Для получения списков постов (GET):
```
http://127.0.0.1:8000/api/v1/posts/
```
##### Ответ:
```
[
    {
        "id": 1,
        "author": "Ktoto",
        "text": "PUT от авторизованного пользователя",
        "pub_date": "2022-11-06T06:18:14.995711Z",
        "image": null,
        "group": null
    },
    {
        "id": 2,
        "author": "User_2",
        "text": "Пост от второго автора",
        "pub_date": "2022-11-06T06:46:04.570039Z",
        "image": null,
        "group": null
    }
]
```
##### Для получения определенного поста (GET):
```
http://127.0.0.1:8000/api/v1/posts/{post_id}/
```
##### Ответ:
```
{
    "id": 1,
    "author": "Ktoto",
    "text": "PUT от авторизованного пользователя",
    "pub_date": "2022-11-06T06:18:14.995711Z",
    "image": null,
    "group": null
}
```
##### Для создания поста (POST):
```
http://127.0.0.1:8000/api/v1/posts/
```
Поля id, author, pub_date заполняются автоматически. image и group можно заполнить, а можно оставить пустыми(на ваш выбор).
```
{
    "text": "текст"
}
```
##### Получение комментариев к посту (GET):
```
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/
```
```
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/
```
```
[
    {
        "id": 1,
        "author": "User_2",
        "text": "Коммент от другого автора",
        "created": "2022-11-06T06:49:17.640389Z",
        "post": 1
    },
    {
        "id": 2,
        "author": "User_2",
        "text": "Коммент от другого автора2",
        "created": "2022-12-06T06:49:17.640389Z",
        "post": 1
    }
]
```
######Разрешены методы GET, POST, PUT, PATCH, DELETE

##### Группы (GET):
```
http://127.0.0.1:8000/api/v1/groups
```
```
http://127.0.0.1:8000/api/v1/groups/{group_id}
```
```
[
    {
        "id": 1,
        "title": "Первая группа",
        "slug": "first",
        "description": "Это только начало"
    },
    {
        "id": 2,
        "title": "Вторая группа",
        "slug": "second",
        "description": "Это только начало"
    }
]
```
######Разрешены методы GET



##### Подписки (GET, POST):
```
http://127.0.0.1:8000/api/v1/follow/
```