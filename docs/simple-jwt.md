
# JSON Web Token Authentication

A brief description of what this project does and who it's for

## Installation

Install djangorestframework-simplejwt with pipenv

```bash
pipenv install djangorestframework-simplejwt
```

In `settings.py`:

```python
INSTALLED_APPS = [
    "rest_framework_simplejwt",
]

REST_FRAMEWORK = {
    "DEFAULT_AUTHENTICATION_CLASSES": [
        "rest_framework_simplejwt.authentication.JWTAuthentication",
    ],
}
```

In `urls.py`:

```python
from rest_framework_simplejwt.views import (
    TokenObtainPairView,
    TokenRefreshView,
)

urlpatterns = [
    path('token/', TokenObtainPairView.as_view(), name='token_obtain_pair'),
    path('token/refresh/', TokenRefreshView.as_view(), name='token_refresh'),
]

```

## Usage/Examples

To verify that Simple JWT is working, you can use curl to issue a couple of test requests:

```bash
curl \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"username": "davidattenborough", "password": "boatymcboatface"}' \
  http://localhost:8000/api/token/

...
{
  "access":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX3BrIjoxLCJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiY29sZF9zdHVmZiI6IuKYgyIsImV4cCI6MTIzNDU2LCJqdGkiOiJmZDJmOWQ1ZTFhN2M0MmU4OTQ5MzVlMzYyYmNhOGJjYSJ9.NHlztMGER7UADHZJlxNG0WSi22a2KaYSfd1S-AuT7lU",
  "refresh":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX3BrIjoxLCJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImNvbGRfc3R1ZmYiOiLimIMiLCJleHAiOjIzNDU2NywianRpIjoiZGUxMmY0ZTY3MDY4NDI3ODg5ZjE1YWMyNzcwZGEwNTEifQ.aEoAYkSJjoWH1boshQAaTkf8G3yn0kapko6HFRt7Rh4"
}
```

### Option Setting

```python
from datetime import timedelta

JWT_ACCESS_TOKEN_LIFETIME = env("JWT_ACCESS_MINUTE", cast=int, default=5)
JWT_REFRESH_TOKEN_LIFETIME = env("JWT_REFRESH_HOUR", cast=float, default=24)

SIMPLE_JWT = {
    "ACCESS_TOKEN_LIFETIME": timedelta(minutes=JWT_ACCESS_TOKEN_LIFETIME),
    "REFRESH_TOKEN_LIFETIME": timedelta(hours=JWT_REFRESH_TOKEN_LIFETIME),
    "ROTATE_REFRESH_TOKENS": True,  # 若為 True，則重新整理後新的 refresh_token 有更新的有效時間
    "UPDATE_LAST_LOGIN": True,  # 若為 True，auth_user 表中的 last_login 欄位在登錄時會更新
}
```

## Documentation

GitHub: <https://github.com/jazzband/djangorestframework-simplejwt>

PyPI: <https://django-rest-framework-simplejwt.readthedocs.io/en/latest/>
