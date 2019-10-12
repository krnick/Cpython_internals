======
Bytecode
======

Bytecode definition: https://docs.python.org/3/library/dis.html

stack based


``dis`` module: https://docs.python.org/3/library/dis.html

``dis`` module could show us the disassembling bytecode from Python code, and the bytecode will map to the `opcode.h <https://github.com/python/cpython/blob/master/Include/opcode.h>`_

You can write some code like below:

.. code-block:: python

    x = 1+1
    y = x+2
    print(y)

save it to **test.py** and then back to the command line 
typing ``python3 -m dis test.py``

.. image:: image/dis_module.png


pyc
----

pyc is sort of bytecode that putting on disk,and
a sequence of instructions for machine to run.

When Python program runs, the bytecode is temporarily stored
in the PyCodeObject in the memory. Once the Python
program ends, the Python interpreter writes the PyCodeObject
to the ``.pyc`` file.

We can also execute directly through pyc file: ``python xxx.pyc``

When the Python program is executed for the second time, it will
first look for the .pyc file in the current directory. If it is found, it will
be loaded directly. If it is not found, repeat the above process.

If Python finds that Python's source code has been modified, it will
check the timestamp. In short, it is to determine the update time of
the two files before deciding whether to compile or load directly.

.. seealso:: `Scott Sanderson, Joe Jevnik - Playing with Python Bytecode - PyCon 2016 <https://www.youtube.com/watch?v=mxjv9KqzwjI&feature=youtu.be>`_

