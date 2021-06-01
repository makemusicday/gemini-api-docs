Authentication
==============

The Gemini API uses OAuth2_ for client authentication and as such you will need to request client
credentials prior to being able to interact with most facets of the API. It is currently limited
to the password grant flow.

Once you have requested and obtained a client ID and secret, you will be able to use those to
exchange a user's credentials for a bearer token. All API functionality that is protected by
authentication requires that a valid bearer token be provided.

There are many libraries and frameworks that implement the OAuth 2 specification and will be
compatible with the API's implementation. You are, of course, more than welcome to interact
with the API via your own custom built OAuth 2 client library.


Creating a user
---------------

.. code-block:: python

  import json
  import os
  import requests

  # GEMINI_HOST should be something like: "https://<city>.makemusicday.org"
  base_host = os.environ['GEMINI_HOST']

  # GEMINI_CLIENT_ID and GEMINI_CLIENT_SECRET are specific to your API client.
  client_id = os.environ['GEMINI_CLIENT_ID']
  client_secret = os.environ['GEMINI_CLIENT_SECRET']

  default_scopes = "profile performer venue"

  create_user_url = f"{base_host}/api/users/create"
  create_user_payload = {
      "email": os.argv[0],         # provided at runtime
      "password": os.argv[1],      # provided at runtime
      "grant_type": "password",    # Only 'password' grants are supported at this time
      "scope": "profile performer venue",
      "has_accepted_terms": True,  # Indicates that the user has accepted the city's terms and conditions
  }

  resp = requests.post(
      create_user_url,
      auth=requests.auth.HTTPBasicAuth(client_id, client_secret),
      json=create_user_payload
  )

  print(json.dumps(resp, indent=True))


After reviewing this code, you might be wondering what the valid scopes are. There are 5 possible scopes:

- ``profile``: basically every token needs this to function. It allows viewing other artist or venue
  profiles.
- ``performer``: this is required if the user wishes to create/update/delete an artist profile.
- ``venue``: this is required if the user wishes to create/update/delete a venue profile.
- ``city``: this is a special scope that cannot be requested. It is granted upon token creation to
  those users that have been marked as administrators of a city.
- ``admin``: this is a special scope that cannot be requested. It is granted upon token creation to
  those users that have been marked as administrators of the entire system.

Most users will want to have the 3 default scopes listed in the example, in order to be able to
interact with the various aspects of the system.

Assuming that there were no errors in the posted payload, the server should respond with a status
code of ``201`` and the output from the example code should look similar to this:

.. include:: _includes/responses/auth/login.rst

From the response, you would need to make note of the ``access_token`` to make further requests as
this new user.

You should also note that the ``_links`` dictionary has all the actions available to this user at
this point, along with the request method needed to perform the desired action.


Logging in
----------

Now that you have a user, and assuming that your ``access_token`` has expired, you can use the login
endpoint to obtain a new ``access_token``, which follows the same rough structure as the create
endpoint, with the notable exception that `username` is used in the payload instead of `email` to
allow for better integration with various pre-existing OAuth2 clients.

.. code-block:: python

  login_user_url = f"{base_host}/api/oauth/token"
  login_user_payload = {
      "username": create_user_payload['email'],
      "password": create_user_payload['password'],
      "grant_type": "password",
      "scope": "profile performer venue",
  }

  resp = requests.post(
      login_user_url,
      headers={'Authorization': f'Bearer: {access_token}'},
      json=login_user_payload
  )

  print(json.dumps(resp, indent=True))


Once again, a successful response will have the ``201`` status code, not because you are creating
a new user, but because you are creating a new token for the user. And the response payload will
look almost exactly the same as for the create user endpoint shown above.

.. _OAuth2: https://oauth.net/2/
