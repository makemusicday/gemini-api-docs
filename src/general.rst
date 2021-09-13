General API Notes
=================

Each city has a unique subdomain associated to them. All API endpoints will work on any given city
that the subdomain belongs to. Most requests need to be sent to the appropriate city's subdomain
for the API to associate newly created or updated data with the correct city. However, there are
a handful of API endpoints that are available with a global scope that crosses the city boundaries.

Requests must use various different methods (``GET``, ``POST``, ``PUT``, ``PATCH``, ``DELETE``)
to accomplish the appropriate actions. All requests (other than ``GET``) should be sending a
content-type of ``application/json``. The sole exception to this is the image upload endpoints
for the city logo and the artist avatars, which take ``multipart/form-data``.

Responses return appropriate HTTP status codes to indicate success (``200-299``) or failure
(``400-599``), along with an error message payload indicating what caused the error, if possible,
or the data requested on success. Additionally, there are several instances where a redirect
status code (``300-399``) will be returned with the appropriate URL to redirect to.

.. note::
  There are a few endpoints that respond with ``204 No Content`` and have no response payload upon
  success. Specifically, those convenience endpoints that are toggling a boolean flag on a record
  or deleting a record.


Automatic Notifications
-----------------------

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


Pagination
----------

Various endpoints will return a plethora of data. Therefore pagination has been enabled for them.
The endpoints that support pagination are easily recognizable because the response will include
a ``pagination`` key similar to this:


.. code-block:: json

    "pagination": {
        "next": "/api/cities/events/simple/2",
        "pages": 5,
        "prev": null,
        "total": 15
    }


- ``pages`` is the total number of pages available for the request criteria
- ``total`` is the total number of records found using the request criteria
- ``next`` is the URI to the next page of results. If you are already at the last page of
  results, this will be `null`.
- ``prev`` is the URI to the previous page of results. If you are already at the first page of
  results, this will be `null`.

Any endpoint that includes ``pagination`` in the response will **always** do so, regardless of
if the amount of records is below the per page limit. The default per page limit of records
returned is set in the application's configuration, and is generally set to ``25``. You can
override this default, having a custom number of records returned per page, by passing
``?per_page=<int>`` to any of the endpoints that support pagination. There is also a max
number of records returned, which is also set in the application's configuration and is
currently set to ``1000``.


Object Actions
--------------

In almost every response from the API, there is a ``_links`` key provided for each object with
actions that are available related to the object, the URL to hit and the HTTP method to use.
For example, in the following payload returned from logging in a user, there are a handful of
actions that are returned:

.. include:: _includes/responses/auth/login.rst

There are a mix of operations there, from creating a new artist profile
(``user._links.new-artist``) to deleting the user account (``user._links.delete``). While
interacting with the system, you will likely notice that within a single API response,
there could be some objects that have every possible action and other objects that have
only 1 or 2 actions, even when of the same type of object. This is simply due to user
permissions. If an action is not listed in the object's ``_links``, it is likely because
the current user does not have permission to complete the action for that object.


.. _Gemini: https://github.com/makemusicday/gemini
