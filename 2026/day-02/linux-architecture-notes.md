The core components of Linux OS are: kernel, user-space, systemd,shell, System Libraris, System Utilities.

OS is special kind of software with the help of that we can manage,communicate and access the hardware. OS can be divided broadly into two parts.
One is user space and another is kernel space.

Kernel: The core part of linux with that OS access and communicate with the hardware. Kernel is responsible for directly manageimg system resources like
process management, memory management, File system management and network management.

User Space: This is region where applications run, user intercation happens through shell, shell is also exists in this part. Shell is the C interpreter that
takes input and translate those input that can be understand by kernel. 
User space program or application cannot directly access hardware or manages system resources like file/memory or network management. They need kernel help. So, in kernel there are something called system calls. These system called are used by user space prog or apps to access kernel. Then kernel can perform those system calls operations. 
System calls: Thesre are the interface for user space to access kernel.It is meachanism through a user space prog or apps request a service from kernel.
System Libraries: These are pre-written code that user space prog uses to perform tasks like i/o,file management, networking etc.
How things flow from user space to hardware:
Lets take example of simple ls. ( listing)
Shell --> System Libraries --> System call --> Kernel --> Hardware
When you enetr ls in shell, ls is a prog that executes. It then calls system library (glibc). System lib then calls system calls to launch ls as child process
and to access kernel to read directories. Here as system call gets triggered there is chnage of CPU from user mode to kernel mode. Finally kernel executes the tasks and give result back to user space.

