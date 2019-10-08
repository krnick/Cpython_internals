==================
Interpreter_vs_Compiler
==================

The main difference between the compiler and the interpreter

* The compiler translates the whole program, but the interpreter translates the program line by line.
* The compiler is relatively faster than the interpreter because the interpreter executes on a non-native virtual environment.
* To store object code, the compiler requires more memory than the interpreter.
* The compiler will display all errors at the same time, while the interpreter will display the error of each error line by line.

Compiler
-----------

In short, the compiler compiles the code into a machine code that can be executed directly by the computer.
It is usually called executable file, and the process will also do the type check, so no source
code is needed when executing. Therefore, the job of the compiler is to translate, translate into a language that the computer can understand

Interpreter
-------------

It reads the program first, translates it into the code
corresponding to the virtual machine, known as
bytecode, so we do not know what the type
is, only when running the program to know, this
also, lead to the so-called dynamic type checking,
further called dynamic language.


Commonality
----------------

Both the compiler and the interpreter will convert the original file into tokens, which will generate AST, and will also generate the intermediate code, but the compiler produces the **machine code**, the interpreter produces the instruction set is to be executed for the virtual machine.


+--------------------------------------------------------+-------------------------------------------------------------------------------------------------------+--+
| Interpreter                                            | Compiler                                                                                              |  |
+========================================================+=======================================================================================================+==+
| Line by line when executing                            | The whole file scanning                                                                               |  |
+--------------------------------------------------------+-------------------------------------------------------------------------------------------------------+--+
| Overall time is longer                                 | It takes a lot of time to analyze the source code, but the overall execution time is relatively fast. |  |
+--------------------------------------------------------+-------------------------------------------------------------------------------------------------------+--+
| No object code is generated, so it is memory efficient | Generate object code that needs further links, so more memory is needed                               |  |
+--------------------------------------------------------+-------------------------------------------------------------------------------------------------------+--+

Example
-----------

* Java is compiled into bytecode and then executed by the JVM.

* C language is compiled into object code, and then becomes the executable file after the linker

* Python is first converted to the bytecode and then executed via ceval.c. The interpreter directly executes the translated instruction set.