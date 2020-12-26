# Useful Commands

## SSH
- Proxy traffic through SSH tunnel: `ssh -D localhost:8000 user@ip`
- Proxy traffic through multiple tunnels:
```bash
ssh -L 9999:localhost:9999 user@<ip>
ssh -D localhost:9999 <ip> -p 25
```
- Proxy traffic through Metasploit: `ssh -L 8000:<remoteIP>:1337 root@<remoteIP>`, then start socks via Metasploit on port `1337`.

## 
- Parse `access.log` file for unique IP addresses: `cat access.log | grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" | sort -u `

## Starting a SOCKS server via Metasploit
- Add a route to go through a current session
- `use auxiliary/server/socks4a`
- `set srvport <port>`
- `run -j`

## Scanning through Proxychains
- `proxychains nmap -sT -Pn <ip>`

## Linux Enumeration
- `find / -perm -4000 2>/dev/null` - Find files with SUID bit set

## Buffer Overflow

### gdb-peda
- `checksec` - checks memory protections enabled on binary

### Easy check for ASLR
- `ldd <binary> | grep libc` - Run multiple times to see if memory address changes
