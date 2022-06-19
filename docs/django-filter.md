
# Django Filter Backend

Django-filter is a generic, reusable application to alleviate writing some of the more mundane bits of view code. Specifically, it allows users to filter down a queryset based on a model’s fields, displaying the form to let them do this.

## Installation

Install django-filter with pipenv

```bash
pipenv install django-filter
```

In `settings.py`:

```python
INSTALLED_APPS = [
    'django_filters',
]
```

## Usage/Examples

Django-filter can be used for generating interfaces similar to the Django admin's list_filter interface. It has an API very similar to Django's ModelForms. For example, if you had a Product model you could have a filterset for it with the code:

In create new file `filters.py`:

```python
import django_filters

class ProductFilter(django_filters.FilterSet):
    class Meta:
        model = Product
        fields = ['name', 'price', 'manufacturer']
```

And then in your view you could do:

In `views.py`:

```python
def product_list(request):
    filter = ProductFilter(request.GET, queryset=Product.objects.all())
    return render(request, 'my_app/template.html', {'filter': filter})
```

## Documentation

Django REST framework: <https://www.django-rest-framework.org/api-guide/filtering/#djangofilterbackend>

GitHub: <https://github.com/carltongibson/django-filter>

PyPI: <https://django-filter.readthedocs.io/en/stable/guide/install.html>
