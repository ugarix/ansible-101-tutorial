# Before building our first inventory file we can run some ad-hoc commands to
# verify connectivity.

ansible -m ping ansible_class_ubuntu_1
ansible -m ping ansible_class_ubuntu_2
ansible -m ping ansible_class_centos7_1
ansible -m ping ansible_class_centos7_2

# A "pong" should come back from each of these.  This validates that our 
# topology is working properly, ssh keys are installed, and ansible is 
# working.  There are many other built-in ansible modules which docs 
# are located at https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html
#
# Custom modules can also be written to extend functionality.

# By default ansible looks in /etc/ansible for it's configuration files.  This lab will run
# everything from the current directory to make exercise changes eaiser. 

# Create a hosts file with the following contents. See hosts-1 in the folder

[deb]
ansible_class_ubuntu_1
ansible_class_ubuntu_2

[rpm]
ansible_class_centos7_1
ansible_class_centos7_2

# This defines two groups.  One is the list of servers running debian and the other is CentOS
# based.  Grouping for this example is done based on the package format. You can run ad-hoc
# commands against a group from the hosts file as well.

ansible -m ping -i hosts-1 deb
ansible -m ping -i hosts-1 rpm

# It's also likely that a device under management can be a member of multiple groups.  Now 
# modify the hosts file to add dbservers & webservers.  Include one of each different
# OS in each new group. See hosts-2 in the folder

[dbservers]
ansible_class_ubuntu_1
ansible_class_centos7_1

[webservers]
ansible_class_ubuntu_2
ansible_class_centos7_2

# With this in place we can also run commands on all systems that are webservers and dbservers too
