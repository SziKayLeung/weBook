# Project urls

The project `urls.py` list routes URLs to views.


```python
# urls.py
from django.contrib import admin
from django.urls import path, include
from expression import views

urlpatterns = [
    path('', views.home, name='home'),
    path('admin/', admin.site.urls),
    path('expression/', include('expression.urls'))
]
```

### Description

<span class="code">from django.contrib import admin</span>
This imports the Django admin module to create the interfance for managing application's data.

<span class="code">urlpatterns[]</span>
List of all the URL patterns for Django application, i.e. `isoforms.com`, `isoforms.com\admin`, `isoforms.com\expression`

<span class="code">path('expression/', include('expression.urls'))</span>
Includes additional URL patterns from the expression.urls module (listed in the `expression\urls.py`)

>**NOTE**: Important to update the urlpatterns everytime a new module/sub-folder is added. 


### Adding new module
If adding a new module called `Structure`, the new `urls.py` would be:
```python
# urls.py
from django.contrib import admin
from django.urls import path, include
from expression import views

urlpatterns = [
    path('', views.home, name='home'),
    path('admin/', admin.site.urls),
    path('expression/', include('expression.urls')),
    path('structure/', include('structure.urls'))
]
```


