+++++++++++++++++++
Python_object
+++++++++++++++++++

`PyObject Definitions <https://github.com/python/cpython/blob/f7d72e48fb235684e17668a1e5107e6b0dab7b80/Include/object.h#L104-L108>`_

.. code-block:: c

    typedef struct _object {
        _PyObject_HEAD_EXTRA
        Py_ssize_t ob_refcnt;
        struct _typeobject *ob_type;
    } PyObject;

Everything in Python is an object. Objects in C are represented
by contiguous memories and are using a large number of macro
definitions. Because there is no inheritance in C, so put the macro
again in the place where you need to use inheritance.

Using ``dir()`` function to inspect what inside is.

>>> dir(123)
['__abs__', '__add__', '__and__', '__bool__', '__ceil__', '__class__', '__delattr__', '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floor__', '__floordiv__', '__format__', '__ge__', '__getattribute__', '__getnewargs__', '__gt__', '__hash__', '__index__', '__init__', '__init_subclass__', '__int__', '__invert__', '__le__', '__lshift__', '__lt__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__or__', '__pos__', '__pow__', '__radd__', '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__', '__rfloordiv__', '__rlshift__', '__rmod__', '__rmul__', '__ror__', '__round__', '__rpow__', '__rrshift__', '__rshift__', '__rsub__', '__rtruediv__', '__rxor__', '__setattr__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__trunc__', '__xor__', 'bit_length', 'conjugate', 'denominator', 'from_bytes', 'imag', 'numerator', 'real', 'to_bytes']

>>> dir("Python")
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']

Return the memory of an object

>>> id("Python")
4331023408

Each object has a reference count, if count reaches zero, it means no one
is going to refer to it, then it will be garbage collected.

PyTypeObject
-----------------

`/Include/cpython/object.h <https://github.com/python/cpython/blob/b2f94730d947f25b8507c5f76202e917683e76f7/Include/cpython/object.h>`_

.. code-block:: c

    typedef struct _typeobject {
        PyObject_VAR_HEAD
        const char *tp_name; /* For printing, in format "<module>.<name>" */
        Py_ssize_t tp_basicsize, tp_itemsize; /* For allocation */

        /* Methods to implement standard operations */

        destructor tp_dealloc;
        Py_ssize_t tp_vectorcall_offset;
        getattrfunc tp_getattr;
        setattrfunc tp_setattr;
        PyAsyncMethods *tp_as_async; /* formerly known as tp_compare (Python 2)
                                        or tp_reserved (Python 3) */
        reprfunc tp_repr;

        /* Method suites for standard classes */

        PyNumberMethods *tp_as_number;
        PySequenceMethods *tp_as_sequence;
        PyMappingMethods *tp_as_mapping;

        /* More standard operations (here for binary compatibility) */

        hashfunc tp_hash;
        ternaryfunc tp_call;
        reprfunc tp_str;
        getattrofunc tp_getattro;
        setattrofunc tp_setattro;

        /* Functions to access object as input/output buffer */
        PyBufferProcs *tp_as_buffer;

        /* Flags to define presence of optional/expanded features */
        unsigned long tp_flags;

        const char *tp_doc; /* Documentation string */

        /* Assigned meaning in release 2.0 */
        /* call function for all accessible objects */
        traverseproc tp_traverse;

        /* delete references to contained objects */
        inquiry tp_clear;

        /* Assigned meaning in release 2.1 */
        /* rich comparisons */
        richcmpfunc tp_richcompare;

        /* weak reference enabler */
        Py_ssize_t tp_weaklistoffset;

        /* Iterators */
        getiterfunc tp_iter;
        iternextfunc tp_iternext;

        /* Attribute descriptor and subclassing stuff */
        struct PyMethodDef *tp_methods;
        struct PyMemberDef *tp_members;
        struct PyGetSetDef *tp_getset;
        struct _typeobject *tp_base;
        PyObject *tp_dict;
        descrgetfunc tp_descr_get;
        descrsetfunc tp_descr_set;
        Py_ssize_t tp_dictoffset;
        initproc tp_init;
        allocfunc tp_alloc;
        newfunc tp_new;
        freefunc tp_free; /* Low-level free-memory routine */
        inquiry tp_is_gc; /* For PyObject_IS_GC */
        PyObject *tp_bases;
        PyObject *tp_mro; /* method resolution order */
        PyObject *tp_cache;
        PyObject *tp_subclasses;
        PyObject *tp_weaklist;
        destructor tp_del;

        /* Type attribute cache version tag. Added in version 2.6 */
        unsigned int tp_version_tag;

        destructor tp_finalize;
        vectorcallfunc tp_vectorcall;

    #ifdef COUNT_ALLOCS
        /* these must be last and never explicitly initialized */
        Py_ssize_t tp_allocs;
        Py_ssize_t tp_frees;
        Py_ssize_t tp_maxalloc;
        struct _typeobject *tp_prev;
        struct _typeobject *tp_next;
    #endif
    } PyTypeObject;



