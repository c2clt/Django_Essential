### Features of Django
* Object-relational mapping (**ORM**)
* URL rounting
* HTML templating
* Form handling
* Unit test

### Django is NOT:
* a programming language
* A web server

## tutorial for starting a project
* check version: *python -m django --version*
* create a project: *django-admin startproject projectname*

    ```python
    # script-generated structured files
    projectname/
        manage.py       # Runs commands
        projectname/
            __init__.py # tells Pyhton that the folder contains Python code
            settings.py # configures the Django project
            urls.py     # Routes web requests based on URL
            asgi.py  # An entry-point for ASGI-compatible web servers to serve your proj
            wsgi.py  # An entry-point for WSGI-compatible web servers to serve your proj
    ```
* command: *cd projectname* to the right place including *projectname* folder and *manage.py*
* start server: *python manage.py runserver*
* clear the unapplied migrations warnings: *python manage.py migrate*