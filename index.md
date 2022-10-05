---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "University of Texas at Austin"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "Online"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "us"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for workshop location
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "3.25"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-97.75"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "Nov 2-4, 2022"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:00am - 1:00pm CDT"    # human-readable times for the workshop e.g., 9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)
startdate: "2022-11-02"      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: "2022-11-04"        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Emily Beagle","Meryl Brodsky","Dianna Morganti","Michael Shensky","Lydia Tressel"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Jeremy Thompson", "Ian Goodale", "Jessie Simpson", "Allyssa Guzman"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["meryl.brodsky@austin.utexas.edu"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---



{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-astronomy" or site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-astronomy</code>, <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
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

{% if site.pilot %}
This is a pilot workshop, testing out a lesson that is still under development. The lesson authors would appreciate any feedback you can give them about the lesson content and suggestions for how it could be further improved.
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
can use https://www.latlong.net/ to find the lat/long of an
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
  <h3>Where:</h3>
  Online
</p>
{% elsif online == "true_public" %}
<p id="where">
  <h3>Where:</h3>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  <!--If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.-->
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
  <h3>When:</h3>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS
Modify the block below if there are any special requirements.
{% endcomment %}


<p id="requirements">
  <h3>Requirements:</h3>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
  They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>



{% comment %}
REGISTRATION
Modify the block below to provide registration link.
{% endcomment %}


<p id="requirements">
  <h3>Registration:</h3>
  <p>If you are interested in attending, please complete the workshop registration form by clicking the button below.<br><div style="background-color:#bf5700; color:#ffffff; padding:8px;"><a href="https://utexas.zoom.us/meeting/register/tJYsce6vrD4tHNGt7Y7gHuCQmwrybT4MvVno" style="font-weight:bold">Register for Workshop</a></div>. Space in this workshop is limited, so if you are interested in attending please try to register as early as possible. Once the workshop is full, a waitlist will be created that will accept a limited number of additional registrants.</p>
</p>






{% comment %}
ACCESSIBILITY
Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}


<p id="accessibility">
  <h3>Accessibility:</h3>
{% if online == "false" %}
  We are committed to making this workshop
  accessible to everybody. The online workshop sessions will be conducted via Zoom and will have automated closed captioning enabled.
</p>
<p>
  If we can help making learning easier for
  you please get in touch (using contact details below) and we will
  attempt to provide them.
</p>
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
  <h3>Contact:</h3>
  Please email meryl.brodsky@austin.utexas.edu for more information.
</p>

<p id="roles">
  <h3>Roles:</h3>
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
{% if site.carpentry == "incubator" %}
<p><a href="{{ site.incubator_pre_survey }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.incubator_post_survey }}">Post-workshop Survey</a></p>
{% elsif site.incubator_pre_survey or site.incubator_post_survey %}
<div class="alert alert-danger">
WARNING: you have defined custom pre- and/or post-survey links for
a workshop not configured for The Carpentries Incubator
(the value of `curriculum` is not set to `incubator` in `_config.yml`).
Please comment out the `incubator_pre_survey` and `incubator_post_survey` fields
in `_config.yml` or, if this workshop is teaching a lesson in the Incubator,
change the value of `carpentry` to `incubator`.
</div>
{% else %}
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% endif %}

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="schedule">Schedule</h2>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% elsif site.carpentry == "incubator" %}
This workshop is teaching a lesson in [The Carpentries Incubator](https://carpentries-incubator.org/).
Please check [the lesson homepage]({{ site.incubator_lesson_site }}) for a list of lesson sections and estimated timings.
{% endif %}

{% comment %}
Edit/replace the text above if you want to include a schedule table.
See the contents of the _includes/custom-schedule.html file for an example of
how one of these schedule tables is constructed.
{% endcomment %}

{% if site.pilot %}
The lesson taught in this workshop is being piloted and a precise schedule is yet to be established. The workshop will include regular breaks. Please [contact the workshop organisers](#contact) if you would like more information about the planned schedule.
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

<h2 id="syllabus">Syllabus</h2>

{% if page.carpentry == "swc" %}
{% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
{% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
{% include lc/syllabus.html %}
{% endif %}

{% endcomment %}


<h2 id="syllabus">Syllabus</h2>

<div class="row">
  <div class="col-md-6">
    <h3 id="syllabus-ecology-spreadsheet">Data Organisation in Spreadsheets</h3>
    <ul>
      <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/00-intro/">Introduction</a></li>
      <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/01-format-data/">Formatting Data</a></li>
      <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/02-common-mistakes/">Common Formatting Problems</a></li>
      <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/03-dates-as-data/">Dates as Data</a></li>
      <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/04-quality-control/">Quality Control</a></li>
      <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/05-exporting-data/">Exporting Data</a></li>
    </ul>
  </div>
  <div class="col-md-6">
    <h3 id="syllabus-ecology-openrefine">Data Cleaning with OpenRefine</h3>
    <ul>
      <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/00-getting-started/">Introduction</a></li>
      <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/01-working-with-openrefine/">Working with OpenRefine</a></li>
      <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/02-filter-exclude-sort/">Filtering and Sorting</a></li>
      <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/03-numbers/">Examining Numeric Data</a></li>
      <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/04-scripts/">Generating Scripts</a></li>
      <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/05-save-export/">Exporting Data</a></li>
      <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/06-resources/">Other Resources</a></li>    </ul>
  </div>
<!--   <div class="col-md-6">
    <h3 id="syllabus-ecology-r">Introduction to R</h3>
    <ul>
      <li><a href="http://www.datacarpentry.org/R-ecology-lesson/00-before-we-start.html">Overview of R and RStudio</a></li>
      <li><a href="http://www.datacarpentry.org/R-ecology-lesson/01-intro-to-r.html">Introduction to R</a></li>
      <li><a href="http://www.datacarpentry.org/R-ecology-lesson/02-starting-with-data.html">Starting with Data</a></li>
      <li><a href="http://www.datacarpentry.org/R-ecology-lesson/03-dplyr.html">Manipulating Data Frames with <code>dplyr</code></a></li>
      <li><a href="http://www.datacarpentry.org/R-ecology-lesson/04-visualization-ggplot2.html">Data Visualisation with <code>ggplot2</code></a></li>
      <li><a href="http://www.datacarpentry.org/R-ecology-lesson/05-r-and-databases.html">Interacting with Databases with <code>dbplyr</code></a></li>
    </ul>
  </div> -->

  <div class="col-md-6">
    <h3 id="syllabus-ecology-python">Introduction to Python</h3>
    <ul>
      <li><a href="https://datacarpentry.org/python-ecology-lesson/00-before-we-start/index.html">Overview of Python</a></li>
      <li><a href="https://datacarpentry.org/python-ecology-lesson/02-starting-with-data/index.html">Starting with Data</a></li>
      <li><a href="https://datacarpentry.org/python-ecology-lesson/03-index-slice-subset/index.html">Manipulating Data Frames</a></li>
      <li><a href="https://datacarpentry.org/python-ecology-lesson/04-data-types-and-format/index.html">Data Types and Formats</a></li>
      <li><a href="https://datacarpentry.org/python-ecology-lesson/05-merging-data/index.html">Combining DataFrames</a></li>
      <li><a href="https://datacarpentry.org/python-ecology-lesson/06-loops-and-functions/index.html">Data Workflows and Automation</a></li>
      <!--<li><a href="https://datacarpentry.org/python-ecology-lesson/07-visualization-ggplot-python/index.html">Data Visualisation with <code>plotnine</code></a></li>-->
      <li><a href="https://datacarpentry.org/python-ecology-lesson/08-putting-it-all-together/index.html">Data Visualisation with <code>matplotlib</code></a></li>
      <!--<li><a href="https://datacarpentry.org/python-ecology-lesson/09-working-with-sql/index.html">Interacting with Databases with <code>pandas</code></a></li>-->
    </ul>
  </div>
<!--
  <div class="col-md-6">
    <h3 id="syllabus-ecology-sql">Data Management with SQL</h3>
    <ul>
      <li><a href="https://datacarpentry.org/sql-ecology-lesson/00-sql-introduction/index.html">Introduction to SQL</a></li>
      <li><a href="https://datacarpentry.org/sql-ecology-lesson/01-sql-basic-queries/index.html">Basic Queries</a></li>
      <li><a href="https://datacarpentry.org/sql-ecology-lesson/02-sql-aggregation/index.html">SQL Aggregation and Aliases</a></li>
      <li><a href="https://datacarpentry.org/sql-ecology-lesson/03-sql-joins/index.html">Joins</a></li>
    </ul>
  </div>
-->
</div>













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
  you will need access to software as described below.
  In addition, you will need an up-to-date web browser.
</p>
<p>
  A list of common issues that occur during installation is provided as a reference at
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>. You can also find additional details about preparing for the spreadsheet and OpenRefine portions of the workshop at <a href="https://datacarpentry.org/ecology-workshop/setup-python-workshop.html">https://datacarpentry.org/ecology-workshop/setup-python-workshop.html</a>. If you visit either of these webpages, please ignore the “Anaconda” and “Python” sections since we will alternatively be using the Google Colab development environment in this workshop. <br><br>
 We will also have a virtual software installation session that will be conducted via Zoom from 3pm to 4pm on Tuesday November 1st (the day prior to the first day of the workshop). During this session workshop registrants will have the opportunity to ask questions and receive help getting the required software ready on their computers.
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


{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% elsif site.carpentry == "incubator" %}
Please check the "Setup" page of
[the lesson site]({{ site.incubator_lesson_site }}) for instructions to follow
to obtain the software and data you will need to follow the lesson.

{% endif %}
{% endcomment %}

<div id="openrefine"> {% comment %} Start of 'OpenRefine' section. {% endcomment %}
  <h3>OpenRefine</h3>
  <p>
    For this lesson you will need <em>OpenRefine</em> and a
    web browser. <em>Note:</em> this is a Java program that runs on your machine (not in the cloud).
    It runs inside a web browser, but no web connection is needed. In addition to having OpenRefine installed, you will need to download the following data file to your computer <a href="https://ndownloader.figshare.com/files/7823341" style="font-weight:bold">https://ndownloader.figshare.com/files/7823341</a> because we will be working with this data in OpenRefine during the workshop.
  </p>
  <br>
  <div>
    <ul class="nav nav-tabs nav-justified" role="tablist">
      <li role="presentation" class="active"><a data-os="windows" href="#openrefine-windows" aria-controls="Windows" role="tab" data-toggle="tab">Windows</a></li>
      <li role="presentation"><a data-os="macos" href="#openrefine-macos" aria-controls="MacOS" role="tab" data-toggle="tab">MacOS</a></li>
      <li role="presentation"><a data-os="linux" href="#openrefine-linux" aria-controls="Linux" role="tab" data-toggle="tab">Linux</a></li>
    </ul>

    <div class="tab-content">
      <article role="tabpanel" class="tab-pane active" id="openrefine-windows">
        <p>
          Check that you have either the Firefox or the Chrome browser installed and set as your default browser.
          <strong>OpenRefine runs in your default browser.</strong>
          It will not run correctly in Internet Explorer.
        </p>
        <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a></p>
        <p>Create a new directory called OpenRefine.</p>
        <p>Unzip the downloaded file into the OpenRefine directory by right-clicking and selecting "Extract ...". </p>
        <p>Go to your newly created OpenRefine directory.</p>
        <p>Launch OpenRefine by clicking <code>openrefine.exe</code> (this will launch a command prompt window, but you can ignore that - just wait for OpenRefine to open in the browser).</p>
        <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="openrefine-macos">
        <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong> It may not run correctly in Safari.</p>
        <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
        <p>Create a new directory called OpenRefine.</p>
        <p>Unzip the downloaded file into the OpenRefine directory by double-clicking it.</p>
        <p>Go to your newly created OpenRefine directory.</p>
        <p>Launch OpenRefine by dragging the icon into the Applications folder.</p>
        <p>Use <code>Ctrl-click/Open ... </code> to launch it.</p>
        <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
      </article>
      <article role="tabpanel" class="tab-pane active" id="openrefine-linux">
        <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong></p>
        <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
        <p>Make a directory called OpenRefine.</p>
        <p>Unzip the downloaded file into the OpenRefine directory.</p>
        <p>Go to your newly created OpenRefine directory.</p>
        <p>Launch OpenRefine by entering <code>./refine</code> into the terminal within the OpenRefine directory.</p>
        <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
      </article>
    </div>
  </div>
</div> {% comment %} End of 'OpenRefine' section. {% endcomment %}



<h3>Check to confirm that you can use Python in Google Colab</h3>
Visit <a href="https://colab.research.google.com/">https://colab.research.google.com/</a> and click <b>Sign In</b> at the top right of the page and log in with your @utexas.edu Google Account credentials. Once you are signed in, try clicking on the <b>File</b> button at the top left of the page and the select <b>New Notebook</b>. If a new Google Colab Notebook loads successfully for you, you have everything you need in place for the start of the workshop.


<h3>Install the videoconferencing client</h3>

If you haven't used Zoom before, go to the official website to download and install the Zoom client for your computer.
Set up your workspace

Like other Carpentries workshops, you will be learning by "coding along" with the Instructors. To do this, you will need to have both the window for the tool you will be learning about (a terminal, RStudio, your web browser, etc..) and the window for the Zoom video conference client open. In order to see both at once, we recommend using one of the following set up options:
<ul>
<li>Two monitors: If you have two monitors, plan to have the tool you are learing up on one monitor and the video conferencing software on the other.</li>
<li>Two devices: If you don't have two monitors, do you have another device (tablet, smartphone) with a medium to large sized screen? If so, try using the smaller device as your video conference connection and your larger device (laptop or desktop) to follow along with the tool you will be learning about.</li>
<li>Divide your screen: If you only have one device and one screen, practice having two windows (the video conference program and one of the tools you will be using at the workshop) open together. How can you best fit both on your screen? Will it work better for you to toggle between them using a keyboard shortcut? Try it out in advance to decide what will work best for you.</li>
</ul>

This blog post includes detailed information on how to set up your screen to follow along during the workshop.

The setup instructions for the Data Carpentry Social Sciences workshops (with R) can be found at the workshop overview site. 

