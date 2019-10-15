+++++++++++++++++++
Frame_object
+++++++++++++++++++

Each of function call is also called frame
and each function has own frame and stack

_frame

PyFrameObject

the python interpreter maintain threads as PyThreadStates.
Each PyThreadState keeps track of the top of its stack
the stack is just a linked list of PyFrameObject
PyFrameObject is the basic unit of bytecode evaluation
Each frame uses its own stack to perform code execution

https://www.youtube.com/watch?v=smiL_aV1SOc
https://www.youtube.com/watch?v=cSSpnq362Bk
