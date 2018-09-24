# Host configuration

For hosts that are backed up.

Managed by https://github.com/3sd/ansible backed-up role

Ensure a `/etc/backup/pattern` config file is present that describes the files to be backed up. This is passed to rysnc as `--filter="merge /etc/backup/pattern"`.

```
+ /etc
+ /home
- /home/*/.local/share/Trash
+ /var
- /var/cache
```

All directories should be specified relative to the root folder. Folders in the root folder are excluded unless they are explicity included.

See the FILTER RULES section of the rsync man page for more details for more details on how to define the directories to be backed up.

# Server configuration

For servers that store backups.

Managed by https://github.com/3sd/ansible backup role.

Ensure a `/etc/backup/hosts` file is present that describes the hosts for which backups should be collected. The host name will be used as the backup directory name.

Hosts can reference a host definition in `/root/.ssh/config`. This enables you to specify ssh keys, bastion hosts, etc. for each connection. Note that the remote user should be able to run `sudo rysnc` on the host to be backed up.
