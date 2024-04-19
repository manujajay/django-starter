# Django Starter

This repository is a beginner's guide to developing web applications with Django, a high-level Python web framework that encourages rapid development and clean, pragmatic design. It covers setting up a new Django project, creating models, views, and templates, and running the development server.

## Prerequisites

- Python 3.6 or higher installed on your machine
- Virtual environment (recommended)

## Installation

### Set Up a Virtual Environment

1. **Create and activate a virtual environment**:
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows use `env\Scripts\activate`
   ```

### Install Django

1. **Install Django**:
   ```bash
   pip install django
   ```

### Create a New Django Project

1. **Start a new project**:
   ```bash
   django-admin startproject myproject
   cd myproject
   ```

2. **Run migrations** (creates database schema):
   ```bash
   python manage.py migrate
   ```

3. **Start the development server**:
   ```bash
   python manage.py runserver
   ```

## Building Your First App

1. **Create a new application**:
   ```bash
   python manage.py startapp myapp
   ```

2. **Define models in `myapp/models.py`**:
   ```python
   from django.db import models

   class MyModel(models.Model):
       title = models.CharField(max_length=100)
       description = models.TextField()
   ```

3. **Create and apply migrations**:
   ```bash
   python manage.py makemigrations myapp
   python manage.py migrate
   ```

4. **Define views in `myapp/views.py`**:
   ```python
   from django.http import HttpResponse

   def home(request):
       return HttpResponse("Hello, Django!")
   ```

5. **Map views to URLs in `myapp/urls.py`** (create this file if it doesn't exist):
   ```python
   from django.urls import path
   from . import views

   urlpatterns = [
       path('', views.home, name='home'),
   ]
   ```

6. **Include `myapp/urls.py` in the project's `urls.py`**:
   ```python
   from django.contrib import admin
   from django.urls import include, path

   urlpatterns = [
       path('admin/', admin.site.urls),
       path('', include('myapp.urls')),
   ]
   ```

## Contributing

Contributions that enhance the examples, improve the documentation, or add new features to the starter project are welcome. Please fork the repository, make your changes, and submit a pull request.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
