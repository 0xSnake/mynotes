## Cross Site Scripting
- Reflected XSS: Simply the developer trusts the user's input and prints it in the page which allows an attacker to run payloads on the page (not stored in the database)
- Stored XSS: The page allows the user to write a comment which could be a payload and can be ran in the web page (stored in the database) 
- DOM based XSS, will be explained later but for now: DOM is like an API for the web page or maybe an index. and it allows you to access all code in the web page (`document.******`)
### How to Reflected and Stored and DOM:
- Google's XSS game: https://xss-game.appspot.com/
- Always try XSS on search bars and look at the source code for the page
- Example of Payload: `<script>alert(1)</script>` `<img src=x onerror=alert(1)>` , `"><svg onload=alert(1)>`
- Don't test the script immediately, the WAF might be running. instead enter: `xx">xX` and if the website accepts it (it got printed), it means you can try the payload. make sure it's between a normal tag like `<b><\b>` . i
- https://html5sec.org/ -> contains a lot of payloads and what browsers work with them
- if the developer blocks `alert()` you can use `confirm()` or `prompt` 
- you can access DOM with the console by typing `alert(document.****);` ex: `alert(document.getElementsByName("fname").value);`
- If the script fails due to being inside `""` then make sure to close it inside the script itself like: `" onerror='alert(1)'`
- Try to make sure that the syntax of HTML is working correctly by viewing the source code and trying again and again. also if the web page is deleting something in the payload try to encode it as URL
---
### How to Mitigate XSS
- You can modify response header, ex: there's a header called XSS Protection. if set to 1 then it won't work
- You can add it to the web page or in the Apache web server config, ex: `header("X-XSS-Protection: 1; mode=block");` add it to the page. although this header work on all browsers EXCEPT Firefox
**Filter user input:**
- you can use a function called `htmlspecialchars` in PHP to filter the input from the attacker (basically it encodes user input values), ex: 
```php
	 $code = htmlspecialchars($_GET['name']);
```
**Client Side vs Server Side:**
- Client Side -> what happens on your browser (JavaScript)
- Server Side -> what happens on the server itself (PHP)
- that's why we ask the user to do the validation Server Side not Client Side
---
### Advanced XSS Exploitation:
- You can use XSS to change inner HTML code by typing a script that includes: `document.body.innerHTML="Insert JS Command here"` (ex: 
```javascript
<script>document.body.innerHTML=confirm(1)</script>
```
- Injecting Extra Headers: If you try XSS on the user cookies (when the user visits the website with the cookies, the XSS code reflects in the web page) some website consider this to be Self-XSS (has no impact) which is not the case but in fact if the web page is infected with Reflected XSS and cookie-based XSS -> can be escalated into Stored XSS which has much higher impact and steals the cookie from the user
-  be careful that sometimes there are flags like `httponly` or `secure` that prevents JavaScript code from running
- --
This is XSS attacks but really quickly, we will go on with further details on another note