# API Yatube

## Описание

API Yatube — это REST API для социальной сети, которая позволяет пользователям:
- Создавать и редактировать посты
- Оставлять комментарии к постам
- Подписываться на других пользователей
- Добавлять посты в сообщества

Проект построен на базе Django REST Framework и использует JWT-аутентификацию для защиты запросов. API предоставляет полный набор операций CRUD для работы с постами, комментариями, группами и подписками.

## Установка

### Требования
- Python 3.8+
- pip
- virtualenv (рекомендуется)

### Шаги установки

1. **Клонируйте репозиторий:**
   ```bash
   git clone https://github.com/P-Kulakova/api-final-yatube.git
   cd api-final-yatube
   ```

2. **Создайте и активируйте виртуальное окружение:**
   ```bash
   python -m venv venv
   
   # На Windows:
   venv\Scripts\activate
   
   # На Mac/Linux:
   source venv/bin/activate
   ```

3. **Установите зависимости:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Выполните миграции базы данных:**
   ```bash
   cd yatube_api
   python manage.py migrate
   ```

5. **Запустите сервер:**
   ```bash
   python manage.py runserver
   ```

Сервер будет доступен по адресу `http://127.0.0.1:8000/`

## Примеры запросов к API

### Аутентификация

Получение JWT токена:
```http
POST /api/v1/jwt/create/
Content-Type: application/json

{
  "username": "your_username",
  "password": "your_password"
}
```

Ответ:
```json
{
  "refresh": "eyJ0eXAiOiJKV1QiLCJhbGc...",
  "access": "eyJ0eXAiOiJKV1QiLCJhbGc..."
}
```

### Работа с постами

**Получить список всех постов:**
```http
GET /api/v1/posts/
Authorization: Bearer {access_token}
```

**Создать новый пост:**
```http
POST /api/v1/posts/
Authorization: Bearer {access_token}
Content-Type: application/json

{
  "text": "Мой первый пост!",
  "group": 1
}
```

### Работа с комментариями

**Получить комментарии к посту:**
```http
GET /api/v1/posts/{post_id}/comments/
Authorization: Bearer {access_token}
```

**Добавить комментарий к посту:**
```http
POST /api/v1/posts/{post_id}/comments/
Authorization: Bearer {access_token}
Content-Type: application/json

{
  "text": "Отличный пост!"
}
```

### Работа с сообществами

**Получить список сообществ:**
```http
GET /api/v1/groups/
Authorization: Bearer {access_token}
```

**Получить конкретное сообщество:**
```http
GET /api/v1/groups/{id}/
Authorization: Bearer {access_token}
```

### Работа с подписками

**Получить список подписок:**
```http
GET /api/v1/follow/
Authorization: Bearer {access_token}
```

**Подписаться на пользователя:**
```http
POST /api/v1/follow/
Authorization: Bearer {access_token}
Content-Type: application/json

{
  "following": "username"
}
```

После запуска сервера документация API доступна по адресам:
- **ReDoc:** `http://127.0.0.1:8000/redoc/`

## Автор

Polina Kulakova

Учебный проект для изучения Django REST Framework.


