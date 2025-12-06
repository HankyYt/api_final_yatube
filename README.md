# Yatube API

REST API для социальной сети Yatube.

## Описание
API позволяет выполнять операции с публикациями, комментариями, группами и подписками. 
Аутентификация реализована с помощью JWT токенов.

## Установка

1. Клонируйте репозиторий:
```bash
git clone <repository-url>
cd api_final_yatube
```

2. Создайте и активируйте виртуальное окружение:
```bash
python -m venv venv
source venv/bin/activate  # для Linux/Mac
venv\Scripts\activate     # для Windows
```

3. Установите зависимости:
```bash
pip install -r requirements.txt
```
4. Примените миграции:
```bash
python manage.py migrate
```
5. Создайте суперпользователя:
```bash
python manage.py createsuperuser
```
6. Запустите сервер:
```bash
python manage.py runserver
```
# Примеры запросов
## Получение JWT токена
```bash
curl -X POST http://127.0.0.1:8000/api/v1/jwt/create/ \
  -H "Content-Type: application/json" \
  -d '{"username": "your_username", "password": "your_password"}'
```
## Создание поста
```bash
curl -X POST http://127.0.0.1:8000/api/v1/posts/ \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"text": "Текст поста", "group": 1}'
```
## Получение списка постов
```bash
curl -X GET http://127.0.0.1:8000/api/v1/posts/ \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```
## Создание подписки
```bash
curl -X POST http://127.0.0.1:8000/api/v1/follow/ \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"following": "username_to_follow"}'
```
## Документация
После запуска сервера документация доступна по адресу:
http://127.0.0.1:8000/redoc/
