===========
python-wsgi
===========

Ansible role to install WSGI by compiling with a custom Python version.

Django case
-----------

In order to deploy a Python 3 Django 1.8+ project to the above setup,
WSGI will not respect the python version specified in virtualenv
unless WSGI is compiled with the same Python version.

Otherwise, looking into the error traceback will reveal that the Python running
will be the default and not 3.4+. It is `possible to provide`_ to WSGI a different Python executable
only if WSGI is `compiled with the correct Python`_.

Add the role ``python-wsgi`` to install WSGI.

Variables
---------

- ``wsgi_src``: Directory where to download wsgi, default: ``~/mod_wsgi_src``
- ``wsgi_ver``: The wsgi version to install, default: 4.4.21
- ``python_version``: The python version to install (major.minor), default: 3.5

Useful links
------------

- https://code.google.com/p/modwsgi/wiki/QuickInstallationGuide
- https://www.digitalocean.com/community/tutorials/installing-mod_wsgi-on-ubuntu-12-04
.. _possible to provide: http://stackoverflow.com/questions/6450459/mod-wsgi-and-multiple-installations-of-python
.. _compiled with the correct Python: https://code.google.com/p/modwsgi/wiki/ConfigurationDirectives#WSGIPythonHome

Playbook examples
-----------------

Plain::

    ---
    - hosts: servers
      roles:
        - python-wsgi

Specify variables::

    ---
    - hosts: servers
      gather_facts: no
      roles:
        - role: python-wsgi
          python_version: 3.4

