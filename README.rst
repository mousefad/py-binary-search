Binary Search Tool
==================

Provides a time-efficient method for searching for values in some specified key field
in large files that are sorted on that key field.

The program uses a binary search method.

Fields may be specified as delimited of fixed column values within a record.

.. code-block:: shell
 ❯ ls -lh tags
 -rw-r--r--. 2 mouse mouse 1.1G Jul 20 20:04 tags
 
 ❯ time ./bsearch ssize_t tags > /dev/null
 ./bsearch ssize_t tags > /dev/null  0.07s user 0.00s system 98% cpu 0.079 total
 
 ❯ time grep "^ssize_t   " tags > /dev/null
 grep --color=auto "^ssize_t     " tags > /dev/null  0.19s user 0.11s system 99% cpu 0.302 total

Running out of memory
---------------------

This program can exhaust your RAM pretty easily if you pass it a huge file. Python 2.x 
handles huge files less well than Python 3.x (difference in ``mmap`` implementation?).

Some desktop Linux distros to not apply ulimits for memory usage at all, and so this 
program could easily crash your user session if you pass it a huge file!

