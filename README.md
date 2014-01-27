django-app-dev
==============

Basic Django app structure, development-ready and test-ready, Tox integrated.

Getting started
---------------

In order to get started with this framework, you simply need to clone this repository:

```
git clone <repo-url>
```

And create a virtual environment with [Tox](http://tox.readthedocs.org) installed:

```
mkvirtualenv django-app-dev
pip install tox
```

You will then run tests with:

```
tox
```

It's that simple! Go ahead, try it out!


Dependencies
------------

Only [Tox](http://tox.readthedocs.org) is required to be installed. The version supported by this framework is >=1.6, which is the latest, so `pip install tox` should do the magic. If you want to clearly specify Tox's version, run `pip install 'tox >= 1.6'`. This will assure that testing will occur in virtualenvs that use a version of [PIP](http://www.pip-installer.org/en/latest/index.html) higher than 1.5 (which is required by current Tox configuration, see below).

The other app dependencies are automatically detected and installed via Tox from `setup.py`.

If you need dependencies only for testing, adding them to `tox.ini`'s `deps` should do the work.

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

Note: Initial app data should be put in a fixture called `initial_data`.

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
* Since version 1.5 of [PIP](http://www.pip-installer.org/en/latest/index.html), `dependency_links` are ignored by default. To enable them, be sure to include the `--process-dependency-links` flag;
* The `--pre` flag allows installing pre-release versions of the required packages;
* A summary of your app's test can be found in `pytest-results.xml` after running a Tox;
* Modules that need to be tested should be placed in `{posargs:[...]}`.


Going further
-------------

So you've got this basic Django app structure, ready for development and for testing (thanks to the wonderful Tox tool). What's next?

You may find that the structure lacks some files your dev skills desire (such as middleware, templatetags, wsgi and so on). Go ahead and create them! This app structure was intended to be minimal, saving you some time when starting to draft your award-winning app you had in mind. You can add/remove files from this structure to fulfil your dev-guru desire.

You may want to support different versions of PIP or Tox, but you should be aware that PIP has changed a bit from version 1.5, so backwards compatibility is quite hard, if not, impossible to achieve. Bear this in mind and read the docs when you'd wish to change something.

Contributing
------------

Just fork this repo, do your magic and send back a pull request!

License
-------

The MIT License (MIT)

Copyright (c) 2014 Andrei Horak

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
