# Useful Commands

## SSH
- Proxy traffic through SSH tunnel: `ssh -D localhost:8000 user@ip`
- Proxy traffic through multiple tunnels:
```bash
ssh -L 9999:localhost:9999 user@<ip>
ssh -D localhost:9999 <ip> -p 25
```

## 
- Parse `access.log` file for unique IP addresses: `cat access.log | grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" | sort -u `

## Scanning through Proxychains
- nmap -sT -Pn <ip>
