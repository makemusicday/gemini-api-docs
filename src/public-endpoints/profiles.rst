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
