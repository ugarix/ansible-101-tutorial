These two playbooks demonstrate different ways to backup configs.

## 01-config-backup.yaml
This utilizes the built in config-backup module to save the config to file
```
ansible-playbook 01-config-backup.yaml
```

## 02-config-backup-renamed.yaml
This is a manual way of getting the running config, saving to a variable, then copying the
variable to an output file.
```
ansible-playbook 02-config-backup-renamed.yaml
```
