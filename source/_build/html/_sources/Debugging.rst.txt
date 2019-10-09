========
Debugging
========

.. code-block:: bash

    $ sudo apt-get install gdb python3.5-dbg

    $ gdb python3


1. Modules/Python.c (``break main``)

- copy argv
- sets locale
- calls Py_Main

Memory Management

- PyMem\_ (Include/pymem.h, Objects/object.c)
- PyObject_memory

Py_Mem_Malloc(), based on malloc()

Just based on ``malloc``, ``realloc``, ``free``

2. Modules/main.c (``break Py_Main``)

_PyOS_Getopt
Py_GETENV
stdio
Py_Initialize: like bootstrapping, initialize all internal modules
run script / -m module / -c command

3. Objects/object.c (``break _PyObject_New``)

before next step, you need to run ``clear _PyObject_New``

PyObject: Include/object.h, Objects/object.c

Protocol in C

Include/abstract.c, Objects/abstract.c






