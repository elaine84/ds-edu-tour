## Jupyter in UC Berkeley's data science education program

* This document provides a guided tour of information distributed across many web pages and GitHub repositories involved in running a live suite of data science courses at the University of California, Berkeley.
* These valuable resources -- designed for and by UC Berkeley students, instructors, and other teaching and support staff -- are publicly available.
* This content should be of broad interest to diverse folks thinking about data science education, using Jupyter notebooks in the classroom, and/or deploying and scaling JupyterHub.

**Keywords: data science, UC Berkeley, undergraduate education, Jupyter notebooks, JupyterHub deployment**

### Who is this for?
* Designed for anyone who wants to learn about UC Berkeley's data science program but doesn't have an account on [data8.berkeley.edu](https://data8.berkeley.edu/)
* This snapshot is for folks at [JupyterDays Boston 2016](http://blog.jupyter.org/2016/02/16/jupyterdays-boston-2016/) (March 17-18, 2016 in Cambridge, MA) -- hopefully provides plenty of materials to explore, fork, and hack on

### What will you find here?
* An overview of the UC Berkeley's new data science education program
* Pointers to current course materials distributed as Jupyter notebooks
* An overview of the live JupyterHub-based infrastructure

### Some dependencies
* All course content and software is viewable online
* You'll need a [GitHub](https://github.com/) account if you want to clone or fork this content
* Course content is distributed as Jupyter notebooks that have several Python dependencies
    * [Python 3](https://www.python.org/downloads/) and [Jupyter](http://jupyter.readthedocs.org/en/latest/install.html)
    * The [datascience](https://pypi.python.org/pypi/datascience/) Python package

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
    * Interactive substrate for the online course textbook and computer lab assignments

* Why JupyterHub?
    * Multi-user server for Jupyter notebooks can support many users (students, instructors, teaching staff)
    * Enables browser-based interface to computation in the cloud -- students only need a browser to start programming, interacting with data, and creating a visible record of their analytical steps

### Course website: [data8.org](https://data-8.appspot.com/sp16/course)

![data8-sp16](screenshots/data8-sp16.png)

* [Syllabus + links to lecture videos](https://data-8.appspot.com/sp16/course)
    * An overview of data science
    * Using Python to manipulate information in table data structures
    * Interpreting and exploring data through visualizations
    * Sampling: Understanding the behavior of random selection
    * Making predictions from data
    * Inference: Reasoning about populations by computing over samples
    * Models: Making assumptions and exploring their consequences

* [data8.org](https://data-8.appspot.com/sp16/course) is primarily a student-facing website and its links to computer lab assignments will **not** work for anyone who doesn't have a course account
* We'll show you everything that goes into making these links work for students and how to find the underlying source materials hosted on GitHub across various repositories of the [data-8 organization](https://github.com/data-8)

### Online textbook: [www.inferentialthinking.com](http://www.inferentialthinking.com/)

![textbook](screenshots/textbook.png)

Alternatively: [view the textbook on GitBooks](https://ds8.gitbooks.io/textbook/content/)

Most sections of the online textbook begin with a big blue Interact button ([example section](http://www.inferentialthinking.com/chapter3/sampling.html))

![textbook-interact](screenshots/textbook-interact.png)

When a student clicks the Interact button, they are redirected to a Jupyter notebook containing an interactive version of the textbook content!

![textbook-interact-jupyterhub](screenshots/textbook-interact-jupyterhub.png)

#### What's going on?

* First, we'll explain where the source material is
* Second, we'll explain the Interact button

#### [The textbook is hosted in a GitHub repo](https://github.com/data-8/textbook)

    git clone https://github.com/data-8/textbook.git

* Most of the underlying source material for the textbook is written in Jupyter notebooks ([example notebook](https://github.com/data-8/textbook/blob/gh-pages/notebooks/Sampling.ipynb))
* [GitBook](https://www.gitbook.com/) allows us to [write and organize chapters using Markdown](https://help.gitbook.com/format/chapters.html)
* Conveniently, the [Markdown](https://www.gitbook.com/book/gitbookio/markdown/details) syntax allows arbitrary HTML inline
* We can convert a notebook into an HTML snippet using [nbconvert](https://github.com/jupyter/nbconvert) ([example HTML](https://github.com/data-8/textbook/blob/gh-pages/notebooks-html/Sampling.html))
* Then we include that HTML snippet in the Markdown file ([example Markdown](https://github.com/data-8/textbook/blob/gh-pages/chapter3/sampling.md))

```
Sampling
========

{% include "../notebooks-html/Sampling.html" %}
```

#### The Interact button distributes content to students

An Interact button in the textbook ([example section](http://www.inferentialthinking.com/chapter3/sampling.html)) is a link like this:

    http://data8.berkeley.edu/hub/interact?repo=textbook&path=notebooks/top_movies.csv&path=notebooks/Sampling.ipynb

[DS8-Interact](https://github.com/data-8/DS8-Interact) is a side server for the DATA 8 JuypterHub deployment to copy remote notebooks into user accounts

    git clone https://github.com/data-8/DS8-Interact.git

### DATA 8 JupyterHub deployment user interface

### Computer lab assignments are Jupyter notebooks

[data8assets github repo](https://github.com/data-8/data8assets)

    git clone https://github.com/data-8/data8assets.git

## JupyterHub deployment

    git clone https://github.com/data-8/jupyterhub-deploy.git

- We were about to level out a new basement to give students computers with
  Jupyter installed...
- ...until we discovered that [Jessica Hamrick](http://www.jesshamrick.com/) had
  deployed JupyterHub to the cloud. We thought we could do it too.
- We based [our deployment][data8-jhub] on Jess' [jupyterhub-compmodels-deploy]
  [comp-jhub].
- See Jessica's blog post at Rackspace on [Deploying JupyterHub for Education]
  [jhub-post] and also her README at [jupyterhub-compmodels-deploy][comp-jhub]
  for the design details.

### Technical specs

- For our Fall 2015 pilot of ~80 students, we deployed JupyterHub on bare-metal
  machines from UC Berkeley's CS department.
- We gave each student 2GB of RAM. We expected about 50% of the class to be on
  at any point in time, so we provisioned two nodes with 26GB RAM each.
  TODO(sam): Verify these numbers.
- For the Spring 2016 class of ~480 students, we used a donation from [Microsoft
  Azure][azure] and deployed there, using 36 nodes of 14GB RAM each.

[data8-jhub]: https://github.com/data-8/jupyterhub-deploy
[comp-jhub]: https://github.com/compmodels/jupyterhub-deploy
[jhub-post]: https://developer.rackspace.com/blog/deploying-jupyterhub-for-education/
[azure]: https://azure.microsoft.com/

## Connector courses

* Suite of [connector courses](https://data-8.appspot.com/sp16/modules/extra_tabs/render?index=3) are taught in departments across campus and introduce diverse subjects through the lens of data science
* Spring 2016 has 11 connector courses: in ethics, cognitive science, geospatial data, probability & statistics, ecology, history, matrices & graphs, computational structures, health & human behavior, smart cities, literature
* Nearly all use Jupyter notebooks and the DATA 8 JupyterHub deployment
* Many connector instructors are new to Python and GitHub

## Technical challenges and possible future directions

### Scaling **up** to more students

- Theoretically, scaling up to more students means we can just add more nodes to
  the JupyterHub deployment to get the computing power in. However...
- ...we're now discovering bugs that are only discoverable when dealing with
  scale.
- We were haunted by [a race condition][race-condition] in JupyterHub that
  resulted in large amounts of 503 errors for weeks.
- We've had to make a forum thread for these issues. Students still run into
  them every day.

    ![Error reporting forum thread][forum-thread-img]

- Now we have a team of students adding tooling to make deployment more stable.
  This includes a [development deployment][dev-jhub], [logging and
  monitoring][logging], and [load testing][load-testing].

[race-condition]: https://github.com/jupyter/jupyterhub/issues/410
[forum-thread-img]: https://www.dropbox.com/s/535f0ck4feizp1u/Screenshot%202016-03-14%2023.58.44.png?dl=1
[dev-jhub]: https://docs.google.com/document/d/1ami0zbF3Z6KOhA5j_mqzoDPeoUaRXDkxxPtzVvwKCDk/edit?usp=sharing
[logging]: https://docs.google.com/document/d/14l7Goct2Xch4EBCSuO_-SKTAw3vxXO_WtCNB11Xo-SY/edit?usp=sharing
[load-testing]: https://docs.google.com/document/d/1YFLP-O4B86_2A91sdvO7Rpq2on0Cx5cyFF74MN8pXTY/edit?usp=sharing


### Scaling **out** to more classes

- Scaling out is another ordeal. Our goal is to have one JupyterHub deployment
  that can serve all the classes at UC Berkeley. Adding JupyterHub for a class
  should be as easy as creating a class page.
- At the moment, JupyterHub consolidates all users into one system. We need to
  split the users into multiple classes.
- Problems that need solving:
    - Classrooms have different resources. Some might have AWS credits, others
      can have Azure credits, etc.
    - Students should be able to access different hubs for different classes.
    - Instructors need a way to distribute content to students.
    - Ideally, instructors can also grade assignments easily.
- Proposals to solve these problems:
    - A JupyterHub Hub, which lists and manages deployments of JupyterHub
    - A Dropbox-like interface to GitHub to help instructors with content
      management
        - See the [design doc][jhub-synced-design] for an experiment called
          [jupyter-synchronized-folders][jhub-synced]

[jhub-synced-design]: https://github.com/elaine84/jupyter-synchronized-folders/blob/proposal/design.md
[jhub-synced]: https://github.com/elaine84/jupyter-synchronized-folders

## Other resources
* [jupyter-education Google
  Group](https://groups.google.com/forum/#!forum/jupyter-education)
* [JupyterHub Gitter channel](https://gitter.im/jupyter/jupyterhub)
