---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "Woods Hole Oceanographic Institution"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "online"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "us"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the
latitude: "41"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-70"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "FIXME"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "FIXME"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2020-10-26      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2020-11-03        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Amber York", "Karen Soenen"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Stace Beaulieu", "helper two"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["adyork@whoi.edu","ksoenen@whoi.edu"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}


{% comment %}
8< ============= For a workshop delete from here =============
For a workshop please delete the following block until the next dashed-line
{% endcomment %}


<div class="alert alert-danger">
This is the workshop template. Delete these lines and use it to
<a href="https://carpentries.github.io/workshop-template/customization/index.html">customize</a>
your own website. If you are running a self-organized workshop or have not put
in a workshop request yet, please also fill in
<a href="{{site.amy_site}}/forms/self-organised/">this workshop request form</a>
to let us know about your workshop and our administrator may contact you if we
need any extra information.
</div>

{% comment %}
8< ============================= until here ==================
{% endcomment %}


{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
Check SWC curriculum
{% endcomment %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong> Participants must bring a laptop with a
  Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on. They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong>
{% if online == "false" %}
  We are committed to making this workshop
  accessible to everybody. The workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
{% else %}
  We are dedicated to providing a positive and accessible learning environment for all. Please
  notify the instructors in advance of the workshop if you require any accommodations or if there is
  anything we can do to make this workshop more accessible to you.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">Code of Conduct</h2>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>Please be sure to complete these surveys before and after the workshop.</p>
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.  Edit the items and times in the table
to match your plans.  You may also want to change 'Day 1' and 'Day
2' to be actual dates or days of the week.
{% endcomment %}
<h2 id="schedule">Schedule</h2>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% endif %}

<hr/>

{% comment %}
SYLLABUS

Show what topics will be covered.

1. If your workshop is R rather than Python, remove the comment
around that section and put a comment around the Python section.
2. Some workshops will delete SQL.
3. Please make sure the list of topics is synchronized with what you
intend to teach.
4. You may need to move the div's with class="col-md-6" around inside
the div's with class="row" to balance the multi-column layout.

This is one of the places where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}
<h2 id="syllabus">Syllabus</h2>

{% if site.carpentry == "swc" %}
{% include swc/syllabus.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/syllabus.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/syllabus.html %}
{% endif %}

<hr/>

