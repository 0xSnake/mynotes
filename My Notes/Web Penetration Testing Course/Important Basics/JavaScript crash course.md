- JavaScript is used to build interactive web pages (in general)
- runs on browsers
- Node.js is a C++ programs that includes Google’s JavaScript engine
- We write JS code in the console from “Inspect Element” button
- We add the script element in the body section (preferably at the end) : <script> </script>
- Or: we can just separate HTML from JS code in a different file that ends with *`.js`: `<script src="main.js"> </script>`

- **JavaScript syntax:**
    
    ```JavaScript
    console.log('Hello world'); 
    // for printing and will appear in console
    let name = 'Abdo'; 
    var name = 'Abdo';
    // to declare a variable
    const name = 'Abdo'; 
    // to declare a constant (can't be reassigned)
    alert("Hello World"); 
    // to show a message on the webpage
    
    // Objects:
    let person = {
    	name: "Ali", // each one of those inside is called a "property""
    	age: 4
    };
    // to store multiple values into one variable
    
    person.name = "Hema"; 
    // to update the property
    
    // Arrays:
    let blabla = ['balls' , 'nuts'];
    // arrays start with 0 Index
    blabla[0] = 'ligma'; // will change balls to ligma
    
    console.log(blabla.length); // shows number of values
    
    // Functions:
    function Hello(name) { // 'name' is a parameter used to input in the function
    		// this is the body of the function, we add code here
    		console.log('Hello ' + name);
    }
    Hello("Hema");  // 'Hema' is called an argument, the actual input that we want
    
    // another way to do functions:
    function squirt(number) {
    	return number + 7.5 ;
    	// basically return gives us the value of the function
    		
    }
    console.log(squirt(10)); 
    // will print 17.5
    
    
    // If and else If:
    if ( name == "Ali"){
        alert("Yes"); } 
    else if(name == 'Mohamed'){
         alert("Maybe")}
    else {
     alert("No") };
    ```
    
- **How to add JS to check for username and password:**
    
    - First, in the HTML form we add id to both username and password:
    
    ```HTML
    <form>
    <input type="name" placeholder="Username" id="username"> <br>
    <input type="password" placeholder="Password" id="password"> <br>
    <input onclick="check()" type="submit"><br>
    </form>
    ```
    
    - let’s say we well call the function “check()”
    - also don’t forget to include the check function in the submit button by using the attribute: `onclick=”check()”`
    - Now go to your JS code and write the function:
    
    ```JavaScript
    function check(){
        var username = document.getElementById("username").value;
        // We add the same id from the HTML form
        var password = document.getElementById("password").value;
        // Same here
        if ( username == "Ali" && password == "Ahmed"){
        alert("Login Successfull"); } 
        else{
            alert("Login Failed");
        }
    }
    ```