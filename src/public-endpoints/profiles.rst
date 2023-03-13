Profiles
========

There are 2 endpoints that return a list of artist or venue names, for use in dropdown, a ticker, or whatever other use that you can dream up. They are incredibly simple endpoints, and only include artists or venues that have a confirmed event in the current city's festival.

.. code-block:: python

    import json
    import requests

    base_url = 'https://nf.makemusicday.org'
    artist_list_url = f'{base_url}/api/cities/events/artists'

    resp = requests.get(artist_list_url)

    print(json.dumps(resp.json(), sort_keys=True, indent=4))


Which will output the following:

.. code-block:: json

    {
        "artists": [
            "Group MM",
            "Turtle Trolls",
            "Group of Shouting People",
            "Joe Slam and the Spaceship",
            "Pretzel Dads",
            "Rageful Chickens",
            "The B-Sharps",
            "Ellen Reid"
        ]
    }

Similarly, you can do the same for venues:

.. code-block:: python

    import json
    import requests

    base_url = 'https://nf.makemusicday.org'
    venue_list_url = f'{base_url}/api/cities/events/venues'

    resp = requests.get(venue_list_url)

    print(json.dumps(resp.json(), sort_keys=True, indent=4))


Which will output the following:

.. code-block:: json

    {
        "venues": [
            "Fire escape",
            "The Blue Note",
            "Rageful Coop",
            "The Chicken Coop",
            "Bar66",
            "Turtle Pond",
            "House of Millet",
            "RadioShack Loading Dock"
        ]
    }


Profile-specific events
-----------------------

It is also possible to retrieve the events for a specific artist or venue profile. These endpoints allow for pagination, should the need arise.

.. code-block:: python

    import json
    import requests

    # Set the artist id appropriately for the artist you wish to query for
    artist_id = 'd6426661-7deb-4fbb-b24c-9693590070ab'
    base_url = 'https://nf.makemusicday.org'
    events_url = f'{base_url}/api/artists/{artist_id}/events'

    resp = requests.get(events_url)

    print(json.dumps(resp.json(), sort_keys=True, indent=4))

.. include:: ../_includes/responses/events/artist.rst


Or for a venue's events:

.. code-block:: python

    import json
    import requests

    # Set the artist id appropriately for the artist you wish to query for
    venue_id = 'd8ff9bd9-8773-40a5-8b61-1d8725a59158'
    base_url = 'https://nf.makemusicday.org'
    events_url = f'{base_url}/api/venues/{venue_id}/events'

    resp = requests.get(events_url)

    print(json.dumps(resp.json(), sort_keys=True, indent=4))

.. include:: ../_includes/responses/events/venue.rst
