# It's also possible to have grouping within an inventory file.  Observe
# the "hosts" file below.  Two groups have been defined then a parent group
# of "servers" that has two children.  We have also introduced the "vars" 
# attribute.  The vars can be referenced in playbooks later.

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

# A sample task that utilizes this configuration is as follows. It's more advanced
# and was pulled from the internet.  It first removes chrony, if installed, then installs
# ntp.  Then it copies over a Jinja template that utilizes a for loop to assign NTP servers.

# Files:
#  ntp-playbook.yml
#  ntp-template.yml
