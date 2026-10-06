# Yatube API

REST API for a social networking platform built with Django REST Framework.

The API allows users to publish posts, leave comments, join communities, and follow other users.

## Features

- JWT authentication
- Creating, editing, and deleting posts
- Adding images to posts
- Comments on posts
- Communities
- Following other users
- Search through subscriptions
- Author-only editing and deletion
- Pagination
- API documentation with ReDoc
- Automated API tests

## Tech Stack

- Python
- Django
- Django REST Framework
- Simple JWT
- Djoser
- SQLite
- pytest
- Postman

## API Features

### Posts

Authenticated users can create posts.

Posts can be read by other users, but only the author can edit or delete their own content.

### Comments

Comments are nested under posts:

```text
/api/v1/posts/{post_id}/comments/
```

Only the comment author can modify or delete a comment.

### Communities

Communities are available through read-only API endpoints.

### Following

Authenticated users can follow other users and search through their subscriptions.

The API prevents:

- following yourself;
- creating duplicate subscriptions.

A database constraint also guarantees that each subscription pair is unique.

## Permissions

The project uses a custom `IsAuthorOrReadOnly` permission.

Safe HTTP methods are available for reading content, while modifying an object requires authentication and ownership of that object.

## Installation

Clone the repository:

```bash
git clone https://github.com/P-Kulakova/api-final-yatube.git
cd api-final-yatube
```

Create and activate a virtual environment:

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Go to the Django project directory:

```bash
cd yatube_api
```

Apply migrations:

```bash
python manage.py migrate
```

Run the development server:

```bash
python manage.py runserver
```

The API will be available at:

```text
http://127.0.0.1:8000/api/v1/
```

## API Documentation

After starting the server, ReDoc documentation is available at:

```text
http://127.0.0.1:8000/redoc/
```

The repository also includes a Postman collection for testing the API.

## Testing

Run the automated test suite from the repository root:

```bash
pytest
```

## Main Endpoints

```text
/api/v1/posts/
/api/v1/posts/{post_id}/comments/
/api/v1/groups/
/api/v1/follow/
/api/v1/jwt/create/
/api/v1/jwt/refresh/
/api/v1/jwt/verify/
```

## Author

**Polina Kulakova**

Python Backend Developer

GitHub: [P-Kulakova](https://github.com/P-Kulakova)
