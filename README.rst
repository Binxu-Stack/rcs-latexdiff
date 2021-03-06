rcs-latexdiff
#############

rcs-latexdiff is a simple tool to generate a diff of a LaTeX file contained in a Revision Control System (like Git, Mercurial, etc.).
The result is a LaTeX file with the differences between two revisions of a file.
Then, you just have to compile the diff file using your favorite LaTeX compiler (rubber, pdflatex, etc.).

Dependencies:
    * `latexdiff <http://www.ctan.org/tex-archive/support/latexdiff>`_ tool
    * `Python <http://www.python.org/>`_ 

Features:
    * Support of Git, SVN
    * Diff of a LaTeX File for different versions
    * Recursive search of files included

Install 
-------
First, grab sources::

    $ git clone https://github.com/driquet/rcs-latexdiff.git
    $ cd rcs-latexdiff

You may want to install rcs-latexdiff in a virtualenv ; following steps explain how to do it::

    $ virtualenv --prompt==rcs-latexdiff venv
    $ source venv/bin/activate
    $ python setup.py install

If you want to install rcs-latexdiff system wide, just skip the first two steps.

Usage 
-----
Basic usage is::
    
    $ rcs-latexdiff [OPTIONS] filename old_commit new_commit

The complete usage can be displayed with option `-h`.


Examples
--------
For example, if the file `paper.tex` is in a Git repository, you could do::

    $ rcs-latexdiff paper.tex HEAD~1 HEAD

to get a diff between the second to last and the last commit.

You could also use branch names.
For example, to compare a version submitted to a conference and the final version::
    $ rcs-latexdiff paper.tex submission-version camera-ready-version

If you want a diff between changes in the current working directory and the last commit, you can do::

    $ rcs-latexdiff paper.tex HEAD

Troubles
--------
No graphics or bibliography when compiling LaTeX file
    Verify that missing elements are in the path. The simpler is to generate the diff file next to the original file.

Diff file won't compile
    It could be due to exotic document class of LaTeX files. Again, verify that all elements are in the path.

rcs-latexdiff is slow for SVN
    Not rcs-latexdiff's fault, really. SVN is server-based, so it needs to discuss with the server for most operations and it could be pretty long.

Contribute
----------
You may want to add another RCS software.
You can fork and pull request to complete this tool.

Licence
-------
GPLv3.
See LICENCE file.

Contributors
------------
Damien Riquet <d.riquet@gmail.com>
