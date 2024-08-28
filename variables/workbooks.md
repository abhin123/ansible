1) Can we define variables in an Ansible inventory file?
2) Can we define variables in an Ansible playbook?
3) Which of the following formats is used to call a variable in an Ansible playbook?

   a) '(variable_name)'
   b) '{variable_name}'
   c) '((variable_name))'
   d) '{{variable_name}}'

4) The file variable01.yaml playbook is adding a name server entry in /tmp/resolv.conf sample file on localhost.
   The name server information is already added to the /home/bob/playbooks/inventory file as a variable called nameserver_ip.
    Replace the hardcoded ip address of the name server in this playbook to use the value from the variable defined in the inventory file.
   
     ```
     ---
     - name: 'Add nameserver in resolv.conf file on localhost'
       hosts: localhost
       become: yes
       tasks:
         - name: 'Add nameserver in resolv.conf file'
           lineinfile:
             path: /tmp/resolv.conf
             line: 'nameserver 8.8.8.8'
      ```
5) The file variable02.yaml playbook is to add a new task to disable SNMP port on localhost.
   However, the port is hardcoded in the playbook. Update the playbook to replace the hardcoded value of the SNMP port to use the value from the variable named snmp_port, defined in the inventory file.

     ```
     ---
     - name: 'Add nameserver in resolv.conf file on localhost'
       hosts: localhost
       become: yes
       tasks:
         - name: 'Add nameserver in resolv.conf file'
           lineinfile:
             path: /tmp/resolv.conf
             line: 'nameserver {{  nameserver_ip  }}'
         - name: 'Disable SNMP Port'
           firewalld:
             port: '160-161'
             permanent: true
             state: disabled
       ```


