# Basic commands

<span class="code">python manage.py runserver</span>.<br>
<div style="margin-left: 20px;">For running the Django application</div>

<span class="code">python manage.py makemigrations</span><br>
<div style="margin-left: 20px;">Updates changes made in the <code>models.py</code>. Version control of the changes are documented in the <code>migrations</code> folder.</div>

<span class="code">python manage.py makemigrations expression </span><br>
<div style="margin-left: 20px;">Update changes made in the <code>models.py</code> for a tab within the app, named <code>expression</code>.</div>

<span class="code">python manage.py migrate</span><br>
<div style="margin-left: 20px;"> Ran after <code>python manage.py makemigrations</code> and applies the migrations to the database, effectively updating the database schema to match current models.</div>

<span class="code">python manage.py <python.script></span><br>
<div style="margin-left: 20px;"> Run <code>python script</code>, which may upload a csv file to the database </div>

