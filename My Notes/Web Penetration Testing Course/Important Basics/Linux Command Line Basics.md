---
share_link: https://share.note.sx/w7ounj6l#ssckE+M3rNs4yGfzcNGjBrLuF7UWYdFlYN5rdeJYxb8
share_updated: 2025-02-11T01:42:18+02:00
---
### Video 1:
**These commands are for Kali Linux or any debian-based distros:**
- `cd /Example` -> to open a directory (folder) , `cd ..` -> to go backwards
- `apt update && apt upgrade` -> updating your system (update for repos, upgrade for packages)
- `man` -> to view manual pages for any command (ex: man "command")
- `ls` -> lists directory (folder) contents
- `clear` -> cleans the command screen
- `apt install pkg-name` -> to install packages
- `apt-cache search pkg-name` -> to search for packages
- `apt-get autoremove` -> to remove packages with their dependencies
### Video 2:
- `sudo` -> to run program as root (admin)
- `su` -> to switch user to other users
- `locate example.txt` -> finds files
- `find /Destination -name "example.txt"` -> finds files too
- `curl http://example.com/file.png` -> to transfer URL data
- `wget` -> just like `curl` but downloads the website on the PC
- `touch test.txt` -> to create a new file
- `nano` -> opens NANO text editor
- `echo` -> to print something (ex: `echo "Hi" > test.txt`)
- `echo "Hi" >> test.txt` -> we used `>>` to append to the file in the end
- `cat` -> to display contents of a file
### Video 3:
- `ifconfig` -> to show the device's IP address
- `grep` -> searches inside the files or in the output of another command
- `|` -> it's called the "pipe" (standard output) which applies the second command on the first one (ex: `ifconfig | grep -i "inet"` to search for the word `"inet"` in the output of `ifconfig`)
- `cut` -> to NOT search (opposite of `grep`)
- `pwd` -> shows the current directory
- `id` -> shows the current user
- `;` or `&&` -> to do more than one command at the same time
- `&` -> to run a command in the background
- `head` -> to read a number of lines from a big file, starting from the top (ex: `head -n 20`  to show the first 20 lines)
- `tail` -> Just like `head` but starts from the bottom
- `/var/log` -> the location of all logs
- `/var/log/apache2/access.log` -> where access logs of the web server are
- `/var/log/apache2/error.log` -> for errors
### Video 4:
- `grep -i` -> to ignore case-insensitivity, `grep -o` -> to only output something
- `[a-z0-9]*.test.com` -> this is a regular expression to get all subdomains
- `sort` -> to sort results or output (ex: `sort -u` to get unique lines and no duplicates)
- `ps` -> to show running processes
- `ps aux` -> to show ALL processes including scripts
- `/sbin/init` -> is the first process that starts everything in Linux
- `kill (process id)` -> to kill a process , `kill -9` -> to force kill it
- `df -h` -> to show all folders and their sizes
- `top` -> shows ram and memory usage
- `htop` -> `top` but with colors
### Video 5:
**File permissions:**
- `-` -> means it's a file , `d` -> it's a directory
- `r` -> read , `w` -> write , `x` -> execute
- it is divided into 3 sections (left to right): first is the user (or the root) , second is the group of the user, third is normal or other users in the server
- `/etc/shadow` -> this file has the passwords for all users in the server
- `chown` -> to change ownership of users (ex: `chown -c root:user /etc/shadow` , this makes the user read the file)
Aaaaaaaaand that's it.
Next is [[Burp Suite Crash Course]].