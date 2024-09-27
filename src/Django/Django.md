# Django Development

As described in the Deployment section, a simple Django project structure is created with:
```shell
django-admin startproject isoVisDev 
```
Following the steps to deploy the application AWS successfully, the following tree structure should be as of follows:
```plaintext 
isoVisDev/
├── manage.py
├── requirements.txt
├── .ebextensions/
│   └── django.config
├── .elasticbeanstalk/
│   └── config.yml
└── isoVisDev/
    ├── asgi.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```

## Guide

This next section is a guide to create a more functioning Django application:
- covering the basic folder structure for live rendering
- creating a basic homepage and two tabs
- interactive widgets and filtering using a SQLite database
- plotting with python and Rscripts