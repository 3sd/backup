# Backup

Managed by https://github.com/3sd/ansible

Ensure a config file is available at `/etc/backup/pattern` that describes the files to be backed up in a format expected by rsync's `--filter` option, for example:

```
+ /etc
+ /home
- /home/*/.local/share/Trash
+ /var
- /var/cache
```

All directories should be specified relative to the root folder. Folders in the root folder are excluded unless they are explicity included. See the FILTER RULES section of the rsync man page for more details for more details on how to include/exclude directories to be backed up.
