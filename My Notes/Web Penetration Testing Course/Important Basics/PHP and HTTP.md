## PHP crash course

### PHP Syntax: (too lazy to use documentation)

```PHP
Code is written in <?php   ?> and do NOT forget the semi-colon.
<?php
// We do variables using:
$example = 98 ;
echo //to print
"" // this one uses variables
'' // this one does NOT
. // between two strings to combine them

$list = array("Ali", "Abdo" , "Osama") ; // array example
$list2 = ["Osama" , "Bin", "Ladin"] ; // another way to do array
var_dump($list); // show what is inside the array
print_r($list); // similar to var_dump
$list2[0] // chooses a certain index (replace 0 with whatever you want)

// multi-dimentional and associative aren't that important but here they are anyway:
$people = ['Punished' => 34, 'Venom' => 23 , 'Snake' => 86];
echo $people['Snake']; //this gives us Snake's value: 86
$cars = array(
				array('Toyota' , 20 , 30),
				array('BMW' , 30 , 60)
) // this is the MD array example
echo $cars[1][0]; //this gives us variable 0 from array 1 which is: "BMW"
// and I'm getting bored already :(

// Loops
for($i = 0; $i < 10; $i++){
// your code
} // this is for loop 

// in the other loops, it is neccessary to intialize value of i, ex: $i=0

while($i <= 9){
// your code
$i++
} //this is while loop

// Now for do...while loop (we use it to make the command run at least once):
do{
// your code
$i++
}
while(i<10);

// foreach loop is simply loop for arrays:
$people = ['Punished' => 34, 'Venom' => 23 , 'Snake' => 86];
// in the next line, we assign new variables for the loop
foreach($people as $people2 => $numbers){
// your code
}
// That's all for loops.

// Functions: basically blocks of code to use it later.
function myFunction(/*Here we put parameters*/){
// your code
// you can also use return command here to return values
}
myFunction(); // Now you use it
// TIME TO FINISH THIS BULLSHIT 

// Conditionals:
if($var == 0){
echo "idk";
}elseif($var == 1 OR >= 0){
echo "Nah";
}else{
echo "Yes";
}
// that was a basic example of it
// you can also use logical operators like AND or && or even XOR
// Switch is the same as if but a little different
?>


Forms, just forms from html but here is how php works with a quick example:
<form action="index.php" method="GET">
	Name: <input type="text" name="idk" >
</form>
<?php
echo $_GET[idk];
// We got the name from the form
?>
This command will print the input from the form and they are connected using
the GET method from the (name="idk")
just try it and you will get it

and yes we use the methods to store shit in the database.

the methods or cookies are: GET, POST and REQUEST
they basically do the same thing but difference is:
GET shows the parameters and their content in the URL,
POST does NOT and just stores the value in the database.

notice that action parameter in <form> shows what php page that will use the method.

as for REQUEST: we can use it to use POST or GET at the same time
basically this:
<form action="index.php" method="GET">
		<input type="text" name="firstname" >
</form>
<?php
echo $_REQUEST[firstname];
?>
and it will work, doesn't matter if you use GET or POST in the form.


aaaaaand THAT'S IT!
btw this is just for myself as a quick recap but that's pretty much sums it.
and for future me: FUCK YOU.
```

  

## HTTP or how internet works

- means Hypertext Transfer protocol
- which means it’s the protocol for transferring web pages
- works on request-response protocol
- the **Client** sends a **Request** to the **Server** and the server returns a **Response**
- Requests methods (Headers from client): GET, POST, PUT, PATCH and DELETE
- GET if client needs data, POST if client sends data, PUT and PATCH to update data and DELETE to delete data

- Status codes (responses from server):
    - 100: info response
    - 200: Successful Response (200 is OK, 202 is Accepted)
    - 300: Redirects (301 is Moved permanently)
    - 400: Client error (403 is forbidden, 404 is not found)
    - 500: Server error (501 not implemented , 503 not available)

- HTTPS is the Encrypted version of HTTP which uses SSL (TLS) to secure the connection
- Content-Length show the size of the body of the request
