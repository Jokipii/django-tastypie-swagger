Synopsis
========

**django-tastypie-swagger** is a small adapter library to construct Swagger_ documentation from Tastypie_ resources.

This package provides two things:

1. An embedded instance of `Swagger UI`_ to point a URL to.
2. Automatic `Resource Listing`_ and `API Declaration`_ generation that is consumed by #1


Usage
=====

Install package::

    pip install django-tastypie-swagger

Add to INSTALLED_APPS::

    INSTALLED_APPS = [
        ...

        'tastypie_swagger',

        ...
    ]

Include in your urlconf with **namespace** and **tastypie_api_module** parameter with its value being a path to a tastypie.api.Api instance.::

    urlpatterns = patterns('',
        ...

        url(r'api/doc/', include('tastypie_swagger.urls', namespace='tastypie_swagger'), {'tastypie_api_module': 'mainsite.urls.api'}),

        ...
    )


Swagger documentation will be served up at the URL you configured.


Detecting required fields
-------------------------

Tastypie 0.9.11 **ModelResource** fields do not respect the *blank* attribute on django model fields, which this library depends on to determine if a field is required or not.

You can use `this ModelResource subclass <https://gist.github.com/4041352>`_ as a workaround to this issue.





.. _Swagger: http://swagger.wordnik.com/
.. _Tastypie: https://django-tastypie.readthedocs.org
.. _Resource Listing: https://github.com/wordnik/swagger-core/wiki/Resource-Listing
.. _API Declaration: https://github.com/wordnik/swagger-core/wiki/API-Declaration
.. _Swagger UI: https://github.com/wordnik/swagger-ui
.. _tastypie.api.Api: https://django-tastypie.readthedocs.org/en/latest/api.html
