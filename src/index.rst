Gemini Music Event Matchmaking software
=======================================

Gemini_ was written to accomplish the goals of the `Make Music Alliance`_, specifically to enable
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

It was named Gemini_ in reference to the astrological sign that ends on June 21st, the yearly date
of `Make Music Day`_.

Both the Gemini_ code and this documentation_ are open source, and available on GitHub_.

This documentation is built using Sphinx_. Additionally, example code is provided in Python_,
but you are welcome to use whatever programming language that you wish to communicate with the API.


.. _Make Music Alliance: https://www.makemusicday.org
.. _Make Music Day: https://www.makemusicday.org
.. _Gemini: https://github.com/makemusicday/gemini
.. _documentation: https://github.com/makemusicday/gemini-docs
.. _GitHub: https://github.com
.. _Sphinx: https://www.sphinx-doc.org/en/master/
.. _Python: https://www.python.org/

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   contributing
   glossary
   general
   public-endpoints
   authentication
