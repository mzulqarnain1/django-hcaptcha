===============
Django hCaptcha
===============

*A fork of django-hCaptcha by Andrej Zbín, Modified for Django 1.10 for hCaptcha support in legacy systems*

Django-110-hCaptcha provides a simple way to protect your django 1.10 forms using `hCaptcha <https://www.hcaptcha.com/>`_.

Configuration
-------------

Add "django-hcaptcha" to your INSTALLED_APPS setting like this::

    INSTALLED_APPS = [
        ...
        'hcaptcha',
    ]

For development purposes no further configuration is required. By default, django-hCaptcha will use dummy keys.

For production, you'll need to obtain your hCaptcha site key and secret key and add them to you settings::

    HCAPTCHA_SITEKEY = '<your sitekey>'
    HCAPTCHA_SECRET = '<your secret key>'


You can also configure your hCaptcha widget globally (`see all options <https://docs.hcaptcha.com/configuration>`_)::

    HCAPTCHA_DEFAULT_CONFIG = {
        'onload': 'name_of_js_function',
        'render': 'explicit',
        'theme': 'dark',  # do not use data- prefix
        'size': 'compact',  # do not use data- prefix
        ...
    }

If you need to, you can also override default hcaptcha endpoints::


    HCAPTCHA_JS_API_URL = 'https://hcaptcha.com/1/api.js'
    HCAPTCHA_VERIFY_URL = 'https://hcaptcha.com/siteverify'

Use proxies::

     HCAPTCHA_PROXIES = {
        'http': 'http://127.0.0.1:8000',
     }

Change default verification timeout::

    HCAPTCHA_TIMEOUT = 5



Usage
-----------

Simply add hCaptchaField to your forms::

    from hcaptcha.fields import hCaptchaField

    class Forms(forms.Form):
        ....
        hcaptcha = hCaptchaField()
        ....

You can override default config by passing additional arguments::

    class Forms(forms.Form):
        ....
        hcaptcha = hCaptchaField(theme='dark', size='compact')
        ....

