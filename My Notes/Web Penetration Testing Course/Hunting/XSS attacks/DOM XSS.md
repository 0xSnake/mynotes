### What is DOM ?
- **DOM (Document Object Model) -> basically an interface that represents the structure of the document (HTML or XML. images, tags etc) and allows programs (the browser) to manipulate it.**
- Needs JavaScript Reading and happens on browser level.
**DOM XSS vs Reflected XSS**
- In Reflected XSS: you send your payload to the server, the server handles it and returns it in the response
- In DOM XSS: Happens on Browser level (Client Side) NOT on the server itself
- Reflected XSS is easier to find. unlike DOM which is more harder
- To mitigate Reflected XSS, you put a function in server side that handles and manipulates the payload by encoding it or striping tags.
- WAF filters Reflected attacks because the data goes from client to server which enables the WAF to filter your payload, But in DOM the WAF has no idea because everything happens in the browser not in the server
- DOM Reflected XSS -> it happens due to sending a payload to the server which the browser handles it using DOM
**How to find it?**
- We start by reading the client side JS code (really difficult due to frameworks but there are workarounds) to look for sources and sinks (sources -> input, sinks -> output) 
- Then we check for event handlers (`ex: onclick, onmouseover, onload`) which executes the functions
- then we Inject the strings (simple strings) and check if it reaches the sinks and the context it reached, after a few other steps we finally inject the payload
**Sources:**
- Input fields, URL path, parameters, hash , local storages
- Cookies or Headers (sometimes needs other bugs to happen, not recommended to report unless it's sensitive information)
**Sinks:**
- `document.write() ,innerHTML, appendChild, eval(), setTimeout(), setInterval()` and many others
---
**An Example on DOM Location Object and its properties:**
(https://www.example.com/index.html?x=test#register)
- `location.href`="https://www.example.com/index.html?x=test#register"
- `location.host`=www.example.com
- `location.path`=index.html
- `location.search`="?x=test"
- `location.hash`=#register
- `location.origin`="https://www.example.com"
---
- First we view the source to try to understand the JS code to find the sinks and understand how it works.
- we try to add a string using one of the sources to test for an infected sink (this is location.hash ), (ex: `index.html#abdo`) if the string prints out, try the JS payload
- When we test the payload and view the payload, we actually don't see what we wrote since it gets the page source from the server side. but if we inspect it from the browser, we find our payload -> ALWAYS look at the element
- You can actually get DOM based Open Redirect bug from the web page -> ( `index.html#https://yahoo.com` ) and it redirects it to another website (yahoo for ex)
- it's best to review [[JavaScript crash course]]
- Again in short: Open the source code and check for JS code, can't find it? try to test on user input (the server injects JS under certain conditions) and see if it shows up. Look at the function and try to understand how it works, then try to inject a string, then the payload. hence and repeat until something works. Practice makes perfect.
---
### DOM Invader:
- It's a plugin and only inside Burp Suite's browser, it helps you to read JS code in actual large websites in order to find DOM XSS vulnerabilities.
- It's recommended to choose the interesting sinks with `xhr` sink
- in Misc you have a lot of options to choose from but essentially enable message filtering
- Canary: is a random string that the tool automatically injects in all sources to check for sinks. you also change it to something familiar
- check https://portswigger-labs.net/dom-invader to find a lot of test cases to test the DOM invader
- Open Inspect Element and find the DOM invader tab in order to use it, you can also exploit it as well and report it. you can inject URL parameters and forms which is basically the main use
- Of course it doesn't work all the time, due to WAF or other complications but it helps us in large websites