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
   However, the port is hardcoded in the playbook. Update the playbook to replace the hardcoded value of the SNMP port to use the value from the variable named snmp_port.

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
             port: '161'
             permanent: true
             state: disabled
       ```

 6) The file variable03.yaml playbook is printing some personal information of an employee. We would like to move the car_model, country_name and title values to the 
    respective variables, and these variables should be defined at the playbook level.
    Add three new variables named car_model, country_name and title under the playbook and move the values over there. Use these variables within the task to remove the 
    hardcoded values.

     ```
     ---
     - hosts: localhost
       tasks:
         - command: 'echo "My car is BMW M3"'
         - command: 'echo "I live in the USA"'
         - command: 'echo "I work as a Systems Engineer"'
     ```

7)  The file variable04.yaml playbook is responsible for installing a list of packages on a remote server(s). The list of packages to be installed is already added to the 
 /home/bob/playbooks/inventory file as a list variable called app_list.

    ```
    ---
    - hosts: all
      become: yes
      tasks:
        - name: Install applications
          yum:
            name: "{{ item }}"
            state: present
          with_items:
            - vim
            - sqlite
            - jq
       ```

    Right now the list of packages to be installed is hardcoded in the playbook. Update the variable04.yaml playbook to replace the hardcoded list of 
    packages to use the values from the app_list variable defined in the inventory file.

