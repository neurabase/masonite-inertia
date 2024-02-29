# Installation

## Requirements

* masonite >= 4
* a Node.js environment

## Installation

Install the latest Inertia server-side adapter in your project

```
pip install inertia-masonite
```

Add `InertiaProvider` to your project

{% code title="config/providers.py" %}
```python
# ...
from masonite.inertia import InertiaProvider

PROVIDERS = [
    # ...

    # Third Party Providers
    InertiaProvider,
]
```
{% endcode %}

Add the Inertia middleware to your project.

{% hint style="warning" %}
It's important to put this middleware in your HTTP middleware and `EncryptCookies` in route middlewares
{% endhint %}

{% code title="config/middleware.py" %}
```python
from masonite.inertia import InertiaMiddleware
# ...
http_middleware = [
    #...,
    InertiaMiddleware,
]
route_middleware = {
    "web": [EncryptCookies, SessionMiddleware,...]
}
```
{% endcode %}

Finally you can (optionally) publish the package configuration file to your project if you want to change some configuration parameters:

```python
python craft package:publish inertia
```

You should now have a configuration file `inertia.py` in your project configuration folder.

You're ready to start working with Inertia !
