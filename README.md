django-app-dev
==============

Basic Django app structure, development-ready and test-ready, Tox integrated.


Knowing what's in the box
-------------------------

The _django-app-dev_ tree looks like this:


```
├── app
│   ├── admin.py
│   ├── fixtures
│   │   └── fixture.json
│   ├── forms.py
│   ├── __init__.py
│   ├── middleware.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── settings.py
│   ├── static
│   │   ├── admin
│   │   │   ├── css
│   │   │   ├── images
│   │   │   └── js
│   │   └── app
│   │       ├── css
│   │       ├── images
│   │       └── js
│   ├── templates
│   │   ├── admin
│   │   │   └── sample_template.html
│   │   └── app
│   │       └── sample_template.html
│   ├── templatetags
│   │   ├── app_tags.py
│   │   └── __init__.py
│   ├── tests
│   │   ├── __init__.py
│   │   ├── models.py
│   │   ├── settings.py
│   │   ├── tests.py
│   │   └── urls.py
│   ├── tests.py
│   ├── urls.py
│   ├── views.py
│   └── wsgi.py
├── LICENSE
├── MANIFEST.in
├── README.md
├── setup.py
└── tox.ini

```

### setup.py

Describes your awesomely-crafted project. You should modify this by giving the right `name` for your app, its current `version`, a short `description` and the `author` name and `author_email` (that's you!).

Furthermore, any Python package your app relies on should be placed under `DEPENDENCIES` and any links to these packages should be put in `DEPENDENCY_LINKS`. Also, any package required for setting up your app should be put in `setup_requires`.


Going further
-------------
