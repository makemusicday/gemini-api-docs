Events
======


Retrieving a list of confirmed events:

.. code-block:: python

    import json
    import requests

    base_url = 'https://nf.makemusicday.org'
    events_url = f'{base_url}/api/cities/events/simple'

    resp = requests.get(events_url)

    print(json.dumps(resp.content, sort_keys=True))


And the response will look similar to this:

.. include:: ../_includes/responses/events.rst


Events with Livestreams
-----------------------

Unlike most of the API endpoints, the streams endpoint will cross city boundaries, retrieving
all available streams. 

.. code-block:: python

    import json
    import requests

    base_url = 'https://nf.makemusicday.org'
    streams_url = f'{base_url}/api/cities/events/streams'

    resp = requests.get(streams_url)

    print(json.dumps(resp.content, sort_keys=True))



And the response will look similar to this:

.. include:: ../_includes/responses/streams.rst
