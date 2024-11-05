# linux-cheat-sheet

## Index

- [Copying a file or a list of files via jumpstart](#copying-a-file-or-a-list-of-files-via-jumpstart)
- [Generating SSH keys to avoid password prompts](#generating-ssh-keys-to-avoid-password-prompts)


## Copying a file or a list of files via jumpstart

```bash
#!/bin/bash

# Define variables
SOURCE="ubuntu@172.16.10.30:/var/log/spring/spring-api-0/archived/spring-api-0-2024-11-03_*.log.gz"
LOCAL_DEST="~/logs/spring-api/"
JUMP="ubuntu@172.16.10.31"

# Run rsync with options
rsync -avz -e "ssh -J $JUMP" $SOURCE $LOCAL_DEST
```

## Generating SSH keys to avoid password prompts

To generate SSH keys and copy them to the remote server, follow these steps:

1. Generate a new SSH key pair: (Only for the 1st time)
    ```bash
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```

2. Copy the public key to the remote server:
    ```bash
    ssh-copy-id -i ~/.ssh/id_rsa.pub username@remote_host
    ```

3. Verify that you can log in without a password:
    ```bash
    ssh username@remote_host
    ```

Replace `username` and `remote_host` with your actual username and remote host address.