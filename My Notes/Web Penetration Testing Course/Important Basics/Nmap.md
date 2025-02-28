### Video 1:
***Nmap basics***
- Before pentesting, we need to know the ports of the services on the target web app
- The port is: open, closed or filtered (means there's a firewall)
- Nmap shows you the open ports that aren't usually open, sometimes ports are open for developers
- `nmap "ip"` ex: `nmap yahoo.com` or `nmap 127.0.0.1`
- it only scans the most famous 1000 ports (HTTP, HTTPS etc)
**Most Important uses:**
- `nmap -sT -sU yahoo.com` -> `-sT` to scan TCP, `-sU` to scan UDP
- space allows you to see the completion percentage
- `nmap --top-ports 2000` -> to specify a certain number of ports
- `nmap -p 80,443,22` -> to specify certain ports
- `nmap 1-65535` -> scanning from 1 to 65535
- `nmap -A` -> figures out the service of the port (tcprapped means it couldn't figure it out)
---
### Video 2:
***Advanced Nmap***
- `nmap 192.168.0.0/16` -> `16` or `24` allows us to scan a range of IP's
- IP subnet calculator -> helps us to determine the IP range (ex: `*.*.*.0/24` -> 24 gives us 255 IP's)
- `nmap -iL target.txt` to scan the list of IP's in the text file
- `nmap -sn` -> show how many and what IP's have responded
- If a port is open on a certain subdomain, it means there has to be other open ports as well
- `nmap "website" -p "port" -A` -> to figure out the service of this port
- https://exploit-db.com to find certain exploits for the open ports
**Quick on Metasploit Framework:**
- `msfconsole` to start Metasploit
- `search "service-name"` -> to search for the vulnerability name, then copy the name of the vulnerability
- `use "vun-name"` to use it
- `show options` to show how to use this vulnerability and it's requirements
- ex: `set RHOST "hostname"` to set the host for it
- `exploit` to start exploiting
**Nmap Moreover:**
- `/usr/share/nmap/scripts` is where Nmap scripts are located
- `ls | grep -i "name"` to find the wanted script (ex: `ls | grep -i brute` to find brute force scripts)
- `nmap --script="script-name"` -> to use a certain script
- `nmap --oA` or `--oG` or `--oX` to save the output of Nmap
- --
Next is [[Burp Suite Crash Course]] (From Ebrahim's notes).