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
