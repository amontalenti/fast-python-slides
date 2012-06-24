.. include:: <s5defs.txt>

===========
Fast Python
===========

:Author:  Andrew Montalenti
:Date:    $Date: 2012-06-24 11:00:00 -0500 (Sun, 24 Jun 2012) $

.. This document is copyright Andrew Montalenti

.. container:: handout

    **How this was made**

    This document was created using Docutils_/reStructuredText_ and S5_.

    Simplicity begets elegance.

.. _Docutils: http://docutils.sourceforge.net/
.. _reStructuredText: http://docutils.sourceforge.net/rst.html
.. _S5: http://meyerweb.com/eric/tools/s5/

.. container:: handout

    **Exercises**

    Exercises for this book are taken from four primary sources. These are:
            * Zed Shaw's excellent book, `Learn Python the Hard Way`_, known affectionately as LPTHW
            * `Google's Python Class`_, available on Google Code
            * `Intermediate and Advanced Software Carpentry with Python`_, an online course by C. Titus Brown
            * `Dive Into Python`_, by Mark Pilgrim

.. _Learn Python the Hard Way: http://learnpythonthehardway.org
.. _Google's Python Class: http://code.google.com/edu/languages/google-python-class/
.. _Intermediate and Advanced Software Carpentry with Python: http://ivory.idyll.org/articles/advanced-swc/
.. _Dive Into Python: http://diveintopython.org/

Read slides on your own
-----------------------

http://pixelmonkey.org/pub/fast-python

shorter: http://bit.ly/fast-python


Meta Information
----------------

**Me**: I've been using Python for over 10 years. I use Python full-time, and have for the last 4 years.

**Professionally**: I'm the co-founder/CTO of Parse.ly_, a tech startup in the digital media space. We build web analytics systems and APIs for the web's best publishers. I'm also the founder/principal at `Aleph Point`_, an agile software engineering consulting and training firm. 

**E-mail me**: andrew@alephpoint.com

**Follow me on Twitter**: amontalenti_

**Connect on LinkedIn**: http://linkedin.com/in/andrewmontalenti

.. _Aleph Point: http://alephpoint.com
.. _Parse.ly: http://parsely.com
.. _amontalenti: http://twitter.com/amontalenti

Slide Zero
-----------

Simplicity begets elegance.

---------------------

.. sourcecode:: python

    >>> nums = [45, 23, 51, 32, 5]
    >>> for idx, num in enumerate(nums):
    ...    print idx, num
    0 45
    1 23
    2 51
    3 32
    4 5

The Zen of Python
-----------------

It's embedded in the heart of the language.

.. sourcecode:: python

    >>> import this
    The Zen of Python, by Tim Peters

    Beautiful is better than ugly.
    Explicit is better than implicit.
    ...

Principles behind Python
------------------------

Time to a solution is determined by:
    * how long writing a program takes (*human time*)
    * how long it takes that program to run (*machine time*)

Every language was written with a tradeoff between these:
    * Java
    * C
    * C++
    * Perl
    * MATLAB

Time spent developing
---------------------

Watch out for the increasing human cost of a project as time goes on!

.. image:: img/06_devcurve.png
    :align: center

Didier's decision
-----------------

Didier is a Parse.ly cofounder and my favorite Python engineer on the planet.

.. class:: incremental

    My choices at the time were `Java (the Eclipse-driven language),` `C (a
    language of last resort),` `C++ (a language that comes with reference
    book),` `Perl (a Babylonian language),` `and Matlab (closed source).`

    `At the time, I was done with computer science and I needed a language
    that I could use for` `prototyping, like Matlab was,` `but more
    general.`

Python meets expectations
--------------------------

There are many programming languages that meet the minimum criteria
for a strong platform for modern software development. Python, like
many of those options, is: 

.. class:: incremental

    * free and open source
    * cross-platform
    * widely-used and well-supported
    * well-documented

...and then exceeds them
-------------------------

Python is unique in that it also has:

.. class:: incremental

    * an enormous standard library 
    * a vibrant third-party development ecosystem
    * a wide acceptance for web development
    * a slew of academic programming libraries (bioinformatics, NLP)
    * several options for increasing performance 

Our first program
-----------------

.. sourcecode:: python

    >>> nums = [45, 23, 51, 32, 5]
    >>> for idx, num in enumerate(nums):
    ...    print idx, num
    0 45
    1 23
    2 51
    3 32
    4 5

Dissection
----------

.. sourcecode:: python

    >>> nums = [45, 23, 51, 32, 5]

.. class:: incremental

    Declares a *label* called ``nums``, and *binds* it to a ``list`` value.

    Could just as easily be written this way, although no Pythonista would ever do this.

.. sourcecode:: python

    >>> nums = list()
    >>> nums.append(45); nums.append(23)
    >>> nums.append(51); nums.append(32)
    >>> nums.append(5)

The verbosity of Java
---------------------

Contrast to Java:

.. sourcecode:: java

    // Java code
    List<Integer> nums = new ArrayList<Integer>();
    nums.add(45); nums.add(23);
    nums.add(51); nums.add(32);
    nums.add(5);

Or, at best:

.. sourcecode:: java

    List<Integer> nums = 
        Arrays.asList(new Integer[] {45, 23, 51, 32, 5});

Concise syntax is Pythonic
---------------------------

.. class:: incremental

    In Java, I have even tapped into some obscure features, using ``Arrays.asList`` to initialize the ``ArrayList``, leveraging the fact that arrays, but not lists, have a concise initialization syntax.

    In Python, lists are declared using ``[item1, item2, item3, ...]``, a simple and concise syntax that can be easily read.

    This is but one example of *hundreds* made in the language.

