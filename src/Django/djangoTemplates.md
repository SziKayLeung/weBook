# Templates

The templates folder creates the backbone of the dynamic HTML pages. There are two files:

```plaintext 
isoVisDev/
├── manage.py
└── isoVisDev/
|   ├── asgi.py
|   ├── settings.py      
|   ├── urls.py          
|   └── wsgi.py
└── templates
	├── base.html     # file 1
	└── home.html     # file 2
```


## <span class="code">base.html</span>

The code below in the `base.html` is used to create the style and tabs:

![bookmark](../Images/DjangoBookmark.jpg)

```html
{% raw %}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">

    <!-- INSERT ADITIONAL INFORMATION TO THE HEAD TAG HERE-->
    {% block head %}
    {% endblock%}

    
 </head>
  <body>
    <!-- BOOTSTRAP NAVBAR CODE -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="d-flex justify-content-between px-5 mx-auto" style="width: 90%;">
            <span class="navbar-text text-white">Long-Read Brain Transcriptome Dataset</span>
            <ul class="navbar-nav mr-auto">
                <li class="nav-item active">
                    <a class="nav-link active" href="{% url 'home' %}">Home</a>
                </li>
                <li class="nav-item active">
                    <a class="nav-link active" href="{% url 'expression:summary' %}">Summary</a>
                </li>
                <li class="nav-item active">
                    <a class="nav-link active" href="{% url 'expression:transcript' %}">Transcript Level</a>
                </li>
            </ul>
        </div>
    </nav>
    <!-- END OF NAVBAR CODE-->


    <div class="container-fluid mt-5" style="max-width: 80%">    
    <!-- INSERT THE CONTENT FROM SPECIFIC PAGES HERE-->
        {% block content %}
        {% endblock  %}
    </div>
    
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
  </body>
</html>
{% endraw %}
```

To create a new tab (i.e Contact), include the code with appropriate indentation:
```html
{% raw %}
<li class="nav-item active">
    <a class="nav-link active" href="{% url 'contact' %}">Contact</a>
</li>
{% endraw %}
```
The `contact.html` then needs to be placed in the same `templates` folder. 

>**Note**: `expresion:summary` and `expression:transcript` means that the `summary.url` and `transcript.url` are placed in the `expression\urls` folder, and those sites will be accessed through <span class="search">wwww.isoforms.com\expression\summary</span> and <span class="search">www.isoforms.com\expression\transcriptsummary</span>`


## <span class="code">home.html</span>

The code below in the `home.html` is used to create the homapage.

![bookmark](../Images/homepage.jpg)

```html
{% raw %}
{% extends 'base.html' %}
{% block content %}
<h1>Long read brain transcriptome dataset</h1>
<br>
We used long-read transcriptome sequencing to characterise the structure and abundance of full-length transcripts in the human cortex from donors aged 6 weeks post-conception to 83 years old. We identified thousands of novel transcripts, with dramatic differences in the diversity of expressed transcripts between prenatal and postnatal cortex. A large proportion of these previously uncharacterised transcripts have high coding potential, with corresponding peptides detected in proteomic data. Novel putative coding sequences are highly conserved and overlap de novo mutations in genes linked with neurodevelopmental disorders in individuals with relevant clinical phenotypes. Our findings underscore the potential of novel coding sequences to harbor clinically relevant variants, offering new insights into the genetic architecture of human disease. Our cortical transcript annotations are available as a resource to the research community via an online database

<br>
<br>
<br>
Please refer to <a href="https://www.biorxiv.org/content/10.1101/2024.09.09.612016v1"> Bamford et al. 2024 </a> and the 
<a href="https://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&lastVirtModeType=default&lastVirtModeExtraState=&virtModeType=default&virtMode=0&nonVirtPosition=&position=chr6%3A105273218%2D105403082&hgsid=2355395487_u493yeIu7Ry5BcMRNmxfUqkeKryA"> transcripts detected on UCSC Genome Browser</a>.

{% endblock  %}
{% endraw %}
```