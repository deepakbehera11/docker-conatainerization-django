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

![](https://github.com/deepakbehera11/docker-conatainerization-django/blob/6c747fb7d8edcb58b4f845a8aaaebef71df65e19/assets/Screenshot-demo-view.png)

### To define a URLconf for the demo  app, creating a file `polls/urls.py` with the following 
![](https://github.com/deepakbehera11/docker-conatainerization-django/blob/6c747fb7d8edcb58b4f845a8aaaebef71df65e19/assets/Screenshot-demo-url-setup.png)

#### Next is to configure the root URLconf in the `mysite` project to include the URLconf defined in `demo.urls`. To do this, added an import for `django.urls.include` in `mysite/urls.py` and insert an `include()` in the `urlpatterns` list
![](https://github.com/deepakbehera11/docker-conatainerization-django/blob/6c747fb7d8edcb58b4f845a8aaaebef71df65e19/assets/Screenshot-mysite-url.png)

#### Inside the setting which is in the `mysite/settings` we have to import the `os`  which allows you to interact with the operating system—things like file paths, environment variables, and directories. And update the os in the Template 

![](https://github.com/deepakbehera11/docker-conatainerization-django/blob/6c747fb7d8edcb58b4f845a8aaaebef71df65e19/assets/Screenshot%20import-os-insettings.png)

![](https://github.com/deepakbehera11/docker-conatainerization-django/blob/6c747fb7d8edcb58b4f845a8aaaebef71df65e19/assets/Screenshot-update-os-in-template.png)

#### Then created the ec2 instance then cloned the repo

#### Exposed the 8080 traffic to the security group inbound rule

#### Then going into the directory where the application is then building the docker image by
```
docker build .
```
![](https://github.com/deepakbehera11/docker-conatainerization-django/blob/9de8b0b50bbaa8fc92756b70f737e11bdf8e066f/assets/Screenshot-docker-images-cmd.png)

#### The Django application will be running inside our container at 8000, but we are trying to run the application on ec2 instance,  so we need port mapping. Instead of the command—— docker run -it < containerID> , we have to run 
```
docker run -p 8000:8000 -it <containerID>
```
![](https://github.com/deepakbehera11/docker-conatainerization-django/blob/9de8b0b50bbaa8fc92756b70f737e11bdf8e066f/assets/Screenshot-docker-run.png)

#### Accessing the application which is a static site
![](https://github.com/deepakbehera11/docker-conatainerization-django/blob/6c747fb7d8edcb58b4f845a8aaaebef71df65e19/assets/Screenshot-app.png)

#### the application will be accessed when we give `/demo` after the URL because it's the context root of the application. The [urls.py](http://urls.py) in the mysite directory will understand that whenever anyone tries to hit the /demo, it will try to serve the content on the demo application..

![](https://github.com/deepakbehera11/docker-conatainerization-django/blob/6c747fb7d8edcb58b4f845a8aaaebef71df65e19/assets/Screenshot-demo-opening.png)











