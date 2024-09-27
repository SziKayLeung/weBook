# Add files to database

In most uses of a web application, we will need to have a database where we can retrieve information. This is stored in the form of a SQLite database (`db.sqlite3`), which is referred in the <span class="code">DATABASES</span> in the `settings.py`.

The database can either be populated using the Django admin site or directly through the app by loading csv/txt files, as guided below:

## Set up
1. Deposit the `.csv` file in the apps folder, within the `files` directory (need to create directory). 

2. Create a `.py` script to load the csv file, within `management\commands` directory (need to create directories).
 
   An example of the folder structure:
   ```
   	isoVisDev/
   	├── manage.py
	└── expression/
		└── files/
			└── whole_gene_counts.csv   # deposit this csv file here 
		├── management/
			└── commands/
				└── load_gene_counts.py   # create this script 
	    ├── migrations/
	    ├── __init__.py
	    ├── admin.py
	    ├── apps.py
	    ├── models.py
	    ├── tests.py
	    └── views.py
  	```
  	In the `load_gene_counts.py` script:

  	```python
  	from csv import DictReader   
	from django.core.management import BaseCommand

	# Import the model 
	from expression.models import Genecounts

	class Command(BaseCommand):
	    # Show this when the user types help
	    help = "Loads data from whole_genecounts.csv"

	    def handle(self, *args, **options):
	    	            
	        # Show this before loading the data into the database
	        print("Loading gene counts data")

	        #Code to load the data into database
	        for row in DictReader(open('./expression/files/whole_genecounts.csv')):
	            Genecount=Genecounts(sampleID=row['sampleID'], geneName=row['geneName'], counts=row['counts'], group=row['group'], sex = row['sex']) 
	            Genecount.save()
	    
	    def __str__(self):
	        return self.title  
  	```