Before going straight into the vulnerabilities, some things that we must know first:
### PHP GET vs POST:
- Review PHP and JavaScript, check [[JavaScript crash course]] and [[PHP and HTTP]]
- A quick example of an XSS attack:
- Starting the `apache2` web server and making a simple `.php` code like:
```php
<?php 
$code =$_GET['name'];
echo 'Hello '.$code;
 ?>
```
- then add the parameter `name=hema` to the URL in the localhost: `http://localhost/code.php?name=hema`
- Now, you can do a cross-site scripting like this: `http://localhost/code.php?name=hema<script>confirm('Ok')</script>` -> we just added a JS script in the URL and it works!
- That's how the bugs happen. The developer trusts the user input with the content of the web page which sometimes the user might be an attacker
- you can also do this in the Burp Suite in case the request is POST but that's for the bugs themselves.
- --
Now let's Begin!