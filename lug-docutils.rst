Suffering Less
==============
A Tour of Docutils and reStructuredText
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:Author: Jack Rosenthal
:Date: 2018-02-22

About This Presentation
-----------------------

.. image:: graphics/rtfm.jpg
   :width: 180pt

.. note::

    This presentation is intended to give you **a tour** of reStructuredText
    and Docutils, but by no means is it intended to be a replacement for (or
    even a supplement to) the `official documentation`_.

In other words, read the *fine* manual.

.. _official documentation: http://docutils.sourceforge.net/rst.html

Background
----------

Markup Languages
~~~~~~~~~~~~~~~~

**Markup languages** are used to annotate semantical features of a document.
Typically, these semantical features also describe how the text should be
presented (a **presentational markup language**), but this is not always the
case (e.g., with XML).

Some examples:

* HTML
* DocBook
* TeX, troff, PostScript (all of these are **procedural markup languages**)
* MediaWiki Wikitext
* Markdown
* **reStructuredText**

What's wrong with just writing HTML?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* HTML is very powerful
* It's hard to write, and even harder to read *"in the raw"*
* Especially true of new versions, where meaning can be hidden in CSS, or worse
  yet, JavaScript
* Readability *"in the raw"* is important for programming documentation, etc.
* Similar argument could be made for TeX, troff, etc.

Introducing reStructuredText
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* reST is based on StructuredText, a markup language developed by Zope for use in
  their Python documentation
* Addresses issues_ with StructuredText, Setext, and earlier iterations
* Intends to read and write naturally, like you might type an Email
* Intends to be extensible, and allows the addition of new features without
  introducing new syntax
* Guido approves: official markup language for Python documentation

.. _issues: https://mail.python.org/pipermail/doc-sig/2000-November/001240.html

Basics
------

Show me an example!
~~~~~~~~~~~~~~~~~~~

.. sourcecode:: rst

    Hello World!
    ============

    This is my first reST document!


More Examples!
~~~~~~~~~~~~~~

.. sourcecode:: rst

    Hola World!
    ===========
    This is a reST document with cool features like
    *italics*, **bold**, and ``literal`` text.

    Second Level Header
    -------------------
    More stuff!

    Third Level Header
    ~~~~~~~~~~~~~~~~~~
    You can actually use whatever symbols you want to
    underline headers, so as long as they fall in order.

Hyperlinks
~~~~~~~~~~

.. sourcecode:: rst

    The simplest way to make a link is to type anything
    that looks like a URL or Email address, like
    http://this.example.org/ or this@example.org.

    Often times though, we want to refer to our link by
    name_, or by `fancy names with spaces`_.

    .. _name: http://inside.mines.edu/~jrosenth
    .. _fancy names with spaces: http://www.python.org

More Hyperlinks
~~~~~~~~~~~~~~~

.. sourcecode:: rst

    You may be tempted to refer using an `embedded URI
    <http://www.python.org>`_, but generally this reduces
    the readability of your document.

    Instead, consider referring to another reference for
    `particularly long names <yacht_>`_.

    .. _yacht: http://montypython.wikia.com/wiki/Graham_Chapman

    or, you might consider an `anonymous reference`__:

    __ http://montypython.wikia.com/wiki/Raymond_Luxury-Yacht

Internal References
~~~~~~~~~~~~~~~~~~~

.. sourcecode:: rst

    This slide is on `Internal References`_, and that link
    will link to the header of this slide.

    We could make a reference right _here, then refer to it
    `later <here_>`_, or even refer to explicit_ internal
    references.

    .. _explicit:

    Yadda yadda yadda.

Footnotes
~~~~~~~~~

