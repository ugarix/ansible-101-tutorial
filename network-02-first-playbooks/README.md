These playbooks are built from samples from Brad and https://www.reddit.com/r/networking/comments/6ljtpo/bossing_cisco_around_with_ansible/

## 01-show-int-brief.yaml 
This shows how to get interface output.
```
ansible-playbook 01-show-int-brief.yaml
```
## 02-create-acl.yaml
This shows how to create an acl and apply it to an interface.  It will show what
exists before and after the ACL creation.
```
ansible-playbook 02-create-acl.yaml
```

## 03-show-run.yaml
This will show the running config of routers
```
ansible-playbook 03-show-run.yaml
```
