It's also possible to have grouping within an inventory file.  Observe the "hosts" file below.  Two groups have been defined then a parent group of "servers" that has two children.  We have also introduced the "vars" attribute.  The vars can be referenced in playbooks later.
```
[deb]
ansible_class_ubuntu_1
ansible_class_ubuntu_2

[rpm]
ansible_class_centos7_1
ansible_class_centos7_2

[nodes:children]
deb
rpm

[nodes:vars]
ntp_server_1=0.us.pool.ntp.org
ntp_server_2=1.us.pool.ntp.org
ntp_server_3=2.us.pool.ntp.org
ntp_server_4=3.us.pool.ntp.org
```
A sample task that utilizes this configuration is as follows. It's more advanced and was pulled from the internet.  It first removes chrony, if installed, then installs ntp.  Then it copies over a Jinja template that utilizes a for loop to assign NTP servers.
```
Files:
 ntp-playbook.yml
 ntp-template.yml
```
To run the playbook issue
```
ansible-playbook -i hosts ntp-playbook.yml
```
The status can be validated by checking the time synchronization with an ad-hoc command that can be ran on all the containers at once.
```
ansible -i hosts -m shell -a "ntpq -p" nodes
```
Next we'll deploy a web server to one of the CentOS & Ubuntu VMs.  The first step is to define these servers by adding the new groups to our existing inventory file.  
```
[webservers]
ansible_class_ubuntu_2
ansible_class_centos7_2
```
To run the playbook issue
```
ansible-playbook -i hosts webserver.yml
```
Now we'll modify the playbook (or create a new one: web_and_database_1.yml) that will deploy mariadb to a single server.  This is to demonstrate that playbooks can be mixed via groups and individual hosts.
```
ansible-playbook -i hosts web_and_database_1.yml
```
Lastly, we will modify the playbook (or create a new one: web_and_database_2.yml) that will deploy mariadb to the other container and show the output of a CLI command to verify if it's running or not.  The first time the playbook is run the service will not be running due to order of operations.  Running the playbook again will demonstrate that it's running by looking at the file output.
```
ansible-playbook -i hosts web_and_database_2.yml
```
Then cat the status file
```
cat mysqlstatus.txt
```
We can also utilize the tags that were added on the 2nd run to make the process qicker.  
```
ansible-playbook -i hosts web_and_database_2.yml --tags mysqlstatus
```
