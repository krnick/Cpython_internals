========
Debugging
========

.. code-block:: bash

    $ sudo apt-get install gdb python3.5-dbg

    $ gdb python3


1. Module/Python.c

- copy argv
- sets locale
- calls Py_Main

Memory Management

- PyMem\_ (Include/pymem.h, Objects/object.c)
- PyObject_memory

Py_Mem_Malloc(), based on malloc()

Just based on ``malloc``, ``realloc``, ``free``

2. Modules/main.c

