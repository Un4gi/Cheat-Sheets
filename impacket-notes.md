# Impacket Notes

## Remote Code Execution

_atexec.py_ - Executes the command on the target machine using the Task Scheduler service. Example:
    
    ./atexec.py DOMAIN/Username:Password1!@1.2.3.4 systeminfo

_psexec.py_ - Writes RemComSvc to a share as a random executable name, creates a service tied to the executable, and runs the service. RemComSvc is a remoteshell/telnet replacement that lets you execute processes on remote windows systems, copy files on remote systems, process their output and stream it back. 
RemCom was used by `FANCY BEAR/APT 28` in the attack on the Democratic National Committee in 2016, according to open source reporting.
    
*Note: This starts a named pipe called `\\.\pipe\remcom_comunication`, but this needs tested to see if the named pipe was changed in the impacket version.*
    
    ./psexec.py DOMAIN/Username:Password1!@1.2.3.4 net user

_smbexec.py_ - A similar approach to PSEXEC w/o using RemComSvc. Initiates a local smbserver to issue commands.

    ./smbexec.py DOMAIN/Username:Password1!@1.2.3.4

_wmiexec.py_ - Provides a semi-interactive shell using Windows Management Instrumentation. It does not require installing any service/agent on the target server and runs with elevated privileges. The working of this script is Highly stealthy.
    
    ./wmiexec.py DOMAIN/Username:Password1!@1.2.3.4 netstat

## SMB/RPC

_smbclient.py_ - Allows you list the files, rename, upload and download files and create and delete directories, all using either username and password or username and hashes combination. You can use the `help` command once connected to list the available commands.

    ./smbclient.py DOMAIN/Username:Password1!@1.2.3.4

_services.py_ - This script can be used to manipulate Windows services through the [MS-SCMR] MSRPC Interface. It supports start, stop, delete, status, config, list, create and change.

    ./services.py DOMAIN/Username:Password1!@1.2.3.4 list

_netview.py_ - This script extracts a list of the sessions opened at the remote hosts and keeps track of them by looping over the hosts found and keeping track of who logged in/out from remote servers.

    ./netview.py DOMAIN/Username -target 192.168.1.103

_smbclient.py_ - Allows you list the files, rename, upload and download files and create and delete directories, all using either username and password or username and hashes combination. You can use the `help` command once connected to list the available commands.

    ./smbclient.py DOMAIN/Username:Password1!@1.2.3.4

_reg.py_ - Remote registry manipulation tool through the [MS-RRP] MSRPC Interface. The idea is to provide similar functionality as the REG.EXE Windows utility.

    ./reg.py DOMAIN/Username:Password1!@1.2.3.4 query -keyName HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows -s
