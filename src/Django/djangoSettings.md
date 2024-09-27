# Project settings

The `settings.py` file holds the configuration settings for the Django application, and only needs to be configured at the start of the project. 

While the `django-admin` will create the basic template of the file, there are a few things that need to be updated accordingly:


1. **Allowed Hosts** 

   <span class="code">ALLOWED_HOSTS</span>: A list of strings representing the host/domain names for the Django app. 
   > **Note**: This is empty in the template, and needs to include the Elastic Beanstalk domain and the preferred domain name. 

	```python
	ALLOWED_HOSTS = ['isoforms.com','www.isoforms.com','127.0.0.1','isoVis-deploy-env.eba-r7r9zsja.eu-north-1.elasticbeanstalk.com']
	```

2. **Apps** 

	<span class="code">INSTALLED_APPS</span>: A list of the sub-applications created (i.e expression here), and third-party apps 
	> **Note**: `expression.apps.expressionConfig`: needs to be an `app.py` in the `expression` folder. 
	```python
	INSTALLED_APPS = [
		#### In template
	    'django.contrib.admin',  
	    # Built-in admin interface
	    'django.contrib.auth',         					
	    # Authentication framework
	    'django.contrib.contenttypes', 					
	    # Content type framework
	    'django.contrib.sessions',      				
	    # Session framework
	    'django.contrib.messages',     					
	    # Messaging framework
	    'django.contrib.staticfiles',   				
	    # Static file handling

	    ### Added by user
	    # Your custom app
	    'expression.apps.expressionConfig',     
	    # Third-party app for REST APIs        
	    'import_export',       					
	]
	```

3. **Language and Time Zone**

	Update this to the language and time zone as appropriate.
	```python
	LANGUAGE_CODE = 'en-gb'
	TIME_ZONE = 'Europe/London'
	```