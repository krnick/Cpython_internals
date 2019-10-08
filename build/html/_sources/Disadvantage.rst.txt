============
Disadvantage
============

* GIL
* Dynamic type

Python does not check the type at the compile time until it is executed. Therefore, an exception may be thrown when encountering wrong type operations. However, although Python uses a dynamic type mechanism, it is also a strong type. Python prohibits operations that are not explicitly defined, such as numbers and strings.