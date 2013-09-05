finddupes
=========

Simple script to find duplicate files from a list of directories.

``finddupes.py`` is Python 3 compatible.

Install
--------

``finddupes.py`` requires the docopt module.  If present, it can use the
openpyxl module to output to an Excel spreadsheet.

.. code-block:: sh

   pip install docopt


Run
---------

::

    Find Duplicates

    Program to find duplicate files in a given file heirarchy.

    finddups.py will traverse a file heirarchy and print out, or save to an excel
    spreadsheet, a list of files that duplicates of each other.  Multiple
    may be specified on the command line separated by spaces.  Use quotes for
    direcotries that contain spaces.  If multiple directories are specified and
    one directory is a subfodler of another, there will be duplicate entries in
    the output.

    Usage:
      finddups.py [-hx <file>] <directory>...

    Options:
      -h --help               Show this screen
      --version               Show version
      -x <file> --xls=<file>  Write results to the file given in excel format

If Python isn't on your PATH or you're running on Windows, you will need to
specify the path to Python when you run ``finddupes.py``.  For example:

::

    C:\Python33\python.exe finddupes.py C:\Users\pacopablo "C:\Program Files"


Reason
-------

I initially wrote ``finddupes.py`` towards the beginning of the year to help
find files that could be deleted to free up some space.  The initial version
traversed the directory given and hashed every file it encountered.  This
works, but it's slow.  Especially when you have large files.

Recently, I was asked by a friend, who is just starting to learn Python, how
to convert doublesdetector.py_ to work with Python 3.3.2.  I started to look
at it and realized that I had already written something similar.  The main
difference being that doublesdetector.py_ only hashes files of the same size.
At once I realized my stupidity in bothering to hash every file.

Instead of updating doublesdetector.py_, I decided to modify ``finddupes.py`` to
only hash files of the same size like doublesdetector.py_.  Why did I not
modify doublesdetector.py_?  Mainly due to the nubmer of changes that would
need to be made.  Beyond the simple syntax changes for print statements, and
the replacement of the ``sha`` modules with the ``hashlib`` module,
doublesdetector.py_ as using the ``os.path.walk`` method which has been
deprecated for a while and is removed in Python 3.  After reworking
doublesdetector.py_ to use ``os.walk``, I would have basically ended up with
``finddupes.py``.

Since my friend is just learning Python, and programming in general, I plan on
adding comments explaining the code.  While ``finddupes.py`` might not be the
most "newbie" friendly code, it's relatively short, it does something
meaningful, and displays quite a few concepts.  Concepts such as:

 * Objects
 * loops
 * conditionals
 * dictionaries / hash tables
 * lazy loading
 * command line argument parsing (albeit easily with docopt)

Corrections, comments, suggestions, etc. will be greatly appreciated.





.. _doublesdetector.py: http://sebsauvage.net/python/doublesdetector.py
