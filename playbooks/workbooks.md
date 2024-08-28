1) How many Ansible plays are there in the following given playbook?
     ```
     ---
     - name: Setup apache
       hosts: webserver
       tasks:
         - name: install httpd
           yum:
             name: httpd
             state: installed
         - name: Start service
           service:
             name: httpd
             state: started

     - name: Setup tomcat
       hosts: appserver
       tasks:
         - name: install httpd
           yum:
             name: tomcat
             state: installed
         - name: Start service
           service:
             name: tomcat
             state: started
     ```

 2) If we use the following inventory, on which hosts will Ansible install the httpd package using the given playbook?

   ```
   [webserver]
   web1
   web2
   [appserver]
   app1
   app2
   app3
   ```

   ```
    ---
     - name: Setup apache
       hosts: webserver
       tasks:
         - name: install httpd
           yum:
             name: httpd
             state: installed

     - name: Setup tomcat
       hosts: appserver
       tasks:
         - name: install httpd
           yum:
             name: tomcat
             state: installed
     ```


  3) Run a playbook to display the contents of the file `/etc/hosts` 

  4) Run a playbook to Execute a date command and display the contents of the file `/etc/hosts`. These task should be run against the remote node

  5) Run a playbook to Check Disk Usage on Linux and print the disk usage.
