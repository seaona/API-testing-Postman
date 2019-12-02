<h1> API-testing-Postman </h1>
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
