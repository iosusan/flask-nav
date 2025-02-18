Changes in this fork
=====================
edited flask_nav/__init__.py to replace collections.MutableMapping with collections.abc.MutableMapping to make this compatible with python 3.10


Flask-Nav
=========

Flask-Nav is a `Flask <http://flask.pocoo.org>`_-Extension to ease the creation
of navigational Elements in Applications. It provides means to Express the
Navigational structure and different ways to render these, making it easy to
custom tailor it for your application.

A motivating example:

.. code-block:: python

    from flask import Flask
    from flask_nav import Nav
    from flask_nav.elements import *

    nav = Nav()

    # registers the "top" menubar
    nav.register_element('top', Navbar(
        View('Widgits, Inc.', 'index'),
        View('Our Mission', 'about'),
        Subgroup(
            'Products',
            View('Wg240-Series', 'products', product='wg240'),
            View('Wg250-Series', 'products', product='wg250'),
            Separator(),
            Label('Discontinued Products'),
            View('Wg10X', 'products', product='wg10x'),
        ),
        Link('Tech Support', href='http://techsupport.invalid/widgits_inc'),
    ))


    app = Flask(__name__)
    # [...] (view definitions)

    nav.init_app(app)

You can find a small, runnable example application inside the ``example``
folder. To run it, install `Flask-Appconfig
<https://github.com/mbr/flask-appconfig>`_ and execute::

    $ flask --app=example dev

The `full documentation <http://pythonhosted.org/flask-nav/>`_ can be found on PyPI.
