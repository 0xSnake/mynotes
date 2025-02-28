### Video 1:
- CA (Certificate Authority) are a bunch of certificates made by big companies which allows the browser to check for a secure HTTPS connection
- CRL (Certificate Revocation List) is a list that contains invalid certificates, it stops the browser from connecting to the website until the certificate is renewed
- OCSP server is a new and a faster version of CRL, used instead of storing all certificates offline (CRL) which is a slow process
### Video 2:
- HTTP (Hypertext transfer protocol) is a request-response protocol (browser sends the server a request and gets a response)
- HTTP is a stateless protocol (means it sends the request and forgets your info, that's why cookies were made)
- HTTP can be sniffed (Man on the middle attack) which makes it insecure
- on port 443 -> HTTPS , on port 80 -> HTTP
- port is a "door" which allows us to do a certain task (transferring files, data, web pages etc)
- HTTP Headers are the "language" that allows the server to understand the request
For more info check [[PHP and HTTP]] 's HTTP section
**Request Headers -> Sent by the server:**
- Referrer indicates from where the user came to the website
- Host is the link of the web app
- GET means to get the content of the web app (ex: `GET /` gets all the contents) and it shows in the URL
- POST same as GET but the request is in the body of the web page without showing it in the URL
- User Agent -> a HTTP header that shows the browser info (or the device in general)
- Cookie -> is a file which restores the data of the user locally (on the device itself)
**Response Headers -> Sent by the web application:**
- Date -> shows the time and date obviously
- Set cookie (explained later in XSS attack)
- Status code -> shows the status of the website (200 -> OK , 301 -> Redirect and etc)
- Expires -> shows when the cache (cache is the website stored locally) will expire
**HTTP methods:**
- GET -> all parameters are shown in the URL
- POST -> unlike GET, they are in the body of the page
- HEAD -> like GET request but shows no content in the request (response header only)
- TRACE -> used in cross-site scripting, shows request content in the response
- OPTIONS -> (not allowed method) only select
- in the URL: before "=" is the parameter and after it is the value
 **HTTPS:**
- is a secure HTTP connection that uses the SSL Encryption (both the Symmetric and Asymmetric Encryption)
more is explained in the Networking notes
### Video 3:
**WAF (Web Application Firewall):**
- Firewall stops what you want from entering the server
- stops web vulnerabilities in general (XSS, SQLi, DOS etc)
- Types of WAF: F5, AWS WAF, MS Azure WAF etc
- There are paid and free WAFs (F5 -> The strongest one and paid)
- it's a server that filters or checks the request before allowing it into the web app
- also to prevent any programming errors from developers
***1-WAF Learning Mode***
- WAF here learns how the web app works
- the longer the learning mode lasts, the better its understanding for the web app
***2-WAF Passive Mode***
- records or saves any unnatural activity but won't do anything (yet)
- it also saves everything in logs in one server (SIEM solution or QRadar)
- Security Engineers use these logs to determine an action 
***3-WAF Active Mode***
- If it sees any unnatural or malicious activity, it blocks it or stops it (blocks the IP or the request)
---
Next is [[Networking and other stuff]].