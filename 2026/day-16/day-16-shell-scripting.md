TASK 1
#!/bin/sh
shell: User interface to communicate with kernel. Every shell is itlself an interpreter.
Interpreter: A program that reads and executes code.

shebang: Very first line of code that tells kernal which interpreter to use to execute the script.

Without shebang, kernel fails to find an interpreter, and the calling shell (often /bin/sh) tries to interpret it.
