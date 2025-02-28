- It is a tool that stands in between the browser and the server
- It is used to modify requests sent to server
- We use intercept to stop the requests 
- Host is the targeted website
- User agent is the browser and the device's info
- ---
### Video 2:
**Burp Suite tabs:**
- Target shows targeted websites (the others are grayed out)
- To focus on one target, add it to the Scope tab and filter it
- Showing targets depends on your case
- Show only requested items if you want
- Para metered requests to specify sites with parameters
- In proxy tab, we modify the payload and then forward it to the server
- We can also drop the host if we don't want it
- In "Action" button or right click, we can add it to: Scanner, Repeater or etc
- Headers just shows the headers alone
- HTTP history is your visit history in burp
- Options allows you to listen to other devices in the local network
- You can also highlight hidden fields
### Video 3:
- Spider is not available in newer versions
- Intruder tab, is used to brute force an attack on a certain parameter
- Repeater tab, to test modified requests without loading the website again
- Sequencer tab, to check the cookie and analyse it (Ex: PHP ID Session)
- Decoder tab, Encodes the script into a URL in order to apply it as a payload and vice versa
### Video 4:
- Comparer tab, compares between two websites or requests and their data. You can compare words or even bytes in hex
- Extensions tab, to use plugins that are made by users
- Scanner is for Pro version only :(
### Video 5:
- If we want to actually intercept and modify the request, we go to options and tick "Intercept client requests" and "Intercept server response"
- Render is to see the behavior of the web app
- in "Intercept client requests" make sure to choose to intercept in targets within scope only
- in Scope settings, we can edit it to add subdomains (in big web apps)
- \w.example.com allow us to add subdomains
Next is [[Web Technologies]].

---
## Ebrahim's Course (quick notes):
- check Unhide hidden form fields and highlight it -> to show hidden forms
- check Remove input field limits and Enable disabled form fields
- check Remove JavaScript validations and check more options as well
- Match and Replace option -> modifying headers
- Intruder -> used to brute force attacks
- Repeater -> to repeat a request more than once and editing it
- Sequencer -> to check for and analyse Session Randomness (look for `Set-Cookie:`)
- Comparer -> to compare two web pages (could be the same web page but with modified info)
---
Now it's time to hunt!