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
It runs before the request happens. For example, let's generate a random number, between 1 and 100, to put in a variable that we are going to send in the body of a Post Request. We can write inside the pre-request script:
<br>
const customerId = Math.floor((Math.random()x 100)+1);
<br>
console.log(customerId);
<br>
We can also use random variables in Postman:
<br>
"quantity": {{$randomInt}}
<br>
This will generate a random integer, directly in json body.
<h2>Writing Tests</h2>
<h3>Check Status 200</h3>
We can go to "Tests" tab and on the right menu click "Status Code: Code is 200".
<h3>Check Customer Id Status</h3>
We click on the right menu: "Response Body: JSON value check". We write the expect value which is on the json object response body (jsonData.customerId) and compare it to the global variable ("get global variable") that we had on pre-request.
<br>
pm.test("Your test name", function () {
<br>
    var jsonData = pm.response.json();
    <br>
    pm.expect(jsonData.json.customerId).to.eql(pm.globals.get("customerId"));
    <br>
});
<br>
We can also check a value from an array like this:
<br>
pm.expect(jsonData.json.products[0].productId).to.eql(pm.globals.get("3000"));
<br>
<h3>Automation</h3>
We can use the "Collection Runner" to see if our tests can be automated.
If we want to go in the direction of running our API tests in a continuous integration service, like Jenkyns, we need to use a tool like Newman, which can be integrated there. 
