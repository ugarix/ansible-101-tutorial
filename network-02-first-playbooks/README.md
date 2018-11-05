# These playbooks are built from samples from Brad and 
# https://www.reddit.com/r/networking/comments/6ljtpo/bossing_cisco_around_with_ansible/

# 01-show-int-brief.yaml
This shows how to get interface output.

# 02-create-acl.yaml
This shows how to create an acl and apply it to an interface.  It will show what
exists before and after the ACL creation.

# 03-show-run.yaml
This will show the running config of routers

# 04-config-backup.yaml
This utilizes the built in config-backup module to save the config to file

# 05-config-backup-renamed.yaml
This is a manual way of getting the running config, saving to a variable, then copying the
variable to an output file.
