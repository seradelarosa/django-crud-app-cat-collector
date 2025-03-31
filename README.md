# django-crud-app-cat-collector
pipenv install django
pipenv shell
django-admin startproject catcollector .

MVC - Mongo and Express
MVT - Model/Views/Template

Review of Express framework
Express is characterized as a minimalist framework, offering just enough tools to get started but not much beyond the basics. This approach provides the flexibility to define routes, map controller actions, and render dynamic views according to your project’s needs. The lack of rigid structure means file naming and organization are left largely to the developer’s discretion. When additional functionality is required, it typically involves integrating and configuring middleware or outside libraries. This setup is ideal if you appreciate a “build-it-your-way” philosophy.

Django is a full-featured framework, designed to include a comprehensive suite of built-in functionalities. It adheres to a strict set of conventions, guiding you on how to structure your code, name your files, and even how to handle database operations. This structured approach is accompanied by numerous helper classes and methods, simplifying tasks that in Express might require additional packages.

For those familiar with frameworks like Express, Django might initially seem restrictive. However, this structure aims to ensure scalability and maintainability of applications. It’s important to note that becoming familiar with Django’s many features can be more time-consuming compared to grasping the basics of Express. Nevertheless, learning the essentials of Django is manageable and can greatly accelerate development once you are accustomed to its paradigms.

In Django, the HTTP request/response cycle is managed by built-in components, which simplifies much of the setup process. This integration can greatly benefit newcomers to web development or anyone who wants to simplify their application’s infrastructure.

python3 manage.py startapp main_app
settings.py
INSTALLED_APPS = [
    # add main_app here
    'main_app',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
python3 manage.py runserver

stop server to fix migration message
^C
python3 manage.py migrate
create urls.py in main app: touch main_app/urls.py

--------------------------

# catcollector/urls.py

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('main_app.urls')), # Mounts main_app's routes at the root URL
]

---------------------------

# main_app/urls.py

from django.urls import path
from . import views # Import views to connect routes to view functions

urlpatterns = [
    path('', views.home, name='home'),
]

----------------------------

# main_app/views.py

from django.shortcuts import render

# Import HttpResponse to send text-based responses
from django.http import HttpResponse

# Define the home view function
def home(request):
    # Send a simple HTML response
    return HttpResponse('<h1>Hello ᓚᘏᗢ</h1>')

-------------------------------

run python3 manage.py runserver
