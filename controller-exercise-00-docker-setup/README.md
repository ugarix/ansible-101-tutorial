# Docker build for enviornment

The setup.sh script might be able to be run from a server with apt package manager.

It's preferred to do the following steps.

Install docker-ce

'docker network create ansible_class_default'
'docker-compose -p ansible_class scale centos7=2 ubuntu=2 ansiblecontroller=1'

You can get the status of your containers by issuing

'docker ps [--all]'

To log into the controller container issue

'docer exec -it ansible_class_ansiblecontroller_1 /bin/bash'

Log out of this container just like any other unix based system

When you are finished you can stop your containers

'docker stop ansible_class_ansiblecontroller_1'
'docker stop ansible_class_ubuntu_1'
'docker stop ansible_class_ubuntu_2'
'docker stop ansible_class_centos7_1'
'docker stop ansible_class_centos7_1'

To start them again issue 

'docker start <container_name>'

To destroy the containers and any data within them

'docker rm -f <container_name>'

