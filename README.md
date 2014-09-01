git-presentation
================
A presentation providing an overview of Git(Hub) and some use cases: cloning public repositories, creating local repositories, pushing to a remote. Written in reStructuredText and compiled into a single html document and also an html presentation.

Buidling requirements
---------------------
* ```Python (2.7 or higher)```
* ```hieroglyph```
* ```Sphinx```

To build
--------
To build a single HTML page::

    $ make html

To build HTML slides::

    $ sphinx-build -b slides . ./_build/slides

