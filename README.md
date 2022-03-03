### Pet Adoption System
# An animal shelter adoption system

## Project requirements:
* Store pets with a name, age, vaccination record, and other details
* Allow administrators to create, edit, or delete pets
* Allow users to see a list of available pets, with details about each one

## Features of Django
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
* create app command: *python manage.py startapp appname*

    ```python
    # create app command: directory layout
    appname/
        __init__.py
        admin.py
        apps.py
        migrations/
            __init__.py
        models.py
        tests.py
        views.p
    ```
* Pieces of an App
    * apps.py: Contorls settings specific to this app
    * models.py: Provides the data layer Django uses to contruct our database schema and queries
    * admin.py: defines an administrative interface for the app that will allow us to see and edit the date related to the app
    * urls.py: used for URL routing specific to the app
    * views.py: defines teh logic and control flow for handling the requests and defines teh HTTP responses that are returned
    * test.py: used for writing unit tests for the functionality of this app
    * imigrations/: holds the files Django uses to migrate the database as wee create and change our database schema over time


## Django Apps
* A component in a Django project
* A folder with a set of Python files
* Each app fits a specific purpose
* Examples of Django projects
    * Blog
    * Forum
    * Wiki
    * Our project: manage pet adoptions

## MVC Architecture (Model-View-Control) for Django
* Different names in Django: URL patterns, views, models, templates
    * URL patterns: wisdompets/urls.py
    * Views: adoptions/views.py
    * Models: adptions/models.py
    * Templates: adoptions/templates
    
    ```python
    # MVC architecture in Django
    URL Patterns -------> Views ----------> Templates
    #  http://wisdompets.com
       (empty)            home()            home.html  
    #  http://wisdompets.com/adoptions/1/
    /adptions/1/         pet_detail()     pet_detail.html
                            |
                            |
                          Models
    ```

## Django Models
* Create the data layer of a Django app
* Define database structure
* Allow us to query teh database
    * models.py: contains the set of models for its Django app
    * a model is a class inheriting from django.db.models.Model and it defines database fileds as class attributes
* Models as Spreadsheets: each Field as a Colomn, each Record as a Row
    ```python
    # example of data model
    from django.db import models
    class Pet(moedls.Model):
        name = models.CharField(max_length=100)     # max_length required
        submitter = models.CharField(max_length=100)
        submission_date = models.DateTimeField()
        description = models.TextField(blank=True)  # no need max_length
    ```
    * Field Types: **Textual**/**Numeric**/**Miscellaneous**/**Relational** Data
        * CharField: "Product Name"
        * TextFiled: "Tp elaborate on my point..."
        * EmailField: george@site.com
        * URLField: www.example.com
        ----------------------------------------------
        * IntegerField: -1, 0, 1, 20
        * DecimalField: 0.5, 3.14
        ----------------------------------------------
        * BooleanField: True, False
        * DateTimeField: datatime(1960, 1, 1, 8, 0 ,0)
        ----------------------------------------------
        * ForeignKey: 1 (id of record in another table)
        * ManyToManyField: NA

        ```python
        # Field Attrobutes Code Example
        models.CharField(max_length=10, blank=True)
        ```

## Django migrations
* Models: Defines the structure of database tables
* Migrations: Generate scripts to change the database structure
* When is a migration needed?
    * Adding a Model
    * Adding a Field
    * Removing a Field
    * Changing a Field
* Initial Migration: the fisrt migration created fro a new Django app will create tables for the models that are defined
    ```python
    # makemigrations:
        # generates migartion files for later use, 
        # uses current model fields and current database tables
        # Creates numbered files in appname/migrations/
    python manage.py makemigrations
    python manage.py showmigrations
    # migarte:
        # Runs all migrations in the project to the current state
        # Can also run only migrations in a specific app to a specific number using
    python manage.py migrate
    pyhton manage.py migrate <appname> <number>
    # python manage.py migrate adoptions 1
    ```
* unapplied Migartions: when a migartion file has been created, but hasn't been run