.. sourcecode:: rst

    Authors use footnotes[1]_ to refer to blips of text
    that won't fit in the sentence.

    .. [1] A footnote is usually printed at the edge or
           bottom of a page.

    reST also has autonumbered footnotes like this [#]_,
    or even named footnotes that get an internal reference
    name_ [#name]_.

    .. [#] This one is autonumbered.
    .. [#name] This one has a name_!

Grid Tables
~~~~~~~~~~~

.. sourcecode:: rst

    +------------+------------+-----------+
    | Header 1   | Header 2   | Header 3  |
    +============+============+===========+
    | body row 1 | column 2   | column 3  |
    +------------+------------+-----------+
    | body row 2 | Cells may span columns.|
    +------------+------------+-----------+
    | body row 3 | Cells may  | - Cells   |
    +------------+ span rows. | - contain |
    | body row 4 |            | - blocks. |
    +------------+------------+-----------+

Simple Tables
~~~~~~~~~~~~~

.. sourcecode:: rst

    =====  =====  ======
       Inputs     Output
    ------------  ------
      A      B    A or B
    =====  =====  ======
    False  False  False
    True   False  True
    False  True   True
    True   True   True
    =====  =====  ======

Literal Blocks
~~~~~~~~~~~~~~

Literal blocks are started by typing ``::``, and the indented data is shown
literally::

    and the indented data is shown literally::

        and the indented data is...

If you aren't starting with a colon, you can put it on its own line.

::

    you can put it on it's own line.

    ::

        you can...

Line Blocks
~~~~~~~~~~~

Using a line block lets you easily manually specify the line breaks without
literal text:

.. sourcecode:: rst

    | This data is broken where
    | I put my own new lines.
    | It's great for poems.

Block Quotes
~~~~~~~~~~~~

Indented data on its own is considered to be a block quote.

.. sourcecode:: rst

    Here's a fun quote:

        Any fool can use a computer, many do.

Roles & Directives
------------------

Roles
~~~~~

Roles are a syntax that allows for *inline* extensibility of reST's features.
For example, consider the ``:math:`` role, built into Docutils:

.. sourcecode:: rst

    We see as :math:`x \to \infty`, :math:`f(x) \to 0`.

Docutils also includes a number of other builtin roles:

.. container:: beamer-simplecolumns

    .. container::

        * ``:emphasis:`` (equivalent to ``*``)
        * ``:literal:`` (equivalent to ``````)
        * ``:code:`` (syntax highlighted code)
        * ``:pep-reference:``
        * ``:rfc-reference:``

    .. container::

        * ``:strong:`` (equivalent to ``**``)
        * ``:subscript:``
        * ``:superscript:``
        * ``:title-reference:`` (for citations)

Directives
~~~~~~~~~~

Directives are a syntax that allows for *blocks* extending reST's features. For
example, consider the ``note`` directive:

.. sourcecode:: rst

    .. note::

        LUG is love. LUG is life.

        * This is a bulleted list inside of the note

    This paragraph is outside of the note.

Admonitions
~~~~~~~~~~~

A note is a special form of an ``admonition`` directive. You can make your own
admonitions:

.. sourcecode:: rst

    .. admonition:: Watch Out

        This admonition is custom!

There's a number of other builtin admonition directives:

.. container:: beamer-simplecolumns

    .. container::

        * ``attention``
        * ``caution``
        * ``danger``
        * ``error``

    .. container::

        * ``hint``
        * ``important``
        * ``tip``
        * ``warning``

Images
~~~~~~

.. sourcecode:: rst

    .. image:: picture.jpeg
       :height: 100px
       :width: 200px
       :scale: 50%
       :alt: alternate text
       :align: right

Figures
~~~~~~~

.. sourcecode:: rst

    .. figure:: picture.png
       :scale: 50 %
       :alt: map to buried treasure

       This is the caption of the figure (a simple paragraph).

Substitutions
~~~~~~~~~~~~~

Text inside ``|vertical bars|`` will be substituted with the corresponding
defining directive:

.. sourcecode:: rst

    .. |reST| replace:: reStructuredText

    Yes, |reST| is a long word, so I can't blame anyone for wanting to
    abbreviate it.

You can even use this combined with references:

.. sourcecode:: rst

    I recommend you try |Python|_.

    .. |Python| replace:: Python, *the* best language around
    .. _Python: http://www.python.org/

Topics and Sidebars
~~~~~~~~~~~~~~~~~~~

``topic`` and ``sidebar`` can be used to separate side-tangents in your
writing. ``topic`` displays inline, and is useful for things like an abstract,
and ``sidebar`` displays on the side of the page.

.. sourcecode:: rst

    .. sidebar:: Report Alternative

        I hear you don't like writing reports...

Classes and Containers
~~~~~~~~~~~~~~~~~~~~~~

The ``class`` directive will apply a class to each body element:

.. sourcecode:: rst

    .. class:: myclass

        Element one

        Element two

Similarly, the ``container`` directive will apply the class to all the elements
in a container:

.. sourcecode:: rst

    .. container:: myclass

        Element one

        Element two

Raw Data Passthru
~~~~~~~~~~~~~~~~~

The ``raw`` directive is a stop-gap measure. You specify the name of the writer
to pass through to:

.. sourcecode:: rst

    .. raw:: latex

        \begin{tikzpicture}
            ...
        \end{tikzpicture}

Including Files
~~~~~~~~~~~~~~~

The ``include`` directive will include external files, relative to the current
document's path:

.. sourcecode:: rst

    .. include:: anotherfile.rst

Optionally, you may specify the ``literal`` or ``code`` option to include
external code fragments.

Custom Text Roles
~~~~~~~~~~~~~~~~~

You can quickly add new roles from directives using the ``role`` directive:

.. sourcecode:: rst

    .. role:: rust(code)
       :language: rust

Now we can syntax highlight Rust inline using ``:rust:``!

Default Text Role
~~~~~~~~~~~~~~~~~

You can set the default text role (what you get when using backticks without
``:name:`` in front of it) for a document by using the ``default-role``
directive:

.. sourcecode:: rst

    .. default-role:: math

Now ``:math:`` will be assumed with backticks. This is convenient for documents
that typeset a lot of math.

Hacking Docutils
----------------

Custom Directives
~~~~~~~~~~~~~~~~~

One of the great advantages of Docutils is how easy it is to hack on.

.. sourcecode:: python

    class MyCont(body.Container):
        option_spec = {'name': str, 'width': str}
        def __init__(self, *args, width=None, **kwargs):
            super().__init__(*args, **kwargs)

    rst.directives.register_directive('custom-container', MyCont)

Custom Roles
~~~~~~~~~~~~

Similar to the custom directives, you can add custom roles in Python. See
`Hacking Docutils`_ on my personal website for a detailed example (a custom
``slides`` role for linking to various versions of the slides).

.. _Hacking Docutils: http://inside.mines.edu/~jrosenth/hacking-docutils.html

Sphinx
------

Sphinx
~~~~~~

While ``docutils`` is good for parsing reST documents, Sphinx is a complete
documentation generation suite.

You've probably seen it on sites like "Read the Docs"... it's awesome!

It generates documentation from your code automatically, and parses directories
full of reST documents.

Highly recommend. It's good for other things too, such as course websites! See
https://lambda.mines.edu for an example.

Why Not Markdown?
-----------------

Things that Markdown is good at
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This slide intentionally left blank.
