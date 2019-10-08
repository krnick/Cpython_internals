=========
Compiling
=========

1. Python code -> Parse tree
2. Parse tree -> AST
3. Symbol table
4. Code object
5. Flow control graph
6. Code obejct optimization
7. Result


*******************
1. Decoding & Lexer
*******************

* Parser/tokenizer.c -> PyTokenizer_FromString
* Parser/parsetok.c -> parsetok
* Lib/tokenize.py

*************
2. Tokenizing
*************

**********
3. Parsing
**********

* Python/pythonrun.c -> PyParser_ASTFromStringObject

.. code-block:: python

    import parser
    code = "x = 2 + 2"
    st = parser.suite(code)
    print(parser.st2list(st))

`LL_parser <https://en.wikipedia.org/wiki/LL_parser>`_

******
4. AST
******

.. code-block:: python

    import dis
    import ast
    tree = ast.parse("x=2+2")                       
    print(type(ast.dump(tree)))

***********
5. Compiler
***********

.. code-block:: python

    import dis
    import ast
    tree = ast.parse("x=2+2")
    code_obejct = compile(tree,'test.py',mode='exec')
    dis.dis(code_obejct)