{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in a
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to the software described below.
  In addition, you will need an up-to-date web browser.
</p>
<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instrucctions.
{% endcomment %}
{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.
{% endcomment %}

{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% endif %}

<h2 id="syllabus">Schedule & Syllabus</h2>


This workshop is based on a few workshops developed by the Carpentries (See <a href="https://carpentries.org">https://carpentries.org</a>  for more information about the Carpentries organisation.) and by Joe Futrelle (WHOI):
<ul>
  <li><a href=" https://datacarpentry.org/spreadsheet-ecology-lesson/">Data Organization in Spreadsheets for Ecologists</a></li>
  <li><a href="https://datacarpentry.org/python-ecology-lesson/">Data Analysis and Visualization for Ecologists</a></li>
  <li><a href="https://github.com/WHOIGit/pandas-talk/">Python and the Pandas package-Joe Futrelle (WHOI)</a></li>
</ul>

<br>
    
<h3>Part 1. Preparing your table - Best practices</h3>
 <table class="table table-striped">
  <col style="width:5%">
	<col style="width:15%">
	<col style="width:30%">
  <col style="width:15%">
  <col style="width:35%">
   <tr> 
    <td>TIME</td>  
    <td>SUBJECT</td> 
    <td>TOPICS COVERED</td> 
    <td>NOTEBOOK/EXERCISE</td>
    <td>MORE RESOURCES</td>
   </tr>
   <tr> 
    <td>08:45</td>  
    <td>Introduction</td> 
    <td></td> 
    <td></td>
    <td></td>
   </tr>
   <tr> 
     <td>09:00</td>  
     <td>Formatting data tables in Spreadsheets</td> 
     <td>How do we format data in spreadsheets for effective data use?</td> 
     <td></td>
     <td><a href="https://datacarpentry.org/spreadsheet-ecology-lesson/01-format-data/index.html">Carpentries: data table </a></td>
  </tr>
  <tr> 
    <td>09:10</td>  
    <td>Excercise</td>       
    <td>How can this table be improved to start analysis in python? Excercise in breakout rooms</td>
    <td><a href="https://ndownloader.figshare.com/files/2252083">Datatable for exercise</a></td>
    <td><a href="https://datacarpentry.org/spreadsheet-ecology-lesson/02-common-mistakes/index.html">Carpentries exercise and discussion </a></td>
  </tr>
  <tr> 
    <td>09:35</td>  
    <td>Date Notation</td> 
    <td>Good approaches for handling dates in spreadsheets</td> 
    <td></td>
    <td><a href="https://datacarpentry.org/spreadsheet-ecology-lesson/03-dates-as-data/index.html">Carpentries: Dates</a></td>
  </tr>
  <tr> 
    <td>09:45</td>  
    <td>Break</td> 
    <td>15 minute break</td> 
    <td></td>
    <td></td>
  </tr>
 </table>
 
 <br>
 
<h3>Part 2. Python and the Pandas library</h3>
 <table class="table table-striped">
  <col style="width:5%">
	<col style="width:15%">
	<col style="width:30%">
  <col style="width:15%">
  <col style="width:35%">
  <tr> 
    <td>TIME</td>  
    <td>SUBJECT</td> 
    <td>TOPICS COVERED</td> 
    <td>NOTEBOOK/EXERCISE</td>
    <td>MORE RESOURCES</td>
   </tr>
   <tr> 
        <td>10:00</td>  
        <td>Starting with Python</td> 
        <td>What is Python?<br/>Data types<br/>Mathematical operations<br/>Lists</td> 
        <td><a href="https://github.com/k-rns/2020-05-22-WHOI-online/blob/gh-pages/data/01_Python%20Basics.ipynb">Notebook: Starting with Python</a></td>
        <td><a href="https://datacarpentry.org/python-ecology-lesson/00-before-we-start/index.html">Carpentries: Intro to Python I</a><br><a href="https://datacarpentry.org/python-ecology-lesson/01-short-introduction-to-Python/index.html">Carpentries: Intro to Python II</a><br/><a href="https://github.com/WHOIGit/pandas-talk/blob/master/01%20introduction%20to%20python.ipynb">First commands, Notebook Joe Futrelle, WHOI</a></td>
    </tr>
    <tr> 
        <td>10:20</td>  
        <td>The Pandas Library</td>
        <td>What is Pandas?<br/>How do I import data<br/>What is a dataframe?<br/>How can I access specific data within my data set?</td>
        <td><a href="https://github.com/k-rns/2020-05-22-WHOI-online/blob/gh-pages/data/02_Pandas_DataFrames_Series.ipynb">Notebook: The Pandas Library</a></td>
        <td><a href="https://datacarpentry.org/python-ecology-lesson/02-starting-with-data/index.html">Carpentries: Starting with data</a><br/><a href="https://datacarpentry.org/python-ecology-lesson/03-index-slice-subset/index.html">Carpentries: Indexing, Slicing and Subsetting DataFrames in Python</a><br/><a href="https://github.com/WHOIGit/pandas-talk/blob/master/04%20anatomy%20of%20a%20dataframe.ipynb">Anatomy of a DF, Notebook Joe Futrelle, WHOI</a></td>
    </tr> 
    <tr> 
        <td>10:35</td>  
        <td>Excercise</td> 
        <td></td> 
        <td></td> 
        <td></td> 
   </tr>
   <tr> 
        <td>10:45</td>  
        <td>Break</td> 
        <td>15 minute break</td>
        <td></td> 
        <td></td> 
    </tr>
 </table>

<br> 
   
<h3>Part 3. Further manipulation of a data frame</h3>
 <table class="table table-striped">
  <col style="width:5%">
	<col style="width:15%">
	<col style="width:30%">
  <col style="width:15%">
  <col style="width:35%">
  <tr> 
    <td>TIME</td>  
    <td>SUBJECT</td> 
    <td>TOPICS COVERED</td> 
    <td>NOTEBOOK/EXERCISE</td>
    <td>MORE RESOURCES</td>
   </tr>
   <tr> 
    <td>11:00</td>  
    <td>Further manipulation of a data frame</td> 
    <td>Sorting<br/>Unique values<br/>Logical conditions<br/>Summary statistics<br/>Groups<br/>Merging dataframes</td>
    <td><a href="https://github.com/k-rns/2020-05-22-WHOI-online/blob/gh-pages/data/03_Data_Manipulation.ipynb">Notebook: Further manipulation of a dataframe</a></td> 
     <td>
       <a href="https://datacarpentry.org/python-ecology-lesson/02-starting-with-data/index.html">Carpentries: Statistics, groups and basic math</a>
       <br/><a href="https://datacarpentry.org/python-ecology-lesson/05-merging-data/index.html">Carpentries: Merging data</a>
       <br/><a href="https://github.com/WHOIGit/pandas-talk/blob/master/05%20querying%20and%20merging%20dataframes.ipynb">Querying and merging DFs, Notebook Joe Futrelle, WHOI</a> 
     </td> 
   </tr>
   <tr> 
     <td>11:30</td>  
     <td>Excercise</td> 
     <td></td>
     <td></td> 
     <td></td> 
   </tr>
 
   <tr> 
    <td>11:45</td>  
    <td>Break</td> 
    <td>15 minute break</td> 
    <td></td>
    <td></td> 
   </tr>
   <tr> 
    <td>12:00</td>  
    <td>Questions?</td> 
    <td></td> 
    <td></td>
    <td></td>
   </tr>
   <tr> 
     <td>12:15</td>  
     <td>Wrap-up</td> 
     <td></td> 
     <td></td> 
     <td></td> 
   </tr>
  </table>
<br> 
<h3>Part 4. Extras</h3> 
<ul>
  <li> <a href='http://queirozf.com/entries/pandas-dataframe-plot-examples-with-matplotlib-pyplot'>Plotting</a></li>
  <li> <a href='https://datatofish.com/export-dataframe-to-csv/'>Exporting dataframes</a></li>
  <li> <a href='https://github.com/WHOIGit/pandas-talk/blob/master/07%20pandas%20handling%20time%20series%20data.ipynb'>Handling time series, Joe Futrelle, WHOI</a></li>
  <li> <a href='http://datacamp-community-prod.s3.amazonaws.com/dbed353d-2757-4617-8206-8767ab379ab3'>Python for data science cheat sheet</a></li>
</ul>
<hr/>

{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.


  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  
  {% if site.carpentry == "swc" %}
  {% include swc/setup.html %}
  {% elsif site.carpentry == "dc" %}
  {% include dc/setup.html %}
  {% elsif site.carpentry == "lc" %}
  {% include lc/setup.html %}
  {% endif %}
  {% endcomment %}

<h2 id="setup">Setup</h2>
<p>
  To participate in this workshop, you will need an up-to-date web browser and access access to a spreadsheet program (Excel, LibreOffice,...), Python and Jupyter notebooks. In addition you will need an up-to-date web browser. 
</p>
<p> You only need to install these programs:
  <ul>
    <li>A spreadsheet program (Excel is fine, or you can install the open source software LibreOffice)</li>
    <li>Python and Jupyter notebooks using Anaconda: <a href="https://www.anaconda.com/products/individual#download-section">https://www.anaconda.com/products/individual#download-section</a>  (python 3.7)</li>
   </ul>
Detailed set-up instructions for your software can be found <a href="https://datacarpentry.org/ecology-workshop/setup-python-workshop.html">here</a> (Instructions from Data Carpentry Ecology workshops-with Python). But only install a spreadsheet program and python and Jupyter notebooks (through Anaconda).   
</p>

<p>
  Please make sure you have installed all the required packages before the start of this workshop. We will be holding an on-line data lab with Stace Beaulieu on May 20 and can help you install the packages if necessary. </p>
  

<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>
