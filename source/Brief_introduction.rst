==================
Brief_introduction
==================

***************************
Project directory overview
***************************

- Doc: the manual
- Grammer: grammer is defined
- Include: the C headers
- Lib: the Python modules
- Modules: the C modules
- Objects: the builtin object(string, list, bool, tuple)
- Parser: grammer, lexer, parser, compiler
- Programs: the executable python program
- Python: the virtual machine

Python includes a compiler, interpreter.However, the compilation doesn't do much work.
After compilation, the source code would turn into bytecode,which is code object.

Code object Compiled by CPython compiler can not be directly
executed by the computer, it needs to be executed by the
virtual machine, which is, interpreter.

Also, the virtual machine is running on a stack, and each frame has its own data stack.
If not, we don't have the generator feature.

The reason that Python is called a dynamic language is that
many things are done when the program is running, such as type
checking.