- The first thing we do is that we check for any field for user input, then the source code for the web page, we can specify the wanted area and inspect it too.
- As before, we check for XSS using `x">X` to close any tags. and we check for it again in the source code, then we try an HTML code first to see if the Web App accepts it then we can include a JavaScript event in the HTML tag. then we could inject the payload. NEVER inject a full payload on the web page
- sometimes there are limiters for maximum characters. to bypass it: We can write a really short payload like `<svg onload=prompt(1)>` or `<img src=x onload=confirm(1)>` or `<img src=x onmouseover=alert(1)>` 
- we can do a script to show cookies using DOM like:
```javascript
	<script>alert(document.cookie)</script>
``` 
- If it uses GET method, it's printed in the URL or even the web page itself
- other times it filters JavaScript, we might need to insert an HTML code or encode the JS code, or even try to play with the syntax to get the code out of the tags
- If it stops you from typing `<>` by making it encoded , try and see if you can inject it as an attribute. you don't have to get out of the tags
- Sometimes the developer adds a CSRF token to stop you from doing the attack, will explain later how to bypass it.
---
### Stored XSS:
**This vulnerability focuses on Injecting the JavaScript code in a comment that is saved in the website. so that each time we reload the page, the payload works.**
- Same as Reflected, Check if the app does strip tags and try closing any tags with  `x">x` first. if it works, you may try an HTML code with no JS events. then with a JS event. then Try the full payload.
- as for filters -> if there is a length limit you can try to change the value of the limit in the HTML code (client side) and see if it works.
- you can also use DOM just like before in Reflected for ex: `document.body.innerHTML="U r hacked"` -> you can use it to change the content of the page. Further explanation later in DOM XSS.
- sometimes the developer adds something like `/` to stop you from executing the code, try adding any other string or tag to see what happens and watch it in the source code. 
  To try and Bypass the filter, you can also encode it , of course unlike Reflected, you encode to HTML not URL (obviously we're injecting in the website itself).
- Didn't work? check for the behavior in the source code. the dev might even block you from writing the tags themselves. Look for payloads at https://html5sec.org that might help you or just google it (Check OWASP too). Didn't work? try executing a JS code like this `javascript:alert(1)` , you can try it if you can't get out of the tags by executing a code within the tags themselves
- all this might not even work, and it's okay. try to figure out what happens from the source code. the point that it's all trial and error, test what works and what doesn't work to try and narrow your options.
---
### Reflected DOM XSS: (Eng Dawood)
- happens when the website handles the user input in a way that the JavaScript uses DOM to reflect the data on the page.
- Now try and use the repeater to modify requests and send it again to try and error
- If the Content-Type is for example a `application/json` means that there's no normal XSS reflection because the JavaScript handled the data. even when you try to inspect you will see that your payload is encoded, now we try to deal with it as DOM
- In inspect element, open the sources and find the .js file and see how things work from the code. Try to connect the code and the response. Test the website with a result and without a result. and of course, look for the sink that you will use, ex: `eval()` 
- you can use backslash `\` -> it's called JavaScript escape which allows you to make the next character a normal string, if he does this in the response: `abdo\"` escape his escape by this -> `abdo\"` in the request which will return this response -> `abdo\\"` .
- after that you're allowed to add something like `- or + or *` then try to escape the brackets and inject the payload. you can also comment out other code by adding `//` to cancel whatever comes after. 
- this also works if you want to escape something that is before like `"/alert(1)//` which is exactly like `"-alert(1)-"`
 - If you're in chromium , go to the function in the JS code and add a break point to watch what happens, 
---
### Stored DOM XSS:
- Here the server sends the response to the JavaScript functions which handles on the client side, not on server side.
- just like Reflected DOM, but instead of going for the search bar we go for the comment section. you will notice that the web site might encode your payload, check for the page's JavaScript code to find out how exactly the encoding happens.
- you might notice that from the JS functions, the encoding might not be recursive (repeated). to bypass it -> throw whatever is being encoded as a bait then start your payload. of course that's not always the case but it's one of the ideas. just don't give up when you see that it's encoded, it might be DOM and needs to check the JS code
---