Dissection (con't)
------------------

.. sourcecode:: python

    >>> for idx, num in enumerate(nums):

*Iterates* over each item in the ``nums`` list, yielding a ``tuple`` for each 
iteration step that contains the *index of the list value* and the *list value* itself.

.. sourcecode:: python

    >> list(enumerate(nums))
    [(0, 45), (1, 23), (2, 51), (3, 32), (4, 5)]

Dissection (still con't)
------------------------

.. sourcecode:: python

    ... print idx, num

The ``for`` loop has created two new *bindings*, ``idx`` and ``num``, for each iteration step of the loop. These bindings are *unpacked* from the tuples yielded by the ``enumerate`` built-in function.

Dissection (final)
------------------

We can break this down by looking at how one step would work.

.. sourcecode:: python

    >>> idx, num = (0, 45)
    >>> idx
    0
    >>> num
    45
    >>> print idx, num
    0 45


Welcome to Python!
------------------

Two readable lines of code that do a whole lot of work for you. You've already
been subtly exposed to some features we'll learn about in the upcoming course:

    * concise list syntax
    * variable bindings and scope
    * tuples
    * iterators (and even generators!)
    * value unpacking
    * ``print`` keyword

Development Environment Setup
-----------------------------

Behind every good Python programmer is a good development environment.

.. class:: incremental

    * **Python 2.7**: the latest "stable/prod" version of Python
    * **IPython 0.13**: an enhanced Python shell for prototyping
    * **setuptools**: utility for installing 3rd-party modules
    * **pip**: enhanced utility for 3rd-party modules
    * **virtualenv**: a way to create self-contained Python environments
    * **editor**: I like vim (light) and KomodoEdit/SublimeText (heavy)
    * **UNIX**: http://bit.ly/unix-kitchen

BREAK: Confirm system settings
------------------------------

... cue elevator music ...

The basics
----------

In traditional compiled languages like C/C++, you think about *user programs*
which run directly on the operating system.

.. image:: img/01_prog.png 
    :align: center

Python shell
------------

Python introduces one more layer of abstraction, the *Python interpreter*, that
is like a mini operating system running above the actual operating system.

There is no separate "compilation" step like C/C++/Java.

You simply run the ``python`` command, and you can start evaluating code.

.. sourcecode:: python

    >>> print 1 + 2
    3
    >>> print 'charles' + 'darwin'
    charlesdarwin


Python runtime
--------------

The ``python`` command, when run with no arguments, opens the interactive
shell.

When run *with* arguments, it acts as a runtime for code that can be stored
in files or provided at the command line.

.. sourcecode:: bash

    python -c "print 1 + 2"
    python myprog.py

Label assignment
----------------

.. sourcecode:: python

    >>> planet = 'Sedna'
    >>> print plant # note the deliberate misspelling
    Traceback (most recent call last):
        print plant
        NameError: name 'plant' is not defined
    >>> 

Must assign a value to a label before it can be used. No compile-time check
that label has already been assigned, so mis-spelled label name raises a
``NameError`` exception. *This is a common source of bugs*.

Strong typing
-------------

.. class:: incremental

    Though labels can be re-assigned among types at will, the actual *values* behind the labels do have types.
    
    And Python does not go out of its way to coerce types that cross "semantic boundaries".

Minimal automatic coercion
--------------------------

.. sourcecode:: python

    >>> string = "two"
    >>> number = 3
    >>> string, integer = integer, string # swap values
    >>> print string + number
    Traceback (most recent call last)
        string + number
        TypeError: cannot concatenate 'int' and 'str' objects

.. class:: incremental

    This makes Python a *dynamic, but strongly typed* language. Contrast with Perl, which is *both dynamic and weakly typed*.

Indentation
-----------

"Wait a second. Are you serious? Whitespace is *significant* in Python?"

"Where the hell are my curly braces!?"

.. sourcecode:: python

    >>> from __future__ import braces
    SyntaxError: not a chance (<ipython console>, line 1)

You heard the interpreter.

Why indentation?
----------------

.. class:: incremental

    Short answer: because we do it anyway.

    Better answer: because some of us don't.

    `Python Style Guide (PEP 8)`_ recommends 4 spaces, and no tab characters.

.. _Python Style Guide (PEP 8): http://www.python.org/dev/peps/pep-0008/

Line continuation
-----------------

One problem with significant indentation is how to break long statements on multiple lines.

Python has two options:

    * The ``\`` character, which indicates that the end of a line has been reached and tells the interpreter to treat the next line as a continuation of the current line; best to avoid this one if possible
    * The ``(...)``, ``{...}`` and ``[...]`` characters, which create an implicit continuation; use this one if possible

Empty statements
----------------

Another problem with indentation is that it makes it harder to specify "empty statements". e.g., in JavaScript ``function() {}`` represents an "empty function". Python does this with a special keyword called ``pass``, that simply does nothing. An example:

.. sourcecode:: python

    if normal_condition:
        do_something_normal()
    elif special_condition:
        pass
    else:
        do_default()

The middle condition is a "no-op". It's also used for stubs, e.g.:

.. sourcecode:: python

    def placeholder(): pass

Line continuation example
-------------------------

.. sourcecode:: python

    # prefer this:
    "{foo} {bar} {baz}".format(
        foo=foo, bar=bar, baz=baz)
    # to this:
    "{foo} {bar} {baz}"\
        .format(foo=foo, bar=bar, baz=baz)


Documentation built-in
----------------------

.. sourcecode:: python

    >>> import string
    >>> dir(string)
    ['__builtins__', '__doc__', ..., 'atof', 'atof_error', 'atoi', ...]
    >>> print string.count.__doc__
    count(s, sub[, start[,end]]) -> int

        Return the number of occurrences of substring sub in string
        s[start:end].  Optional arguments start and end are
        interpreted as in slice notation.

help function
-------------

With no arguments, the ``help`` function opens an interactive help prompt.

But usually, you only need help on a specific function or module. So, then you
can call ``help`` with an argument.

Example of help
---------------

.. sourcecode:: python

    >>> import string
    >>> help(string)
    Help on module string:

    NAME
        string - A collection of string operations...

    FILE
        /usr/lib/python2.6/string.py

    MODULE DOCS
        http://docs.python.org/library/string

    ...

Printing
--------

.. sourcecode:: python

    >>> print "Hello World!"
    Hello World!
    >>> cars = 100
    >>> print "There are", cars, "available"
    There are 100 cars available
    >>> print??
    Type:       builtin_function_or_method
    ...
        print(value, ..., sep=' ', end='\n', file=sys.stdout)
            Prints the values to a stream, or to sys.stdout by default.

Comments
--------

.. sourcecode:: python

    #!/usr/bin/env python
    # Written by John Doe, 6/5/2011
    #
    if __name__ == "__main__": # only runs when script is executed
        print "Hello, World"

Math and Numbers
----------------

.. sourcecode:: python

    >>> x = 3
    >>> 1 < x < 3
    False
    >>> 2 < x < 5
    True
    >>> 3 == x
    True
    >>> x + 0.1
    3.1000000000000001

Python number literals are either ``int`` or ``float``, depending on context. If an expression is a ``float``, IEEE 754 floating point rules apply. Otherwise, normal integer math rules apply.

Float context
-------------

.. sourcecode:: python

    >>> type(0.1)
    <type 'float'>
    >>> type(3)
    <type 'int'>
    >>> type(3 + 0.1)
    <type 'float'>


Decimals
--------

.. sourcecode:: python

    >>> from decimal import Decimal as D
    >>> D("3") + D("0.1")
    Decimal('3.1')
    >>> D("3") + D("0.1") == D("3.1")
    True

When dealing with non-scientific computations, you probably want to use the ``Decimal`` class. It is a little awkward to use -- you must specify your numbers as strings. However, it supports all expected operations directly on the Decimal object.

To make it a little easier to use, I imported it using a module alias ``D``.

Fractions
---------

.. sourcecode:: python

    >>> from fractions import Fraction as F
    >>> F(1, 3) + F(1, 2)
    Fraction(5, 6)

Formatting
----------

There are two simple ways to do string formatting in Python, and both are very popular.

    * ``%``, defined on ``str`` objects.
    * ``str.format``, a more verbose method available on ``str``.


.. sourcecode:: python

    >>> "%s cars crossed the intersection \
        in the last %s hours" % (5, 24)
    5 cars crossed the intersection in the last 24 hours
    >>> "{num} cars crossed the intersection \
        in the last {hrs} hours".format(num=5, hrs=24)
    5 cars crossed the intersection in the last 24 hours


Strings
-------

.. class:: incremental

    There are many programmers for whom strings play a much more vital role than number types.

    I am one of those programmers.

    My applications deal with the web and with large-scale text processing.
    
    A core understanding of strings and a language with capabilities to manipulate them is critical to get work done in this environment.


The str literal
---------------

In Python, strings can be enclosed with single, double, or *triple* quotes.

.. sourcecode:: python

    >>> 'single'
    'single'
    >>> "double"
    'double'
    >>> """triple"""
    'triple'
    >>> """though single and double are mostly interchangeable,
    triple quotes have a special property: they ignore line 
    breaks. Thus, they can be used as a kind of 'heredoc'."""
    "though single and double are mostly interchangeable,\n triple ..."

Special str modes
-----------------

They may also be preceded with a special character prefix, indicating a special string mode. Currently, only two are supported: *raw* strings using prefix ``r``, and *unicode* strings using prefix ``u``.

.. sourcecode:: python

    >>> print('C:\new\node\nell.exe')
    C:
    ew
    ode
    ell.exe
    >>> print(r'C:\new\node\nell.exe')
    C:\new\node\nell.exe
    >>> print(u"\u2192")
    →

str methods
-----------

Strings support a healthy number of methods, including:

    * common transformations like ``lower`` and ``upper``
    * conveniences like ``strip`` and ``startswith``
    * utilities like ``find``, ``replace``, ``split``, and ``join``

.. sourcecode:: python

    >>> ". ".join("PYTHON IS GREAT".lower().split()) + "."
    python. is. great.

str operators
-------------

Strings also support some great operators:

    * ``+`` for concatenation
    * ``[idx]`` for slicing
    * ``*`` for repeating
    * ``in`` for substring matching

.. sourcecode:: python

    >>> p = "PYTHON" 
    >>> g = ("GREAT " * 3).strip()
    >>> "GREAT" in g
    True
    >>> p + (" %s " % "IS") + g[0:15] + "..."
    'PYTHON IS GREAT GREAT GRE...'

Method chaining
---------------

When methods are chained, the intermediary results of computation are simply discarded.

.. image:: img/05_methodchain.png
    :align: center

Built-in namespace
------------------

.. class:: incremental

    Python automatically imports a slew of functions, types, and symbols, which are known collectively as *built-ins*.

    These provide the "basic language constructs" before you start referencing the modules of the standard library.

.. sourcecode:: python

    >>> sorted(vars(__builtins__).keys())[-5:]
    ['tuple', 'type', 'unichr', 'unicode', 'vars', 'xrange', 'zip']
    >>> sorted is __builtins__.sorted
    True

Built-in functions
------------------

Built-in functions are covered in this document:

http://docs.python.org/library/functions.html

Some early ones to look at are:

.. class:: incremental

    * ``all`` and ``any`` for applying boolean filters to lists
    * ``dict``, ``list``, ``set``, and ``object``, all of which will be covered later
    * ``hasattr``, ``getattr``, and ``setattr``, for dynamic introspection
    * ``sorted`` and ``reversed`` for sorting lists
    * ``int``, ``str``, and ``float``, which act as type constructors and coercers
    * ``min``, ``max``, and ``sum`` for common list math

All objects are first-class
---------------------------

.. sourcecode:: python

    >>> line = "GOOG,100,490.10"
    >>> field_types = [str, int, float]
    >>> raw_fields = line.split(",")
    >>> fields = [ty(val) for ty, val in zip(field_types, raw_fields)]
    >>> fields
    ['GOOG', 100, 490.1000000000002]

The fact that everything in Python is first-class is often not fully appreciated by new programmers.

How would you have written this in Java / C# / C++ / C?

True, False, and None
---------------------

Among the imported symbols from ``__builtins__`` are ``True``, ``False``, and ``None``.

These core symbols used in boolean logic, and are typically utilized with keywords such as ``is``, ``not``, ``and``, ``or``, etc.

Object equality and identity
----------------------------

.. sourcecode:: python
    
    >>> x, y = (0, 1)
    >>> y == True # aka, "y is truthy"
    True
    >>> x == False # aka, "x is falsy"
    True
    >>> y is True # aka, "y is True singleton"
    False
    >>> x is False # aka, "x is False singleton"
    False
    >>> y is not True
    True
    >>> y is not False
    True

Lack of switch statement
------------------------

.. sourcecode:: java

    // Java code
    switch (file.getType()) {
        case FileTypes.HTML:
            return "HTML Document";
        case FileTypes.DOC:
            return "MS Word";
        case FileTypes.EXCEL:
            return "MS Excel";
        default:
            return null;
        // ...
    }

Using an elif chain
--------------------

.. sourcecode:: python

    ftype = file.type
    if ftype == "text/html":
        return "HTML Document"
    elif ftype == "application/ms-word":
         return "MS Word"
    elif ftype == "application/ms-excel":
        return "MS Excel"
    else:
        return None

Lists
-----

.. sourcecode:: python

    >>> x = [] 
    >>> x.append(5)
    >>> x.extend([6, 7, 8])
    >>> x
    [5, 6, 7, 8]
    >>> x.reverse()
    >>> x
    [8, 7, 6, 5]


Lists and memory
----------------

Lists are reference types, which means they simply contain pointers to objects that exist elsewhere.

.. image:: img/07_lists.png
    :align: center

List alterations
----------------

Lists can be altered (mutated) at will, which does not require recreation of the entire list.

.. image:: img/08_listalter.png
    :align: center
    :class: scaled

List concatenation
------------------

Lists can be concatenated with other lists using ``extend``, which creates a new list but does not require reallocating all the data.

.. image:: img/09_listconcat.png
    :align: center

List slicing
------------

Lists have a convenient syntax for accessing single elements or even ranges of elements. This is called *slicing* and can also be done with the ``slice`` builtin function or ``[i:j:stride]`` syntax.

.. image:: img/10_listslice.png
    :align: center

List aliasing
-------------

Lists can be aliased simply by binding a new label to the list. This sometimes leads to bugs!

.. image:: img/11_listalias.png
    :align: center

List nesting
------------

Lists can also be arbitrarily nested, or contain other types altogether like tuples, sets, or dictionaries.

.. image:: img/12_listnest.png
    :align: center

Dictionaries
------------

.. sourcecode:: python

    >>> d = {}
    >>> d['a'] = 5
    >>> d['b'] = 4
    >>> d['c'] = 18
    >>> d
    {'a': 5, 'c': 18, 'b': 4}
    >>> d['a']
    5
    >>> e = dict(a=5, b=4, c=18)
    >>> e
    {'a': 5, 'c': 18, 'b': 4}

Dictionary visually
-------------------

Dictionaries contain a "magically stored" set of *items*, which are key to value mappings.

.. image:: img/18_dicts.png
    :align: center

Switch statement to dictionary
------------------------------

.. sourcecode:: python

    long = file.type
    long2short = {
        "text/html": "HTML Document"
        "application/ms-word": "MS Word"
        "application/ms-excel": "MS Excel"
    }
    return long2short.get(long, None)

Sets
----

.. sourcecode:: python

    >>> ppl = ["Andrew", "Joe", "Bob", "Joe", "Bob", "Andrew"]
    >>> ppl = set(ppl)
    >>> print ppl
    set(["Andrew", "Joe", "Bob"])
    >>> trainers = set(["Andrew"])
    >>> print ppl - trainers
    set(["Joe", "Bob"])

Sets visually
-------------

Similarly to dictionaries, sets "magically" store their values. Since sets can only store unique (hashable) values, it will remove duplicates from other collections like lists. Sets also support fast set operations like union, intersection, addition and subtraction.

.. image:: img/17_sets.png
    :align: center

Using ``in`` with dicts and sets (1)
------------------------------------

Good:

.. sourcecode:: python

    for key in d:
        print key

Bad:

.. sourcecode:: python

    for key in d.keys():
        print key


Use ``in`` where possible (2)
-----------------------------

.. class:: incremental

   For consistency, use ``key in dict``, not ``dict.has_key()``::

       # do this:
       if key in d:
           ...do something with d[key]

       # not this:
       if d.has_key(key):
           ...do something with d[key]

Tuples
------

.. class:: incremental

    A ``list`` is a mutable heterogeneous sequence

    A ``tuple`` is an immutable heterogeneous sequence

    i.e., a list that can't be changed after creation

    Why provide a less general type of collection?

Tuple example
-------------

.. sourcecode:: python

    >>> primes = (2, 3, 5, 7)
    >>> print primes[0], primes[-1]
    2 7
    >>> empty_tuple = ()
    >>> print len(empty_tuple)
    0
    >>> one_tuple = (0,)
    >>> print len(one_tuple)
    1

Must use ``(val,)`` for one-tuples, due to some grammar ambiguity. ``(...)`` overloaded for tuples, function invocation syntax, and operator grouping!

Tuples very handy for nested sequences
--------------------------------------

.. sourcecode:: python

    >>> pairs = ((1, 10), (2, 20), (3, 30), (4, 40))
    >>> for low, high in pairs:
    ...   print low + high
    ...
    11
    22
    33
    44

Think data, not code
--------------------

.. class:: incremental

    * Java / C++ / C# programmers coming to Python often bring their
      language-specific idioms with them
    * Leverage Python's strongest features to make your code cleaner, shorter, and more readable
    * ``switch`` statements are better written as dictionaries
    * Avoid crutches you used to use because you had to


enumerate for indexed iteration
-------------------------------

.. sourcecode:: java

    // Java code
    List<String> colors = new ArrayList<String>();
    colors.add("yellow");
    colors.add("magenta");
    colors.add("lavender");
    for (int i = 0; i < colors.size(); i++) {
        String color = colors.get(i);
        System.out.println(i + " " + color);
    }

Quite a contrast when you compared to this!

.. sourcecode:: python

    # Python code
    >>> items = ['yellow', 'magenta', 'lavender']
    >>> for i, name in enumerate(colors):
    ...   print i, name

Sequence protocol
-----------------

A Python *sequence* is any type that supports these operations:

.. class:: incremental

    * ``len``, for counting number of items in container
    * ``s[i]``, for getting the i'th element of sequence
    * ``s[i:j]``, for slicing from i to j in container
    * ``s[i:j:stride]``, for slicing from i to j, using stride

.. image:: img/24_slicing.png
    :align: center

Sequence examples
-----------------

Examples of sequences:

.. class:: incremental

    * lists
    * tuples
    * strings

Functions
---------

.. sourcecode:: python
    
    def divide(a, b):
        """Divides operands a and b using integer division. 
        Returns a quotient and remainder of division 
        operation in a 2-tuple."""
        q = a // b
        r = a - q * b
        return q, r

.. class:: incremental

    * the triple-quoted string on the first line is a special form of Python
      documentation known as a *docstring*
    * the ``//`` operator is integer division
    * the ``return q, r`` statement shows Python's concise syntax for
      returning multiple values by returning a tuple

Using functions
---------------

.. sourcecode:: python

    >>> from mymath import divide
    >>> help(divide)
    Help on function divide in module mymath:

    divide(a, b)
        Divides operands a and b using integer division. 
        Returns a quotient and remainder of division 
        operation in a 2-tuple.
    ...

``def`` is like any other statement
-----------------------------------

Logic flows around the function body, then re-enters it upon invocation.

.. image:: img/03_flow.png
    :align: center

Calling functions
------------------

.. sourcecode:: python

    >>> divide(5, 2)
    (2, 1)
    >>> quotient, remainder = divide(5, 2)
    >>> print "quotient is %s, remainder is %s" \
    ...     % (quotient, remainder)
    quotient is 2, remainder is 1
    >>> return_value = divide(5, 2)
    >>> print "quotient is %s, remainder is %s" \
    ...     % return_value
    quotient is 2, remainder is 1
    

Keyword arguments
-----------------

.. sourcecode:: python
    
    def connect(host, port=80, scheme="http", timeout=300):
        http = HTTPClient()
        http.connect("{scheme}://{domain}:{port}".format(
            scheme=scheme,
            domain=domain,
            port=port), timeout=timeout)
        return http

.. class:: incremental

    * The first argument is known as a *positional* or *required*
      argument.
    * The latter 3 are known as *keyword* or *optional* arguments.

Argument types
--------------

.. class:: incremental

    * Required arguments will always have the value passed during function call
    * There is no way to restrict argument type
    * Eagerly checking for an argument type is an *anti-pattern* in Python
    * Instead, Pythonistas prefer what is known as *duck typing*

EXERCISES: Write a functional program
-------------------------------------

Expect to receive a URL of the format you would find on the web:

"http://www.linked.com/in/andrewmontalenti"

Implement a function, ``url_parse``, that splits this string into dictionary with the component parts, including: scheme, port, host, path, fragment (hash), query string. For the above, it would be:

.. sourcecode:: python

    { "scheme": "http", "host": "www.linkedin.com", 
    "path": "/in/andrewmontalenti",
    "port": 80, "fragment": None, "query": None }

URL Parser
----------

.. sourcecode:: python

    def url_parse(url):
        assert url is not None
        scheme, rest = url.split(":", 1)
        rest = rest[2:]
        offset = rest.find("/")
        if offset == -1:
            host = rest
            path = None
        else:
            host = rest[0:offset]
            path = rest[offset:]
        if ":" in host:    
            host, port = host.split(":", 1)
        else:
            port = None
        return dict(
            Scheme=scheme, Host=host, 
            Port=port, Path=path)

Module self-test
----------------

.. sourcecode:: python

    if __name__ == "__main__":
        print "Running test cases... ",
        url = "http://www.linkedin.com/in/andrewmontalenti"
        parts = url_parse(url)
        assert parts["Scheme"] == "http", "scheme must match"
        assert parts["Host"] == "www.linkedin.com", "host must match"
        assert parts["Port"] is None, "port must match"
        assert parts["Path"] == "/in/andrewmontalenti", "path must match"
        print "OK."

Simple URL formatter
--------------------

.. sourcecode:: python

    def format_url(d):
        fmt = "{Scheme}://{Host}:{Port}{Path}"
        url = fmt.format(**d) #** ignore that operator for now 
        if ":80" in url:
            url = url.replace(":80", "")
        return url

Integration test
-----------------

.. sourcecode:: python

    url = "http://www.linked.com/in/andrewmontalenti"
    # end-to-end test
    assert format_url(url_parse(url)) == url
    
Recap
-----

Python is a dynamic and opinionated language.

You've already learned the basics:

.. class:: incremental
    
    * Labels, bindings, declarations, and expressions
    * Conditional statements
    * Data structures like dictionaries, lists, and tuples
    * String and number types
    * Function declaration and invocation

Some Excitement
---------------

So far, we learned *just enough* to be dangerous.

Now, let's act dangerously.

Files
-----

.. sourcecode:: python

    data = []
    for line in open('data/commented-data.txt'):
        if line.startswith("#"):
            continue
        data.append(int(line))
    print data
        
Writing to files
----------------

.. sourcecode:: python

    data = [1, 2, 3, 4, 5]
    f = open('data/output.txt', 'w')
    for item in data:
        f.writeline(item)
    f.close()

Lazy programmer reading
-----------------------

.. sourcecode:: python

    reader = open('data/sizable.txt')
    lines = reader.readlines()
    sorted(int(line) for line in lines)

Explanation of that last line will come soon!

Using Modules
-------------

.. class:: incremental

    The only parts of the standard library we have used so far are the ones that are built-in -- either methods of built-in types like ``list`` and ``str``, built-in functions like ``sorted``, built-in constants like ``True``, or built-in exception types like ``NameError``.

    There are a wealth of other functions available via the import mechanism and modules.

    This is also how you utilize 3rd-party modules.

Python .py files
----------------

Every file named with ``{name}.py`` is a Python module called ``name`` automatically. If it's on the ``$PYTHONPATH``, it can be imported. It's that simple!

Packages
--------

.. class:: incremental

    A Python package is a directory full of Python modules containing a
    special file, ``__init__.py``, that tells Python that the directory is
    a package.

    Packages are for collections of library code that are too
    big to fit into single files, or that have some logical substructure
    (e.g. a central library along with various utility functions that all
    interact with the central library).

Importing functions
-------------------

.. sourcecode:: python

    >>> import pprint
    >>> from pprint import pprint as pp

.. class:: incremental

    Importing functions from other modules is probably the simplest form
    of code reuse available in the Python language

    The ``import`` keyword function has a shorthand for aliasing a symbol with the ``as`` keyword

    The ``from...import`` syntax tends to be preferred to direct imports

Consider the alternative
------------------------

.. sourcecode:: python

    >>> import pprint
    >>> pprint = pprint.pprint

.. class:: incremental

    Eek, too many ``pprints``!

    First, a module.

    Then, a label.

    Then, a function within a module of the same name!

Aliasing functions
------------------

.. sourcecode:: python

    >>> from pprint import pprint, pformat
    >>> pf = pformat
    >>> pf is pformat
    True

First-class?
------------

.. class:: incremental

    An integer is 32 bits of data...

    ...that labels can refer to

    A string is a sequence of bytes representing characters...

    ...that labels can refer to

    A function is a sequence of bytes representing instructions...

    ...and yes, labels can refer to them to

    This turns out to be very useful, and very powerful

First-class built-ins
---------------------

.. sourcecode:: python

    >>> def positive(x): return x >= 0
    >>> print filter(positive, [-3, -2, 0, 1, 2])
    [0, 1, 2]

    >>> def negate(x): return -x
    >>> print map(negate, [-3, -2, 0, 1, 2])
    [3, 2, 0, -1, -2]

    >>> def add(x, y): return x+y
    >>> print reduce(add, [-3, -2, 0, 1, 2])
    -2

Higher order function
---------------------

.. class:: incremental

    So, you can pass functions around to other functions.

    Just the same, functions can also *return functions*.

    These are sometimes known as *higher-order functions*.

Decorators
----------

.. sourcecode:: python

    def simple_func(arg1):
        pass
    simple_func = memoize(simple_func)
    simple_func = debug_log(simple_func)

Decorators were meant to make the use of higher-order functions
easier in Python. Code like the above used to be common, but now,
it can be written more simply.

Decorator example
-----------------

.. sourcecode:: python

    @memoize
    @debug_log
    def simple_func(arg1):
        pass

Star argument application syntax
--------------------------------

Before we talk about decorators, though, we have to understand
some more mechanics about functions. The star argument syntax::

    def decorator(fn):
        def wrapper_fn(*args, **kwargs):
            # ... do something before ...
            val = fn(*args, **kwargs)
            # ... do something after ...
            return val
        return wrapper_fn

    @decorator
    def my_fn(arg1, arg2, default1=None):
        pass

The iterator
------------

.. sourcecode:: python

    it = iter(s)
    while 1:
        try:
            item = it.next()
        except StopIteration:
            break
        process(item)

The for loop is "iteration sugar"
---------------------------------

.. sourcecode:: python

    for item in s:
        process(item)

This is the right way to write it.

Implement an iterator
---------------------

If a class supports ``__iter__``, it is said to be ``Iterable``.

The object returned by ``__iter__`` needs to support two methods: ``__iter__`` and ``next``. This object is an ``Iterator``. Think of it like a "cursor" on the sequence, or as a "yielder of values" from the sequence.

The iterator expression
-----------------------

.. sourcecode:: python

    items = [process(item) for item in s]

Python also supports a special syntactic construct that is particularly popular among Pythonistas, known as the *iterator expression* or *list comprehension*.

It is basically a *declarative* version of this code:

.. sourcecode:: python

    items = []
    for item in s:
        items.append(process(item))

List comprehension
------------------

.. sourcecode:: python

    items = [process(item) 
                for item in s 
                if item in process_list]

These can be very powerful. The above processes and filters a list at once.

List comprehension example (1)
------------------------------

.. sourcecode:: python

    >>> [n ** 2 for n in range(10) if n % 2]
    [1, 9, 25, 49, 81]

List comprehensions example (2)
-------------------------------

.. sourcecode:: python

    >>> words = 'The quick brown fox jumps over the lazy dog'.split()
    >>> [(w.upper(), w.lower(), len(w)) for w in words]
    [('THE', 'the', 3),
    ('QUICK', 'quick', 5),
    ('BROWN', 'brown', 5),
    ('FOX', 'fox', 3),
    ('JUMPS', 'jumps', 5),
    ('OVER', 'over', 4),
    ('THE', 'the', 3),
    ('LAZY', 'lazy', 4),
    ('DOG', 'dog', 3)]
 
List comprehensions example (3)
-------------------------------

.. sourcecode:: python

    >>> import os
    >>> from glob import glob
    >>> [f for f in glob('*.py*') if os.stat(f).st_size > 6000] 

Reading code
------------

.. sourcecode:: python

    >>> [l[i] + l[i+1] for i in range(0, 1000, 2)][0:5]
    [1, 5, 9, 13, 17]

Just because you can doesn't mean you should!

The generator
-------------

Generators take iterators one step further by allowing them to be easily written and lazily evaluated.

.. sourcecode:: python

    def infinity():
        i = 0
        while 1:
            i += 1
            yield i

.. class:: incremental

    Yes, this yields an *infinite* sequence of numbers. (Well, plus or minus overflow)

    But calling ``infinity`` doesn't yield them all at once. It gives you a ``generator`` object, which is an iterator that will return the values specified in the ``yield`` expression!

Generator under the hood
------------------------

.. class:: incremental

    Auto-generates the ``__iter__()`` and ``next()`` methods.

    Saves application state up to the ``yield`` keyword.

    Raises ``StopIteration`` when the generator terminates.

    In combination, these features make it easy to create iterators with no more effort than writing a regular function.

The generator object
---------------------

.. sourcecode:: python

    >>> inf = infinity()
    >>> inf
    <generator object infinity at ... >
    >>> inf.next()
    1
    >>> inf.next()
    2
    >>> for i in range(1000):
    ...     print inf.next(),
    3 4 5 6 7 8 9 ...
    >>> for idx, val in enumerate(infinity()):
    ...     if 1000 > idx > 1005:
    ...         print idx,
    ...     if idx == 5000:
    ...         break
    1001 1002 1003 1004

yield keyword
-------------

.. class:: incremental

    You can think of the ``yield`` keyword similarly to the ``return`` keyword, but with a twist.

    The function containing the ``yield`` is replaced with one that simply returns a ``generator``.

    The generator only executes your function upon first call of the ``.next()`` method. The function runs until it reaches a ``yield``, and when it does, it yields the value and returns it from ``.next()``. But then, execution stops.

    Until the next ``.next()``.

Our own ``range``
-----------------

.. sourcecode:: python

    def range(num_ints):
        vals = []
        i = 0
        while i < num_ints:
            vals.append(i)
            i += 1
        return vals

Our own ``xrange``
------------------

.. sourcecode:: python

    def xrange(num_ints):
        i = 0
        while i < num_ints:
            yield i
            i += 1
            
Generator expressions
---------------------

Similarly to list comprehensions / iterator expressions, generators have a declarative form.

.. sourcecode:: python

    >>> is_even = lambda x: x % 2 == 0
    >>> sum(x for x in xrange(10000) if is_even(x))
    2499950000
    >>> (x for x in xrange(10000))
    <generator object <genexpr> at ...>

Rewriting listcomps as genexps
------------------------------

.. sourcecode:: python

    >>> sum([x**2 for x in range(1000)])
    332833500
    >>> sum(x**2 for x in xrange(1000))
    332833500

What's the difference between them?
-----------------------------------

.. class:: incremental

    Our *listcomps* allocate a new list and populate it with all the values specified in your listcomp expression.

    Meanwhile, *genexps* create a generator object.

    If output is only needed as an input for a function expecting a sequence, you should prefer *genexps*. They will keep memory stable.

    If you need to mutate the list (delete or append elements), you need to stick with *listcomps*.

    Most expressions of form ``fn([listcomp])`` and be rewritten ``fn(genexp)`` safely.

Object-oriented vs. functional 
------------------------------

.. class:: incremental

    Is Python a functional language?

    Yes.

    Is Python an object-oriented language?

    Yes.

    Is Python schizophrenic?

    Maybe.

Python's style flexing
----------------------

.. class:: incremental

    Perhaps programming paradigms aren't paradigms, but just *states of mind*.

    If you are writing a math utility library, *functions* may be the best organizing principle.

    If you are writing a database-oriented business application, perhaps *classes* and *objects* are appropriate.

    If you are writing a framework that is meant to be both used and extended, maybe some combination of *both* is in order.

The standard library
--------------------

.. class:: incremental

    The standard library shows the flexibility in action.

    ``urllib`` is basically a set of utility functions for dealing with URLs.

    But it can be extended by looking into ``urllib.FancyURLopener``.

    ``pprint`` and ``pformat`` are handy functions for pretty-printing.

    But if you need more, your can extend ``pprint.PrettyPrinter``.

Class syntax
------------

.. class:: incremental

    Just like modules, classes create a new namespace. But they also
    have special handling for class attributes.

    Every class object is a function which, when called, creates an
    instance of the class. There is no ``new`` keyword.

.. sourcecode:: python

    >>> from profiles import Person
    >>> help(Person)
    >>> person = Person()
    >>> person.<TAB> # (to see methods)

World's simplest class
----------------------

.. sourcecode:: python

    # class with no attributes
    class Person(object): pass
    person = Person()
    # but attributes can be added
    person.first_name = "John Doe"
    person.age = 42

.. class:: incremental

    This is certainly a simple class, but doesn't do much for us.

    Roughly interchangeable with using a ``dict``, except don't need to use string literals to get access to named values.

A simple class for coffee
-------------------------

.. sourcecode:: python

    class CoffeeMaker(object):
        def __init__(self, num_cups, bean="arabica"):
            self.num_cups = num_cups
            self.bean = bean

        def make_coffee(self):
            fmt "made {num_cups} cups of coffee \
                using {bean} beans"
            print fmt.format(num_cups=self.num_cups, bean=self.bean)

.. sourcecode:: python

    >>> c = CoffeeMaker(2)
    >>> c.make_coffee()
    made 2 cups of coffee using arabica beans

Modeling a practical class
--------------------------

.. sourcecode:: python

    from datetime import datetime

    class Employee(object):
        def __init__(self, id_, name, birth_year, role_id=None):
            self.id = id_
            self.name = name
            self.birth_year = birth_year
            self.role_id = role_id
        def get_age(self):
            return datetime.now().year - self.birth_year
        id2role = {
            "FTE": "Full-time Employee",
            "PT": "Part-time Employee",
            "INT": "Intern",
            "CNT": "Contractor"
        }
        def get_role(self):
            if self.role_id is None:
                return None
            return self.id2role.get(self.role_id, "UNKNOWN")
                
Using the ``Employee`` class
----------------------------

.. sourcecode:: python

    >>> emp1 = Employee(1, "John Doe", 1975, role_id="FTE")
    >>> emp2 = Employee(2, "Jane Doe", 1954, role_id="PT")
    >>> emp3 = Employee(3, "Peter Travis", 1982)
    >>> emp1.get_age()
    36
    >>> emp2.get_role()
    "Part-time Employee"
    >>> emp3.get_role() is None
    True


Stateful methods
----------------

.. sourcecode:: python

    >>> employees = (emp1, emp2, emp3)
    >>> age_sum = sum(employee.get_age() for employee in employees)
    >>> avg_age = age_sum/len(employees)
    >>> print avg_age
    40

More advanced classes
---------------------

.. sourcecode:: python

    import fetchers
    import re
    class Client(object):
        # base URL for Guardian open content API
        base_url = 'http://content.guardianapis.com/'
        # Map HTTP paths to instance methods:
        path_method_lookup = (
            ('^/search$', 'search'),
            ('^/tags$', 'tags'),
            ('^/item/(\d+)$', 'item'),
        )
        def __init__(self, api_key, fetcher=None):
            self.api_key = api_key
            self.fetcher = fetcher or fetchers.best_fetcher()
        def search(self, query):
            self.do_call(query)

A real-world example.

Customizing __repr__ and __str__
---------------------------------

.. sourcecode:: python

    class Person(object):
        def __init__(self, name, gender):
            self.name = name
            self.gender = gender
        def __repr__(self):
            return "<%s name=%s, gender=%s>" % (
                self.__class__.__name__,
                self.name, self.gender)
        char2gender = dict(M="Male", F="Female")
        def __str__(self):
            name = self.name
            gender = self.char2gender.get(self.gender, None)
            if gender is None: return name
            return "%s (%s)" % name, gender

Using ``repr`` and ``str``
--------------------------

.. sourcecode:: python

    >>> person = Person("John Doe", "M")
    >>> person
    <Person name=John Doe, gender=M>
    >>> print person
    John Doe (Male)
    >>> str(person)
    "John Doe (Male)"
    >>> repr(person)
    '<Person name=John Doe, gender=M>'
    >>> person.gender = None
    >>> print person
    John Doe
    
Methods
-------

.. class:: incremental

    Every function declared inside a class body is known as a *method*, which is automatically *bound* to an instance of the class at initialization time.

    Inside a bound method, the first argument, typically named ``self``, contains the instance of the object in question. 

The pesky ``self`` convention
------------------------------

.. class:: incremental

    Many programmers find this annoying, and wish they could work around it.

    I'm one of those programmers.

    But I'm here to tell you, in practice, you just get used to it and it ain't so bad.

    Plus, GvR blesses this decision and has said it won't change.

Not just methods
----------------

.. class:: incremental

    Any non-function attributes are considered "class attributes", and are not treated in any special way. Note these are *shared* for all instances of the class, somewhat similarly to ``static`` properties in other languages.

    Any attributes added to the instance directly using ``self.attr = val`` are considered "instance attributes".

Classes are fancy dictionaries
------------------------------

.. class:: incremental

    Sometimes, you'll hear Pythonistas refer to the ``class dictionary`` and the ``instance dictionary``. That's because, under the hood, Python classes are basically fancy dictionaries.

    A built-in, ``vars(object)``, lets you return the "instance dictionary" for a given instance of a class. This is useful to fetch all the data of a class in a generic way.

__init__
---------

At its core, a class is simply a class definition and *typically*, an initialization sequence implemented by ``__init__``.

*Instances* of that class can act either as data containers or, more typically, *bundles of state and behavior*.

OO Design with Classes
----------------------

Classes can let you design object-oriented interfaces that are intuitive for business people to grasp.

.. image:: img/21_oo.png
    :align: center

Deciding between a function and a class
---------------------------------------

.. class:: incremental

    You might wonder, with all of this flexibility...

    How do I decide between a function and a class?

Some functionality requires classes
-----------------------------------

.. class:: incremental

    * Inheritance and type heirarchies
    * Exception types
    * Attribute lookup customization
    * Operator overloading
    * Most "Dunder" protocols

For everything else, prefer functions
-------------------------------------

Only take on as much complexity as you actually need! This is the Python Way!

Python Stdlib
-------------

Let's now do a quick run through a few useful Python standard library modules
to give you a sense of what they mean by "batteries included".

random
------

.. sourcecode:: python

    >>> import random
    >>> random.choice(['apple', 'pear', 'banana'])
    'apple'
    >>> random.sample(xrange(100), 10)      # sampling without replacement
    [30, 83, 16, 4, 8, 81, 41, 50, 18, 33]
    >>> random.random()                     # random float
    0.17970987693706186
    >>> random.randrange(6)                 # random integer chosen from range(6)
    4

datetime
--------

.. sourcecode:: python

    >>> from datetime import date
    >>> now = date.today()
    >>> now
    datetime.date(2003, 12, 2)
    >>> now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B.")
    '12-02-03. 02 Dec 2003 is a Tuesday on the 02 day of December.'
    >>> birthday = date(1964, 7, 31)
    >>> age = now - birthday
    >>> age.days
    14368

json
----

.. sourcecode:: python

    >>> import json
    >>> json.dumps(['foo', {'bar': ('baz', None, 1.0, 2)}])
    '["foo", {"bar": ["baz", null, 1.0, 2]}]'
    >>> print json.dumps({'4': 5, '6': 7}, sort_keys=True, indent=4)
    {
        "4": 5,
        "6": 7
    }
    >>> json.loads('["foo", {"bar": ["baz", null, 1.0, 2]}]')
    [u'foo', {u'bar': [u'baz', None, 1.0, 2]}]

collections
-----------

.. sourcecode:: python

    >>> from collections import defaultdict
    >>> s = 'mississippi'
    >>> d = defaultdict(int)
    >>> for k in s:
            d[k] += 1
    >>> d.items()
    [('i', 4), ('p', 2), ('s', 4), ('m', 1)]

itertools.groupby
-----------------

.. sourcecode:: python

    >>> is_even = lambda x: x % 2 == 0
    >>> items = sorted(range(1000), key=is_even)
    >>> from itertools import groupby
    >>> odd, even = groupby(items, is_even)
    >>> odd[1].next()
    1
    >>> odd[1].next()
    3
    ...

Baby Turtles
------------

Use your powers wisely, and always remember...

.. image:: img/babyturtles.png
    :align: center

Magic Turtles!
--------------

It's turtles all the way down!

.. image:: img/magicturtle.jpg
    :align: center

Other great presentations about Python
---------------------------------------

* `Python & Stuff`_ by @japerk
* `Generator Tricks for Systems Programmers`_ by @dabaez
* `Python, Good to Great`_ by @jessenoller

.. _Python & Stuff: http://www.slideshare.net/japerk/python-stuff-10047724
.. _Generator Tricks for Systems Programmers: http://www.dabeaz.com/generators/
.. _Python, Good to Great: http://jessenoller.com/good-to-great-python-reads/

Lab Time
--------

Now it's time to explore a real Python web application that is using 
some of the best web prototyping technologies around. These include:

* Flask (web framework)
* Jinja (template engine)
* MongoDB (persistent database)
* Bootstrap (HTML/CSS boilerplate)
* jQuery (JavaScript library)

https://github.com/amontalenti/fastflask

https://github.com/amontalenti/fastflask/blob/master/README.rst


End
----

Fin!

Your host:

Andrew Montalenti, http://pixelmonkey.org

CTO, Parse.ly, http://parse.ly

Principal, Aleph Point, http://alephpoint.com

