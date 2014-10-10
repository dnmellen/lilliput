lilliput
========

Django URL shortener based in Django 1.7

How it works
------------

It's really simple. Links are model objects, each object has an auto-incremental primary key is converted to another 'number' in base 64.
Writing numbers in this fashion allows to represent billions of URLs using just 4 chars.

Shortening URLs
---------------


.. code-block :: python

    import requests

    r = requests.post(
        'http://yourshortenerserver.com/api/links/',
        data={'original_url': "http://www.django-rest-framework.org/api-guide/routers"},
        headers={'Authorization': "Token 9fe1d43feb6902ce6858ca9665a22ff5ef13eaa"}
    )

    # r.content output
    '{
        "original_url": "http://www.django-rest-framework.org/api-guide/routers",
        "short_url": "http://yourshortenerserver.com/9",
        "hash": "9",
        "created_at": "2014-10-10T08:02:39.510Z",
        "updated_at": "2014-10-10T08:02:39.514Z"
     }'