Task 4: Install Packages via Script
Create install_packages.sh that:
Defines a list of packages: nginx, curl, wget
Loops through the list
Checks if each package is installed (use dpkg -s or rpm -q)
Installs it if missing, skips if already present
Prints status for each package

#!/bin/bash

services=(nginx curl wget)

for i in ${services[@]}; do

        if dpkg -s $i &>/dev/null; then
                echo " $i is Installed"
        else
                echo " $i is not installed"
                echo "Starting installing..."
                sudo apt install $i -y 1>/dev/null
                        if [ $? -eq 0 ];then
                                echo "install $i sucess"
                        else
                                echo "failed"
                        fi
        fi


done

#!/bin/bash

services=(nginx curl wget apache2)

for i in ${services[@]}; do

         dpkg -s $i &> /dev/null || { echo "insatlling $i..."; sudo apt install $i -y 1> /dev/null; }
done

for i in ${services[@]}; do

        dpkg -s $i &> /dev/null && echo " $i is insatlled" || echo "$i is not installed"
done

Task 5: Error Handling
Create safe_script.sh that:
Uses set -e at the top (exit on error)
Tries to create a directory /tmp/devops-test
Tries to navigate into it
Creates a file inside
Uses || operator to print an error if any step fails


Modify your install_packages.sh to check if the script is being run as root — exit with a message if not.

#!/bin/bash

idx=`whoami`

if [ $idx != "root" ];then
        echo "Not runnng as root"
        exit 1
else
        echo "running as root"
fi

services=(nginx curl wget)

for i in ${services[@]}; do

        if dpkg -s $i &>/dev/null; then
                echo " $i is Installed"
        else
                echo " $i is not installed"
                echo "Starting installing..."
                sudo apt install $i -y 1>/dev/null
                        if [ $? -eq 0 ];then
                                echo "install $i sucess"
                        else
                                echo "failed"
                        fi
        fi


done
