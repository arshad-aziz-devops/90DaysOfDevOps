TASK 1
#!/bin/sh
shell: User interface to communicate with kernel. Every shell is itlself an interpreter.
Interpreter: A program that reads and executes code.
shebang: Very first line of code that tells kernal which interpreter to use to execute the script.
Without shebang, kernel fails to find an interpreter, and the calling shell (often /bin/sh) tries to interpret it.

Task 5: Combine It All
Create server_check.sh that:
Stores a service name in a variable (e.g., nginx, sshd)
Asks the user: "Do you want to check the status? (y/n)"
If y — runs systemctl status <service> and prints whether it's active or not
If n — prints "Skipped."

#!/bin/bash

read -p "Enter the service name" s_name

read -p "Do you want to check the status? (y/n)" choice

if [ $choice = y ];then

        :

elif [ $choice = n ];then

        echo "exiting"
        
        exit 1
        
fi

sudo systemctl status $s_name | awk '/Active/ {print $2}'
