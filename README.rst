README
======

**DISCLAIMER: This is extremely alpha/beta/not-production code at this point.  I take no
responsiblity for the use of this software to manage OpenSRS accounts.**

This package provides a set of `pyCLI`_ applications for interfacing with an `OpenSRS`_
reseller account.

.. _pyCLI: http://packages.python.org/pyCLI/
.. _OpenSRS: http://www.opensrs.com/

Installation
------------

Install from pypi::

 $ pip install opensrscli

Development
-----------

Install virtualenv and distribute if they aren't already present::

 $ pip install distribute virtualenv

Clone the project and initialize a development environment::

 $ git clone git://github.com/shawnsi/opensrs-cli.git && cd opensrs-cli
 $ virtualenv . 
 $ source bin/activate

You can use distribute to install dependencies and setup entry points::

 $ python setup.py develop

Configuration
-------------

Basic Auth
~~~~~~~~~~

You must create a yaml file to provide OpenSRS authentication info at a 
minimum. This should match the user and private key information you setup in
the OpenSRS reseller dashboard for API access.

Auth template::

 username:
 private_key:

Now provide the prefs.yaml file to opensrs commands with the -p or
--preferences parameter.  If no preferences file is specified opensrs-cli will
look in `$HOME/.opensrs/prefs`.

Contact Sets
~~~~~~~~~~~~

In order to perform and domain registration or transfers contact sets will need
to be defined.  Add them to prefs.yaml using the following template.  A default
contact can be provided and fields can be overriden for admin, owner, billing,
or tech contacts.

Contact set template::

  contact_set:
    default:
      first_name:
      last_name:
      org_name:
      address1:
      city:
      state:
      postal_code:
      country:
      phone:
      email:
    billing:
      last_name:
      email:
    tech:
      last_name:
      email:

Usage
-----

This package installs scripts prefixed with opensrs.

Currently provided:

- opensrs-balance

  Returns account balance

- opensrs-check-transfer

  Returns transfer status of one or more domains

- opensrs-transfer

  Transfers one or more domains according to contact sets described above

- opensrs-get-nameservers

  Get the nameservers attached to one or more domains

- opensrs-set-nameservers

  Sets default nameservers from user preferences file on one or more domains

- opensrs-lock

  Lock one or more domains

- opensrs-unlock

  Unlock one or more domains

