# Playbooks are a way of automating tasks.  Using our VIM example
# from before lets re-install it.

# SPACING IS VERY IMPORTANT WITHIN PLAYBOOKS

# See playbook-1.yml

# To run a playbook issue it as follows

ansible-playbook -i hosts playbook-1.yml

# Since ansible gathers alot of data from the host during the "gathering facts" 
# TASK we can take advantage of that data in the playbook.  To see all that 
# data use the setup module.

ansible -m setup ansible_class_ubuntu_1  ### May want to pipe this through grep or less

# To filter these down to specific facts follow this syntax

ansible -m setup -a "filter=ansible_os_family" ansible_class_ubuntu_1
ansible -m setup -a "filter=ansible_os_family" all
ansible -m setup -a "filter=ansilbe_pkg_mgr" all
ansible -m setup -a "filter=ansible_memory_mb" ansible_class_ubuntu_1

# Lets modify the playbook so that the appropriate task will run based on the OS type. 
# To do this we will use the "when" clause and match an "ansible_os_family"

# See playbook-2.yml

# Now run this new playbook and see that it insttalls VIM on each different group even
# though the commands are different.

ansible-playbook -i hosts playbook-2.yml
