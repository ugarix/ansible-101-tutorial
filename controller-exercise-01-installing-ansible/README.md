Connect to the docker controller container from the host as follows
```
docker exec -i ansible_class_ansiblecontroller_1 /bin/bash
```
You should notice the prompt change
From here you are issuing commands from within the container.

You will be logged in as root by default.  If root credentials are needed the pass is "pass"
```
apt update
apt install software-properties-common
apt-add-repository ppa:ansible/ansible
apt update
apt install ansible
```
Once those tasks have completed generate a key on the ansible controller.  This will be used to log into the other containers.  Accept the defaults here and don't set a password.  Copy the key to the  other containers.
```
ssh-keygen
ssh-copy-id ansible_class_ubuntu_1  ### Password is "pass" when prompted
ssh-copy-id ansible_class_ubuntu_2  ### Password is "pass" when prompted
ssh-copy-id ansible_class_centos7_1 ### Password is "pass" when prompted
ssh-copy-id ansible_class_centos7_2 ### Password is "pass" when prompted
```
At this point you should have the following
1. 5 Docker containers running.  2 are ubuntu and 2 are centos
2. Ansible installed on the controller container
3. The ansible controller has connectivity to the containers
