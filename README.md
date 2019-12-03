<h1>API-testing-Postman</h1>
httpbin.org
<br>
Example of a request:
<br>
httpbin.org/get
<br>
<h2>Query Parameters</h2>
After the question mark, you will have query parameters:
<br>
httpbin.org/get?name=John
<br>
If we have several query parameters we add <str>&</str> :
<br>
httpbin.org/get?name=John&age=15
<br>
<h2>Path Variables</h2>
Path variables are different form query parameters. I.e. :
<br>
httpbin.org/status/200
<br>
We can change this by a path variable, by adding ":" followed by the path:
<br>
httpbin.org/:status
<br>
We add the value of status path at Postman "Path Variables"
<h2> Working with Variables </h2>
Whatever we write in the test tab, will be exectued after the request. This means that we hava access to the response body.
In Postman we use:
<br>
pm.response.json();
<br>
const response = pm.response.json();
<br>
console.log(response.uuid);
<br>
In Postman snippets, we can set global variables, on the right menu:
<br>
pm.globals.set("variable_key", variable_value);
<br>
And then set the variable_value the "response.uuid".
<br>
In Postman, the way we access global variables is by using double curly brakets {{}}. We can write on the request body:
<br>
{	"orderID": "{{orderId}}"}
<h2>Pre-request Script</h2>
It runs before the request happens. For example, let's generate a random number to put in a variable that we are going to send in the body of a Post Request. We can write inside the pre-request script:
<br>
const customerId = Math.floor((Math.random()x 100)+1);
<br>
console.log(customerId);
<br>
