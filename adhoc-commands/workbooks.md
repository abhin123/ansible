1. Ping All Hosts
   To check if all hosts in your inventory are reachable, use the ping module:
   ```
   ansible all -m ping
   ```
   
2. Run a Command on Remote Hosts
   To execute a command on all hosts, use the shell or command module. For example, to list files in the /tmp directory:
   ```
    ansible all -m shell -a 'ls /tmp'
   ```

3. Install a Package
   To install a package on all hosts, use the apt module for Debian-based systems or the yum module for RedHat-based systems. For example, to install vim:

   For Debian-based systems:
   ```
   ansible all -m apt -a 'name=vim state=present' -b
   ```
   For RedHat-based systems:
   ```
   ansible all -m yum -a 'name=vim state=present' -b
   ```

4. Create a Directory
   To create a directory on remote hosts, use the file module:
   ```
   ansible all -m file -a 'path=/tmp/newdir state=directory' -b
   ```
   
5. Copy a File
   To copy a file from the local machine to remote hosts, use the copy module. For example, to copy myfile.txt to /tmp:
   ```
   ansible all -m copy -a 'src=myfile.txt dest=/tmp/myfile.txt'
   ```

6. Update System Packages
   To update all packages on Debian-based systems, use the apt module:
   ```
   ansible all -m apt -a 'upgrade=dist' -b
   ```
   For RedHat-based systems, you might use:
   ```
   ansible all -m yum -a 'name=* state=latest' -b
   ```
7. Start a Service
   To start a service on remote hosts, use the service module. For example, to start the nginx service:
   ```
   ansible all -m service -a 'name=nginx state=started' -b
   ```
8. Restart a Service
   To restart a service, use the service module. For example, to restart nginx:
   ```
   ansible all -m service -a 'name=nginx state=restarted' -b
   ```

9. Remove a Package
   To remove a package from all hosts, use the apt or yum module. For example, to remove vim:
   For Debian-based systems:
   ```
   ansible all -m apt -a 'name=vim state=absent' -b
   ```
    For RedHat-based systems:
    ```
    ansible all -m yum -a 'name=vim state=absent' -b
    ```
10. Check Disk Usage
    To check disk usage, you can use the shell module to run a command like df -h:
    ```
    ansible all -m shell -a 'df -h'
    ```

11. Retrieve a File from Remote Hosts
    To fetch a file from remote hosts, use the fetch module. For example, to fetch /tmp/myfile.txt from remote hosts to the local directory /tmp/:
    ```
    ansible all -m fetch -a 'src=/tmp/myfile.txt dest=/tmp/ flat=yes'
    ```
    
12. Manage Users
    To create a user on remote hosts, use the user module. For example, to create a user newuser:
    ```
    ansible all -m user -a 'name=newuser state=present' -b
    ```

13. Execute a Command as a Specific User
    To execute a command as a specific user, use the become option with the -b flag. For example, to list files in /root as the root user

    ```
    ansible all -m shell -a 'ls /root' -b -u root
    ```

14. Check Free Memory
    To check free memory on remote hosts, use the shell module to run free -m
    ```
    ansible all -m shell -a 'free -m'
    ```

15. Gather System Facts
    To gather facts about all hosts (like hostname, OS, and more), use the setup module:
     ```
     ansible all -m setup
     ```
