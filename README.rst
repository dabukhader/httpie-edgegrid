httpie-edgegrid
===============

EdgeGrid plugin for `HTTPie <https://github.com/jkbr/httpie>`_.


Installation
------------

To install from sources:

.. code-block:: bash

    $ python setup.py install

If using python 3 on Mac, replace python with python3:

.. code-block:: bash

    $ python3 setup.py install

If you have problems intalling from sources, you could use pip:

.. code-block:: bash

    $ pip install httpie-edgegrid




Usage
-----

The EdgeGrid plugin relies on a .edgerc credentials file that needs to be created in your home directory and organized by [section] following the format below. Each [section] can contain a different credentials set allowing you to store all of your credentials in a single .edgerc file. 

.. code-block:: bash

		[default]
		client_secret = xxxx
		host = xxxx # Note, don't include the https:// here
		access_token = xxxx
		client_token = xxxx
		max-body = xxxx

		[section1]
		client_secret = xxxx
		host = xxxx # Note, don't include the https:// here
		access_token = xxxx
		client_token = xxxx
		max-body = xxxx

Once you have the credentials set up, here is an example of what an Akamai OPEN API call would look like:

.. code-block:: bash

	% http --auth-type edgegrid -a <section_name>: :/<api_endpoint>

Example
-------

Making the diagnostic-tools API `locations` call:

.. code-block:: bash

	% http --auth-type edgegrid -a default: :/diagnostic-tools/v1/locations
	
Troubleshooting
---------------

MacOS Sierra users have reported  the error "http: error: argument --auth-type/-A: invalid choice: 'edgegrid' (choose from 'basic', 'digest')" after installation. Try installing using pip instead.

The error "ImportError: ‘pyOpenSSL’ module missing required functionality. Try upgrading to v0.14 or newer" requires you to install an updated version of `pyOpenSSL`:

.. code-block:: bash

	$ pip install --ignore-installed pyOpenSSL

Since v0.9.4 of httpie the Mac homebrew package is build with python3. If you get an error for "ImportError: No module named cryptography" then probably you installed httpie-edgegrid with python2.7. To explicitly install with python3 use:

.. code-block:: bash

	$ sudo python3 setup.py install

Or with pip3:

.. code-block:: bash

	$ sudo pip3 install httpie-edgegrid
