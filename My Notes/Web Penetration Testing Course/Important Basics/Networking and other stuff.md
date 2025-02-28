### Video 1:
- Hashing: a code that does math on an input and turns it into a fixed-size output (or the same size, 32 characters for example)
- It is NOT irreversible (one way function), unless you crack it using huge word lists or tables that contain passwords
- Examples: `md4, md5, sha1, sha2` etc
- It is used to check integrity for files, text etc
- to check for hash: `sha256sum file.txt` and it will show the hash and then you can compare it with the original hash
- [cmd5.org](https://cmd5.org) is a website that checks for hash
- Salting: is adding a few more things to the original text and then hashing it to make cracking the hash more difficult (ex: `Password123` -> `Password123ow65#`)
- ---
### Video 2 & 3:
- Encoding: we do it for transforming the data so that it can be properly and safely used by other systems
- Examples: `base64`, `rot13`, `URL`, `Hex` and etc
- Decoding: The opposite of Encoding, restoring the text to it's original state
**Encryption:**
- Symmetric Encryption: using the same key to encrypt and decrypt the message or the text
- the encrypted text is called "Cipher text" and the non-encrypted is called "Clear text"
- Examples: `AES, DES, 3DES, TwoFish, BlowFish`
---
### Video 4 & 5:
**Asymmetric Encryption:**
- uses public key for encryption and private key for decryption
- We use `ssh` service (secure shell) to gain access to a remote server
- `ssh-keygen` -> creates a public key and a private key (ex: `ssh-keygen -t rsa`)
- ssh algorithms like: `RSA, DH, DSA, ECDH` etc
- CA (Certificate Authority): are pre-installed certificates that ensures that the website is trusted (trusted certificates)
- the browser sends the server a request with a certain encryption algorithm (uses both symmetric and asymmetric)
- They use asymmetric connection first to exchange the key then they use symmetric connection to communicate again
- then the server sends a response with a status code
- CRL (Certificate Revocation List) -> when a certificate gets stolen, it gets reported to CRL and stops the connection to the site
- on port 443 -> HTTPS , on port 80 -> HTTP
**For more details see: [[Web Technologies]]**
---
### Video 6:
**What happens when I open https://www.google.com in my browser?**
- first we should know the OSI Model (or the layers):
- 1- Physical -> the physical wire or the network cable basically
- 2- Data Link -> reads the MAC address from the data packet (still hardware or switches)
- 3- Network -> reads he IP address (here the router works)
- 4- Transport -> where TCP and UDP protocols are and they're used to transfer the data (explained more later)
- 5- Session -> starts/ends the connections between the two devices (NetBIOS protocol or PPTP)
- 6- Presentation -> the SSL encryption happens here basically (formatting the data so it can be used)
- 7- Application -> where the service we want to use
**Now here's what happens:**
- First we get the IP address for our machine (DHCP protocol manages that and automatically gives you an IP, or sometimes the security engineer gives it to you)
- The browser then sends a HTTPS request to the target web app, it gets the target's IP from the DNS
- DNS (Domain Name Service)-> it's a service that gives the IP a unique name instead of numbers 
- Then the web server responds to the request by sending a SSL certificate and a public key (Asymmetric encryption)
- The browser decrypts the response with a private key and it also validates the SSL certificate (the whole CA process basically) then they communicate later on with a Symmetric encryption
---
### Video 7:
***TCP and UDP protocols:***
- Every packet has: Source IP, Source Port, Destination IP, Destination Port
- My own IP is the Source IP, the source port is some random port from like 65,535 port
- Dest IP is the IP of the target website, Dest Port in this case is 443 (HTTPS connection) and it depends on the service we want to access
- Before we reach Network layer or layer 3, our source IP and port are the MAC address from the Data link layer (the packets in layer 2 is called frames)
**TCP protocol:**
- is a stateful protocol, which means I always send and receive requests from the server constantly
- it works in a three-way handshake -> browser says SYN , server replies SYN-ACK , browser replies ACK-BACK to confirm the connection
- we use it for secure connections like messaging or sensitive stuff like emails
**UDP Protocol:**
- It just sends a lot of SYN requests and doesn't matter if it loses some packets
- Doesn't validate the packets and doesn't do the three-way handshake thing
- used mostly in streaming and videos
---
### Video 8:
***What is DNS and how it works:***
- DNS (Domain Name Service) -> used to turn an IP to a memorable name (domain) like google.com (google's DNS: 8.8.8.8)
- DNS Cache is where the DNS keeps records of the stored IP's
- The command `nslookup google.com` gives us the IP of the website, for more Linux commands: [[Linux Command Line Basics]]
- famous attacks -> Subdomain Takeover, DNS Poisoning, DNS Cache Snooping, DDOS
---
### Video 9 & 10:
**Different Record Types:**
- A record -> the subdomain for IPV4 (ex: www.yahoo.com)
- the tool `dig` gives us subdomain records
- AAAA record-> the same as A record but for IPV6
- MX record -> for the mail server
- CNAME record (alias) ->making another alternative subdomain (Subdomain Takeover)
- PTR record -> the reverse of DNS, you give it the IP it gives you the domain name
***Subdomain Takeover:***
- basically buying or owning the original subdomain of the alias (mostly the original subdomain expires)
- `dig` searches all the records for a subdomain
- ex: `dig @8.8.8.8 A yahoo.com`
- or you can search for any tools on https://github.com
---
Next is [[Nmap]] .