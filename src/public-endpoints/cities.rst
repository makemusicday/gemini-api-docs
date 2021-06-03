Cities
======


Retrieving the available cities
-------------------------------

Every city's site exposes a list of cities configured in the system. However, if a city has decided to self-host the Gemini_ software, that particular city will not be returned in this endpoint, and vice versa, when connecting to that city's install, it will not return all the other available cities.

.. code-block:: python

  import json
  import os
  import requests

  # GEMINI_HOST should be something like: "https://<city>.makemusicday.org"
  base_host = os.environ['GEMINI_HOST']

  cities_url = f'{base_host}/api/cities'

  resp = requests.get(cities_url)

  print(json.dumps(resp.json(), indent=True, indent=4))


The response provided by the system will be variable in length, depending on how many cities are configured in this particular Gemini_ installation, but it should look something like this:

.. include:: ../_includes/responses/cities/list.rst

As you can see, there are 2 cities, with a base amount of information about each. You should note that the ``base_url`` key contains the hostname to use when interacting with each city. The various other keys returned are somewhat self-explanatory.


Retrieving information about the current host
---------------------------------------------

Continuing on the previous example, if you have a hostname, but don't know what city it is serving data for, this can be obtained easily in a format similar to the previous example:

.. code-block:: python

  import json
  import os
  import requests

  base_host = 'https://nf.makemusicday.org'

  city_info_url = f'{base_host}/api/city/current'

  resp = requests.get(city_info_url)

  print(json.dumps(resp.json(), indent=True, indent=4))


The response should look something like this:

.. include:: ../_includes/responses/cities/current.rst


.. _Gemini: https://github.com/makemusicday/gemini
