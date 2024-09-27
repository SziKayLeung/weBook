# Add module

To create a `module` or `app` within the Django application, i.e <span class="search">www.isoforms.com/expression/</span>, a separate folder called `expression` needs to be created in the main folder, with all the other template htmls.

To integrate this to the existing Django application:

1. Open the [Windows command prompt](../Deployment/installation.md) and change directory to the project folder. 

2. Create the module `expression` 
	```shell
	cd C:\Users\sl693\Dropbox\Scripts\isoVisDev
	python manage.py startapp expression 
	```
	This command will create the following structure:
	```plaintext
	isoVisDev/
	└── expression/
	    ├── migrations/
	    ├── __init__.py
	    ├── admin.py
	    ├── apps.py
	    ├── models.py
	    ├── tests.py
	    └── views.py
	```

3. Link the module to the Django app
   The module needs to be registered in the `settings.py` and `urls.py` in the main folder.
   ```plaintext
	isoVisDev/
	├── manage.py
	└── isoVisDev/
	    ├── asgi.py
	    ├── settings.py      # modify this
	    ├── urls.py          # modify this
	    └── wsgi.py
	└── expression/
	    ├── migrations/
	    ├── __init__.py
	    ├── admin.py
	    ├── apps.py
	    ├── models.py
	    ├── tests.py
	    └── views.py
	```
   
   In the <span class="code">settings.py</span>, add the module to the <span class="code">INSTALLED_APPS</span>, as described [here](djangoSettings.md).

   In the <span class="code">urls.py</span>, include the urls to the <span class="code">urlpatterns</span>, as described [here](djangoUrls.md).

4. Modify the <span class="code">views.py</span>
   Add the below to the `view.py`. The <span class="search">www.isoforms.com/expression</span> will automatically direct to the `home.html` page defined in the main [app](djangoTemplates.md).

	```python
	# expression/views.py

	from django.shortcuts import render, redirect, get_object_or_404
	from django.http import JsonResponse
	from django.urls import reverse

	def home(request):
    	return render(request, 'home.html')

	```

5. Create other pages within this module 
   Create a new file called `urls.py` and define the other url paths:

   ```python
	from django.urls import path
	from . import views

	app_name = 'expression'
	urlpatterns = [
		path('', views.summary, name='main'),
		path('summary/', views.summary, name= 'summary'),
		path('transcript/', views.transcript_identify, name= 'transcript')
	]
   ```
   Notes:
   	- The module name here is called `expression`.
   	- the `views.summary` refers to the `def summary()` in the `expression/view.py`, which can be accessed with <span class="search">www.isoforms.com/expression.summary</span>


6. Run migrations

	Finalise the module, by typing the following  in the Windows terminal:
	```shell
	cd C:\Users\sl693\Dropbox\Scripts\isoVisDev
	python manage.py makemigrations expression
	python manage.py migrate
	```