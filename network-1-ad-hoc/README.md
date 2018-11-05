Some sample ad-hoc ansible commands.

ansible all -c local -m ping

ansible all -c local -m ios_facts -a "username=vagrant password=vagrant gather_subset=hardware"

ansible all -c local -m ios_command -a "username=vagrant password=vagrant auth_pass=vagrant authorize=true commands='show run'"


