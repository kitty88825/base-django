
# Django REST framework Swagger

Generate real Swagger/OpenAPI 2.0 specifications from a Django Rest Framework API.

## Installation

Install drf-yasg with pipenv

```bash
pipenv install drf-yasg
```

## Quickstart

In `settings.py`:

```python
INSTALLED_APPS = [
  ...
  "django.contrib.staticfiles",  # required for serving swagger ui's css/js files
  "drf_yasg",
  ...
]
```

In `urls.py`:

```python
from drf_yasg import openapi
from drf_yasg.views import get_schema_view
from rest_framework import permissions

schema_view = get_schema_view(
    openapi.Info(
        title="Base Django REST framework API",
        default_version="v1",
        description="Simple Django Project",
    ),
    public=True,
    permission_classes=(permissions.IsAuthenticated,),
)

urlpatterns = [
    ...
    path("docs/", schema_view.with_ui("swagger", cache_timeout=0)),
    ...
]
```

## Lessons Learned

If you are using **JWT** and want to use docs authorizations for testing.

In `settings.py`:

```python
SWAGGER_SETTINGS = {
    "USE_SESSION_AUTH": False,  # disable Django login as an authentication/authorization mechanism
    "SECURITY_DEFINITIONS": {
        "JWT": {
            "type": "apiKey",
            "name": "Authorization",
            "in": "header",
            "description": "Format: `Bearer <access_token>`",
        },
    },
}

or

SWAGGER_SETTINGS = {
    "SECURITY_DEFINITIONS": {
        "Basic": {"type": "basic"},
        "Bearer": {"type": "apiKey", "name": "Authorization", "in": "header"},
    }
}
```

After the setting is completed, enter your Token as shown in the figure. Because [document](https://drf-yasg.readthedocs.io/en/stable/security.html) does not contain a prefix.
![image](https://user-images.githubusercontent.com/32898576/174738705-0b4c2bc3-1cd6-4288-b76e-37d2305ded68.png)

## Documentation

Django REST framework: <https://www.django-rest-framework.org/topics/documenting-your-api/#drf-yasg-yet-another-swagger-generator>

GitHub: <https://github.com/axnsan12/drf-yasg/>

PyPI: <https://drf-yasg.readthedocs.io/en/stable/>
