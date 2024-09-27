# Project Overview

The overarching settings and urls are noted in the `settings.py` and `urls.py` in the `app` (in this case, isoVisDev) subfolder. 

```plaintext
isoVisDev/
|
├── manage.py
|
└── isoVisDev/
	|
    ├── asgi.py
    |
    ├── settings.py      # overview settings
    |
    ├── urls.py          # overview urls
    |
    └── wsgi.py
```

These two files need to be configured correctly before developing the project. 

## Base structure and style

To generate the base structure (i.e. the tabs and individual pages) and set-up the design, create a new folder called <span class="button">templates</span>, and generate two files in the folder (`base.html` and `home.html`):

```plaintext
isoVisDev/
|
├── manage.py
|
└── isoVisDev/
|	|
|   ├── asgi.py
|   |
|   ├── settings.py      # overview settings
|   |
|   ├── urls.py          # overview urls
|   |
|   └── wsgi.py
|
└── templates
	|
	├── base.html
	|
	└── home.html
```
