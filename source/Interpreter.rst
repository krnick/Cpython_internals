+++++++++++++++++++
Interpreter
+++++++++++++++++++

CPython's Virtual Machine

Code evaluator : `ceval.c <https://github.com/python/cpython/blob/master/Python/ceval.c>`_

The so-called Interpreter is just a huge `loop <https://github.com/python/cpython/blob/4d5f94b8cd20f804c7868c5395a15aa6032f874c/Python/ceval.c#L1183-L1184>`_.

* `opcode.h <https://github.com/python/cpython/blob/master/Include/opcode.h>`_
* `code.h <https://github.com/krnick/cpython/blob/master/Include/code.h>`_ 

.. code-block:: bash

    $ python test.py

Python needs to turn test.py into something that can be executed,
so what is that? That is bytecode.

The way Python actually executes is that there are multiple cases
in a loop, which correspond to different instructions.

