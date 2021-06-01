Gemini Music Event Matchmaking software
=======================================

Gemini was written to accomplish the goals of the `Make Music Alliance`_, specifically to enable
artists and venues to find each other and plan performances for a one-day music festival, and to
allow the system to be used for various cities around the world.

The basic use is as follows:

1. a city is created in the system, without this, there is no other record type that can exist
2. a administrative user setups up the various details for this city (dates/times/neighbourhoods)
3. end-users create user accounts for themselves
4. end-users create venue or artist profiles for themselves
5. end-users search for other venue or artist profiles and request performances
6. after the performance details have been accepted by both parties, the city admin takes action
   (approve, deny, suggest changes) to the performance based on city specific needs/requirements.
7. once a performance has been approved by the city, it is included in a performance listing to
   the general public with a subset of artist/venue information.


System structure
----------------

Each city has a unique subdomain associated to them. All API endpoints work on the specific city
that the subdomain belongs to. Most requests need to be sent to the appropriate city's subdomain.
There are only a handful of API endpoints that are available with a global scope. The request are
restricted to their appropriate city.

Requests must use various different methods (``GET``, ``POST``, ``PUT``, ``PATCH``, ``DELETE``)
to accomplish the appropriate actions. All requests (other than ``GET``) should be sending a
content-type of ``application/json``. The sole exception to this is the image upload endpoints
for the city logo and the artist avatars, which take ``multipart/form-data``.

Responses return appropriate HTTP status codes to indicate success or failure, along with an error
message payload indicating what caused the error, if possible, or the data requested on success.

.. note::
  There are a few endpoints that respond with ``204 No Content`` and have no response payload upon
  success. Specifically, those convenience endpoints that are toggling a boolean flag on a record.

The Gemini API uses OAuth2_ for user authentication and as such you will need to request client
credentials prior to being able to interact with most facets of the API.


Automations
-----------

There are various automated email notifications that trigger when certain requests are made to the API.
Specifically:

* request for confirmation of email address upon user creation and upon any edit of the email address
  on record
* forgot password process whenever the user requests a password reset
* security notice regarding password reset whenever the user successfully completes a password reset
* notice of account deletion (a GDPR compliant wipe of all of a user's data upon their request)
* new event requested by other party
* event accepted by other party
* event approved by city admin
* event cancelled by city admin or other party
* new message has been received


Both the Gemini_ code and the documentation_ is open source, and available on GitHub. The documentation is built using Sphinx_.


.. _Make Music Alliance: https://www.makemusicday.org
.. _OAuth2: https://oauth.net/2/
.. _Gemini: https://github.com/makemusicday/gemini
.. _documentation: https://github.com/makemusicday/gemini-docs
.. _Sphinx: http://sphinx.pocoo.org/

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   contributing
   public-endpoints
   authentication
