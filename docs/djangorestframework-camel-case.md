
# Django REST Framework JSON CamelCase

Camel case JSON support for Django REST framework.

## Installation

Install djangorestframework-camel-case with pipenv

```bash
pipenv install djangorestframework-camel-case
```

In `settings.py`:

```python
REST_FRAMEWORK = {
    'DEFAULT_RENDERER_CLASSES': [
        'djangorestframework_camel_case.render.CamelCaseJSONRenderer',
        'djangorestframework_camel_case.render.CamelCaseBrowsableAPIRenderer',
        # Any other renders
    ],
    'DEFAULT_PARSER_CLASSES': [
        # If you use MultiPartFormParser or FormParser, we also have a camel case version
        'djangorestframework_camel_case.parser.CamelCaseFormParser',
        'djangorestframework_camel_case.parser.CamelCaseMultiPartParser',
        'djangorestframework_camel_case.parser.CamelCaseJSONParser',
        # Any other parsers
    ],
}
```

### Underscoreize Options

#### No Underscore Before Number

As raised in this comment there are two conventions of snake case.

```text
# Case 1 (Package default)
v2Counter -> v_2_counter
fooBar2 -> foo_bar_2

# Case 2
v2Counter -> v2_counter
fooBar2 -> foo_bar2
```

By default, the package uses the first case. To use the second case, specify it in your django settings file.

In `settings.py`:

```python
REST_FRAMEWORK = {
    'JSON_UNDERSCOREIZE': {
        'no_underscore_before_number': True,
    },
}
```

Alternatively, you can change this behavior on a class level by setting json_underscoreize:

```python
from djangorestframework_camel_case.parser import CamelCaseJSONParser
from rest_framework.generics import CreateAPIView


class NoUnderscoreBeforeNumberCamelCaseJSONParser(CamelCaseJSONParser):
    json_underscoreize = {'no_underscore_before_number': True}


class MyView(CreateAPIView):
    queryset = MyModel.objects.all()
    serializer_class = MySerializer
    parser_classes = (NoUnderscoreBeforeNumberCamelCaseJSONParser,)
```

## Documentation

Django REST framework: <https://www.django-rest-framework.org/api-guide/parsers/#camelcase-json>

GitHub: <https://github.com/vbabiy/djangorestframework-camel-case>

PyPI: <https://pypi.org/project/djangorestframework-camel-case/T>
