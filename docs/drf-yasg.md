
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
  'django.contrib.staticfiles',  # required for serving swagger ui's css/js files
  'drf_yasg',
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
