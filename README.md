## Jupyter in UC Berkeley's data science education program

* This document provides a guided tour of information distributed across many web pages and GitHub repositories involved in running a live suite of data science courses at UC Berkeley.
* These valuable resources -- designed for and by UC Berkeley students, instructors, and other teaching and support staff -- are publicly available.
* This content should be of broad interest to diverse folks thinking about data science education, using Jupyter notebooks in the classroom, and/or deploying and scaling JupyterHub.

**Keywords: data science, UC Berkeley, undergraduate education, Jupyter notebooks, JupyterHub deployment**

### Who is this for?
* Designed for anyone who wants to learn about UC Berkeley's data science program but doesn't have an account on [data8.berkeley.edu](https://data8.berkeley.edu/)
* This snapshot is for folks at [JupyterDays Boston 2016](http://blog.jupyter.org/2016/02/16/jupyterdays-boston-2016/) (March 17-18, 2016 in Cambridge, MA) -- hopefully provides plenty of materials to explore, fork, and hack on during Friday's coding and projects session

### What will you find here?
* An overview of the UC Berkeley's new data science education program
* Pointers to current course materials distributed as Jupyter notebooks
* An overview of the live JupyterHub-based infrastructure

## DATA 8: Foundations of Data Science

### Course overview
* Teaches computational and inferential (statistical) thinking through interaction with real data
* Pilot run in Fall 2015 with ~80 students
* Current Spring 2016 enrollment at ~470 students
* Three 50 min lectures + 2 hour computer lab session per week
* Enriched by a suite of connector courses teaching diverse subjects through the lens of data science

### Design requirements
* Must be accessible to all incoming first-years at UC Berkeley
* Assume no computer science background and only high school algebra
* Get students immediately interacting with data programmatically
* Can't require students to figure out a local installation -- too huge a barrier

### Implementation
* Jupyter notebooks + JupyterHub support a solution satisfying all design requirements

* Why Jupyter notebooks?
    * Provide a natural environment for introducing data science skills to students
    * Let students develop an explicit computational narrative with data
    * Interactive online substrate for the course textbook and computer labs

* Why JupyterHub?
    * Multi-user server for Jupyter notebooks can support many users (students, instructors, teaching staff)
    * Enables browser-based interface to computation in the cloud -- students only need a browser to start programming, interacting with data, and creating a visible record of their analytical steps

### Course website: [data8.org](https://data-8.appspot.com/sp16/course)

* [Syllabus + links to lecture videos](https://data-8.appspot.com/sp16/course)
    * An overview of data science
    * Using Python to manipulate information in a table data structure
    * Interpreting and exploring data through visualizations
    * Sampling: Understanding the behavior of random selection
    * Making predictions from data
    * Inference: Reasoning about populations by computing over samples
    * Models: Making assumptions and exploring their consequences

* [data8.org](https://data-8.appspot.com/sp16/course) is primarily a student-facing website and its links to computer lab assignments will **not** work for anyone who doesn't have a course account
* We'll show you everything that goes into making these links work for students and how to find the underlying source materials hosted on GitHub across various repositories belonging to the [data-8 organization](https://github.com/data-8)

### Online textbook: [www.inferentialthinking.com](http://www.inferentialthinking.com/)

![textbook](/screenshots/textbook.png)

[textbook github repo](https://github.com/data-8/textbook)

    git clone https://github.com/data-8/textbook.git

[DS8-Interact github repo](https://github.com/data-8/DS8-Interact)

    git clone https://github.com/data-8/DS8-Interact.git

### Computer lab assignments are Jupyter notebooks

[data8assets github repo](https://github.com/data-8/data8assets)

    git clone https://github.com/data-8/data8assets.git

## JupyterHub deployment

    git clone https://github.com/data-8/jupyterhub-deploy.git

* The [JupyterHub deployment for DATA 8](https://github.com/data-8/jupyterhub-deploy) is based on [Jessica Hamrick](http://www.jesshamrick.com/)'s [jupyterhub-compmodels-deploy](https://github.com/compmodels/jupyterhub-deploy) for a UC Berkeley course, Computational Models of Cognition (COGSCI 131)

* See Jessica's blog post at Rackspace on [Deploying JupyterHub for Education](https://developer.rackspace.com/blog/deploying-jupyterhub-for-education/) and also her README at [jupyterhub-compmodels-deploy](https://github.com/compmodels/jupyterhub-deploy)

## Connector courses

* Suite of [connector courses](https://data-8.appspot.com/sp16/modules/extra_tabs/render?index=3) are taught in departments across campus and introduce diverse subjects through the lens of data science
* Spring 2016 has 11 connector courses: in ethics, cognitive science, geospatial data, probability & statistics, ecology, history, matrices & graphs, computational structures, health & human behavior, smart cities, literature
* Nearly all use Jupyter notebooks and the DATA 8 JupyterHub deployment
* Many connector instructors are new to Python and GitHub

## Technical challenges and possible future directions

### Scaling **up** to more students

* Adding users reveals bugs

### Scaling **out** to more classes

* A JupyterHub hub?

* A Dropbox-like interface to GitHub to help instructors with content management?
    * See the [design doc](https://github.com/elaine84/jupyter-synchronized-folders/blob/proposal/design.md) for an experiment called [jupyter-synchronized-folders](https://github.com/elaine84/jupyter-synchronized-folders)


## Other resources
* [jupyter-education Google Group](https://groups.google.com/forum/#!forum/jupyter-education)
* [JupyterHub Gitter channel](https://gitter.im/jupyter/jupyterhub)
