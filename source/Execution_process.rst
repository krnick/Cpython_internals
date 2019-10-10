===================
Python Execution Process
===================

Install the necessary debug tool
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: bash

    $ sudo apt-get install gdb python3.5-dbg
    $ gdb python3


1. Modules/Python.c (``break main``)

- copy argv
- sets locale
- calls Py_Main()

Memory Management
---------------------------

- PyMem\_ (Include/pymem.h, Objects/object.c)
- PyObject_memory

Py_Mem_Malloc() is based on malloc().

All of the python memory usages are based on ``malloc``, ``realloc``, ``free``

2. Modules/main.c (``break Py_Main``)

- _PyOS_Getopt
- Py_GETENV
- stdio
- Py_Initialize: like bootstrapping, initialize all internal modules (Python/pythonrun.c)
- run script / -m module / -c command

3. Objects/object.c (``break _PyObject_New``)

- Include/object.h
- Objects/object.c

Before next step, you need to run ``clear _PyObject_New``

Protocols in C
-----------------

- Include/abstract.c
- Objects/abstract.c

* Objects
* Buffer  tp_as_buffer
* Number tp_as_number
* Mapping tp_as_mapping
* Sequence tp_as_sequence


Reference Counting
------------------------

- Py_INCREF()
- Py_DECREF()

Does a null check:

- Py_XINCREF()
- Py_XDECREF(): 
- Py_CLEAR() 


PyObject_memory
-----------------------

Include/objimpl.h
Objects/obmalloc.c

PyObject\_ small block allocator

struct arena_object -> Link List -> 256k address

4k block -> struct pool_header

- Double-free problem
- Memory leak

PyEval_EvalFrameEx
---------------------------

Main execution function. The big eval loop with a big switch.

- Python/ceval.c

- stack-based
- It has register
- It has opcode

Issue 4753 opcode optimization.

.pyc
------

- Python/marshal.c module: serialization the python code
- Include/marshal.h

The magic tag will change each time pyc file changes.
Depends on time ``st_mtime`` of .pyc file.
