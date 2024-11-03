# linux-cheat-sheet

## Index

- [Copying a file or a list of files via jumpstart](#copying-a-file-or-a-list-of-files-via-jumpstart)

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