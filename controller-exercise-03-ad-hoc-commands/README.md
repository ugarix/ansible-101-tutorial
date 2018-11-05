# Beyond reading the doc website they are also provided with the installation.

ansible-doc -l
ansible-doc user
ansible-doc apt
ansible-doc ping

# If we would like to quickly upgrade all of our debian's APT cache via the
# ad-hoc method we could run the following command.

ansible -i hosts -m apt -a "update_cache=yes" deb

# To install VIM on all our debian servers we would use the following. 

ansible -i hosts -m apt -a "name=vim state=present" deb

# There is logic built into the module as well.  If you rerun that same command
# it will indicate "changed": "false" for both debian servers.

# Modules can be removed as well.  Lets remove VIM

ansible -i hosts -m apt -a "name=vim state=absent" deb
