# Useful Commands

## SSH
- Proxy traffic through SSH tunnel: `ssh -D localhost:8000 user@ip`

## 
- Parse `access.log` file for unique IP addresses: `cat access.log | grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" | sort -u `
