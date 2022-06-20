
# CORS

A Django App that adds Cross-Origin Resource Sharing (CORS) headers to responses. This allows in-browser requests to your Django application from other origins.

## Installation

Install django-cors-headers with pipenv

```bash
pipenv install django-cors-headers
```

In `settings.py`:

```python
INSTALLED_APPS = [
    "corsheaders",
]
```

Make sure you add the trailing comma or you might get a ModuleNotFoundError (see this blog post).

You will also need to add a middleware class to listen in on responses:

In `settings.py`:

```python
MIDDLEWARE = [
    "corsheaders.middleware.CorsMiddleware",
    "django.middleware.common.CommonMiddleware",
]
```

In `settings.py`:

```python
CORS_ALLOWED_ORIGINS = [
    "https://example.com",
    "https://sub.example.com",
    "http://localhost:8080",
    "http://127.0.0.1:9000",
]

# or

CORS_ALLOWED_ORIGINS = env.list('CORS_ALLOWED_ORIGINS', default=[])
```

## Documentation

Django REST framework: <https://www.django-rest-framework.org/topics/ajax-csrf-cors/#cors>

GitHub: <https://github.com/adamchainz/django-cors-headers>

PyPI: <https://pypi.org/project/django-cors-headers/>
