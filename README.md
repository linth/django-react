# django-react
Combine with frontend (React.js) and backend (Django).

## Usage
```
$ git clone https://github.com/linth/django-react.git
$ cd django-react/frontend
$ npm run build

cd ..
$ pip install -r requirent.txt
$ python manage.py makemigrations
$ python manage.py migrate
$ python manage.py runserver
```

## How to create a new django and react
1. Install django packages
```
$ pip install django==2
$ pip install django-cors-headers
```

2. Create a django project and application.
```
$ django-admin startproject django_react
$ cd django_react
$ python manage.py startapp backend
```

3. Edit settings.py in the django project.
```
# settings.py
INSTALLED_APPS = [
    ...
    ...
    'backend',
]
MIDDLEWARE = [
    ...
    ...
    'corsheaders.middleware.CorsMiddleware',
]
TEMPLATES = [
    {
        ...
        'DIRS': ['frontend/build'],
        ...
    },
]
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, "frontend/build/static"),
]
CORS_ORIGIN_ALLOW_ALL = True
```

4. Edit the urls.py in the django project.
```
# urls.py
from django.views.generic import TemplateView
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', TemplateView.as_view(template_name='index.html')),
]
```

5. Create a new React project.
```
$ npx create-react-app frontend
$ cd frontend
$ npm run build
```

6. Run server
```
$ python manage.py runserver
```
