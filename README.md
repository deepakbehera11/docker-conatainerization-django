# Containerizing a Django Web Application with Python and Docker

This project walks through the creation of a simple Django web app and how to containerize it using Docker for deployment, including setup on an AWS EC2 instance.

### 📦 Installing Django and Creating the Project

1. Created a directory called `djangoproj`
2. Bootstrapped the project:
   ```bash
   django-admin startproject mysite djangoproj
   
3. This created a project called mysite inside the djangoproj directory.
```
 djangoproj/
    - manage.py
    - mysite/
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    ├── asgi.py
    └── wsgi.py
```
### Creating the `Demo` App inside the djangoproj, same directory as manage.py is
```
cd djangoproj
python manage.py startapp demo
```
That’ll create a directory demo, which is laid out like this:

```
demo/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```
### Configuring Views and URLs

![]()

### To define a URLconf for the demo  app, creating a file `polls/urls.py` with the following 
![]()

#### Next is to configure the root URLconf in the `mysite` project to include the URLconf defined in `demo.urls`. To do this, added an import for `django.urls.include` in `mysite/urls.py` and insert an `include()` in the `urlpatterns` list
![]()

#### Inside the setting which is in the mysite/settings we have to import the os  which allows you to interact with the operating system—things like file paths, environment variables, and directories.
















