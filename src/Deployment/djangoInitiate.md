## Create django project and environment 

On the Windows terminal:

1. In the destination folder, create and activate the environment:
    ```shell
    # change directory to folder
    cd C:\Users\sl693\Dropbox\Scripts

    # create environment
    python -m venv isoVis_env

    # activate environment
    isoVis_env\Scripts\activate
    ```

2. Install packages to run Django using pip (and any others for plotting etc)
    ```shell
    # install Django
    pip install Django

    # others
    pip install django-import-export
    pip install pandas
    pip install matplotlib
    pip install seaborn
    pip install plotly
    ```

3. Initiate the django project:
   ```shell
   django-admin startproject isoVisDev 
   ```
   > **Note:** Here isoVisDev is the name of the project. Replace "isoVisDev" with the name of project.

   This will create the following folder and structure:
    ```markdown
    isoVisDev
    ├───manage.py    
    └───isoVisDev
         ├───asgi.py
         ├───settings.py
         ├───urls.py
         └───wsgi.py 
    ```

4. Create a requirements.txt (for installing the environment on AWS). The requirements.txt lists all the packages installed in the environment.
   ```shell
   cd isoVisDev
   python manage.py runserver
   pip freeze > requirements.txt
   ```
   The requirements.txt will be in the isoVisDev folder as shown in the tree structure below:
   ```markdown
    isoVisDev
    ├───manage.py
    ├───requirements.txt
    └───isoVisDev  
   ```


5. Create a configuration file for django in the .ebextensions folder.  
   ```shell
   mkdir .ebextensions
   deactivate
   ```
   Manually create the djang.config and copy the following text in the file: 
   ```yaml
   option_settings:
   aws:elasticbeanstalk:container:python:
   WSGIPath: isoVisDev.wsgi:application
   ```
   > **Important:** Ensure that the WSGIPath is updated to the name of the app (isoVisDev.wsgi refers to the wsgi.py script in the isoVisDev folder)
   Note the updated folder structure:
   ```markdown
    isoVisDev
    ├───manage.py
    ├───requirements.txt
    ├───.ebextensions
    │     └───django.config
    └───isoVisDev

   ```
