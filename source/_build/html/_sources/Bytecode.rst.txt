+++++++++++++++++++
Bytecode
+++++++++++++++++++

Bytecode definition: https://docs.python.org/3/library/dis.html


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

.. seealso:: `Scott Sanderson, Joe Jevnik - Playing with Python Bytecode - PyCon 2016 <https://www.youtube.com/watch?v=mxjv9KqzwjI&feature=youtu.be>`_

