django-app-dev
==============

Basic Django app structure, development-ready and test-ready, Tox integrated.


Knowing what's in the box
-------------------------

The _django-app-dev_ tree looks like this:


```
.
├── app
│   ├── admin.py
│   ├── fixtures
│   │   └── fixture.json
│   ├── __init__.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── settings.py
│   ├── static
│   │   ├── admin
│   │   │   ├── css
│   │   │   ├── images
│   │   │   └── js
│   │   └── app
│   │       ├── css
│   │       ├── images
│   │       └── js
│   ├── templates
│   │   ├── admin
│   │   │   └── sample_template.html
│   │   └── app
│   │       └── sample_template.html
│   ├── tests
│   │   ├── __init__.py
│   │   ├── models.py
│   │   ├── settings.py
│   │   ├── tests.py
│   │   └── urls.py
│   ├── urls.py
│   └── views.py
├── LICENSE
├── MANIFEST.in
├── README.md
├── setup.py
└── tox.ini


```

### app/admin.py app/models.py app/settings.py app/urls.py app/views.py

Django-specific files; nothing special about them -- just use them as you're used to.

### app/fixtures

Any fixtures needed throughout the app, whether they are initial app data or required for tests, should be put in here.

Note: Initial app data should be put in a fixture called `initial_data`.s

### app/migrations

[South](http://south.readthedocs.org/en/latest/) migrations will reside here.

### app/static

Any static file used throughout the app should be put here in its corresponding directory. The rule you have to bear in mind is that every static file should be placed under [app-name]/[file-type] and you're good to go.

### app/templates

Templates used in your app should be placed here. The same rule as with static files apply, so be sure to check the above paragraph.

### app/tests/

Everything related to testing should be placed under this directory. As of _django-app-dev_'s tox configuration, tests that reside in `app/tests/tests.py` will be run, using the settings in `app/tests/settings.py`.

Custom test urls should be placed under `app/tests/urls.py`. These are automatically included in tests via the tests settings file.

Additional files, such as models, or additional tests can be placed in new files within this directory (but pay attention on how you configure Tox to run your new tests!).

### MANIFEST.in

You should include here all non-.py files that are required by your app and must be distributed with it.

### setup.py

Describes your awesomely-crafted project. You should modify this by giving the right `name` for your app, its current `version`, a short `description` and the `author` name and `author_email` (that's you!).

Furthermore, any Python package your app relies on should be placed under `DEPENDENCIES` and any links to these packages should be put in `DEPENDENCY_LINKS`. Also, any package required for setting up your app should be put in `setup_requires`.

### tox.ini

[Tox](http://tox.readthedocs.org) configuration file. You should specify here how your tests need to be run, what test dependencies you need and other stuff.

Currently, [py.test](http://pytest.org) is the chosen tool for running the app's tests; [pytest-django](http://pytest-django.readthedocs.org/en/latest/) ties it up to the Django framework.

Notes:
* Since version 1.5 of PIP, `dependency_links` are ignored by default. To enable them, be sure to include the `--process-dependency-links` flag;
* The `--pre` flag allows installing pre-release versions of the required packages;
* A summary of your app's test can be found in `pytest-results.xml` after running a Tox;
* Modules that need to be tested should be placed in `{posargs:[...]}`.


Going further
-------------
