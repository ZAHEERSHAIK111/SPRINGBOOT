In previous units, we learned about HTTP requests, which are messages sent from a client to a server to request information. The client specifies what action they want to perform (such as getting information or posting new data) using an URL and a method like GET, POST, PUT, or DELETE.

The server then sends back an HTTP response, which includes information about the response and a status code indicating the outcome of the request.

In this unit, we will explore how to use REST APIs to perform various operations on data, such as creating, reading, updating, and deleting using HTTP requests.

1. API
API (Application Programming Interface), is a software intermediary that allows two applications to talk to each other. An API defines the rules and format for data exchange between a client and a server.

REST APIs
REST APIs are a type of web APIs that use the Internet to send and receive information. They use common methods such as GET, POST, PUT, and DELETE to interact with data and services on a remote server.

REST APIs allow us to  create, read, update, and delete data by sending HTTP requests to the server, and receiving HTTP responses with the requested information. The responses from the server are typically returned in a standard format, such as JSON or XML, which makes it easier to use in different programs.

REST Principles
REST(REpresentational State Transfer) is a set of principles that define how Web standards, such as HTTP and URLs, are supposed to be used.

Using Rest Principles improves the application in various aspects like scalability, reliability, etc.

Some of the Rest Principles are:

Providing every resource with a unique ID.

 For example,

https://gorest.co.in/public/v2/users/1/
https://gorest.co.in/public/v2/users/5/
https://gorest.co.in/public/v2/users/10/
https://gorest.co.in/public/v2/users/40/

Here, each user has a unique ID which helps to identify and access them.

Using standard methods.

GET https://gorest.co.in/public/v2/users/
GET https://gorest.co.in/public/v2/users/:userId/
POST https://gorest.co.in/public/v2/users/
PUT https://gorest.co.in/public/v2/users/:userId/
DELETE     https://gorest.co.in/public/v2/users/:userId/

These are the standard methods defined in the HTTP specification with guaranteed behaviour.

Accept and Respond with JSON.

http header
 Here, the client sends a request to the server specifying the data format it wants to receive using the Content-Type:application/json header, and the server responds with a JSON content.

Statelessness in REST APIs

The server does not store any information about the client's state. Each request is treated independently.

For example, when you access a webpage, the server does not keep track of your previous requests and simply sends back the requested data

Go REST API
Go Rest is an online fake REST API service used for quick testing and prototyping of web and android applications. It provides a simple and convenient way to simulate REST APIs and test their functionality without having to set up a real server or write code.

respose handling exception
Getting Started with Go REST.
Open https://gorest.co.in/

Click on the login button in the top right corner.

Now click on the Google button and Sign in with Google.

Users API
In our practice, we will be using users API from Go REST API:

Users API from Go REST API:

respose handling exception
Let's look at the data in the users API.

respose handling exception
User Related APIs
Go Rest provides different APIs for performing different actions on user data, such as creating, reading, updating, and deleting data.

respose handling exception
2. API Testing Tools: POSTMAN
API testing tools are tools used to test the performance and functionality of APIs. They help make sure APIs work properly and give the right results.

There are multiple API testing tools available to test different types of HTTP requests

Postman
Insomnia
SoapUI
Swagger Editor etc.
We will be using Postman because it is a popular API testing tool that allows users to send HTTP requests and view the responses. It supports various types of requests (e.g., GET, POST, PUT, DELETE), and provides features for organizing, testing, and documenting APIs. The Postman tool is used by developers to test RESTful APIs and automate API workflows.

Getting Started with Postman
Open the url: https://www.postman.com/.

Click on Sign Up for Free.

response handling exception
Create an account by clicking on Sign Up with Google.

resoponse handling exception
Accept the license agreement.

response handling exception
Fill out the basic details and click Continue without team.

respnse handling exception
Click on the Skip for Now button.

response handling exception
Click on the Let's go button.

response handling exception
Click on New Http Request and Continue.

response handling exception
We completed setting up the Postman. Now we are going to use it to send HTTP requests.

3. Hands-on with Go REST API
Let's perform some CRUD operations (Create, Read, Update, and Delete) using the Go REST API

3.1 GET
Making the HTTP GET request on the users API
  
Copy the users URL https://gorest.co.in/public/v2/users from the Go REST and paste it into the Postman.
Select the GET method.
Click on the send button to send the request.

response handling exception
HTTP Response for the above GET request

response handling exception
Here, we got a response from an HTTP GET request. The response includes information about users, a status code 200 OK, and the format of the response as JSON.

200 OK 
200 is the HTTP status code and OK is the status text. It indicates that the requested resource is available and has been returned to the client in the response message.

JSON 

JSON is a data representation format used for:
  
Exchanging data between client and server.

Storing data (Client/Server).
JSON is a text-based format that represents data as a collection of key-value pairs and arrays.
response handling exception

JSON supports the following data types.

Data Type	Example
String	"Rahul"
Number	9832.32
Object	{"name": "rahul"}
Array	[5, 10, 15]
Boolean	true
Null	null
The body tab contains the information of the different users.

3.2 Authentication & Authorization
Authentication
Authentication is the process of verifying a user’s identity

For example, think of a library card as an example of authentication. In order to enter the library and check out books, we need to prove our identity by presenting a valid library card.

Authorization
Authorization is the process of verifying whether the user is authenticated and determining what a user is allowed to do once they have been authenticated

For example, after we've proven our identity by the librarian, our permissions are determined based on our membership level. 

We may be allowed to check out only books, while a librarian may have access to additional resources such as restricted books, research databases, etc.

3.3 POST
  Let’s make a POST request using Postman to create a new user.

Click here to open a new tab to make a new HTTP request.

response handling exception
Select the POST method.
We are adding a user to the user data. So we use users API to add a new user.

response handling exception
Select the Body tab.

response handling exception
Select the raw option.

response handling exception
The data should be in JSON format, so choose the JSON option.

response handling exception
Add data in the  JSON format and click on the Send button.

response handling exception
HTTP response for the above POST request.

response handling exception
 Here,
 
401 Unauthorized: 401 Unauthorized is an HTTP status code indicating that the client is not authorized to access the requested resource and needs to provide a valid access token.
Also received a message Authentication failed explaining why the client is not authorized.

To get authorization Go REST provides an access token to include in HTTP requests that verifies user identity and allows us to perform a particular action.

 Now let us see how to get access tokens.

Let's go to the home page of Go REST(https://gorest.co.in/) and log in.

Click on the API Tokens.

response handling exception
Now let us copy the access token.

response handling exception
Now open the POSTMAN and select the Auth tab.

Select the Bearer Token option in the Type section.

response handling exception
Now paste the access token copied from the Go REST-->API TOKEN.

response handling exception
Click on the Send button to make the HTTP POST request.

HTTP response for the above POST request.

response handling exception
Here, 201 Created: 201 is an HTTP status code and Created is a status text indicating the successful creation of a new resource on the server as a result of a client's POST request.
Upon creating the user, the new ID is added to the user details to identify the user uniquely and is included in the response. Let us see the request we sent and the response we got.

HTTP request

response handling exception
We don't need to pass the id in the body because the id is automatically generated by the server to avoid repetitions.

HTTP response 

response handling exception
Here, the response  contains the id as 204476 which is automatically generated.

3.4 GET by ID
Using the GET method, you can get specific user data based on the ID of the user.

We use base url: https://gorest.co.in/public/v2/users 
Path: /id  to get the data of the specific user.

Click on the + to open a new tab to create a new HTTP request.

Let’s consider the user details that we created in the above POST request. There, the ID is 204476. So our URL to get the data  is https://gorest.co.in/public/v2/users/204776.

Similar to the POST users API, the GET users API also requires an access token to perform an operation. So click on the Auth tab and select the option Bearer Token.

Now click on the Send button to create the HTTP GET request.

HTTP response for the above GET request.

response handling exception
 Here, the response contains the user details of id 204476 and the status 200 OK.

3.5 PUT
Using the PUT method we can update the  specific user data based on the ID of the user.

We use base url:"https://gorest.co.in/public/v2/users
Path: /id to update the data of the specific user. So the URL is https://gorest.co.in/public/v2/users/204776.
Click on the + to open a new tab to create a new HTTP request.

Let us update the name of the user we created above from "Rahul" to "Rahul Attuluri".

Select the method  PUT.

Select Body, raw, and JSON options.

response handling exception
Let's update the name in the body section.

response handling exception
Similar to the POST users API, the PUT users API also requires an access token to perform an update operation. Select the Bearer Token option in the Auth tab.

Click on the Send button to make an HTTP PUT request.

HTTP response for the above PUT request. 

response handling exception
 Here, the response contains 

Status code 200 OK indicates the user details updated successfully.

The  details of the id 204476. We can see that the name got updated.

3.6 DELETE
We use base url: https://gorest.co.in/public/v2/users 
Path: /id to delete the data of the specific user. So the url is https://gorest.co.in/public/v2/users/204776.

Click on the + to open a new tab to create a new HTTP request.

Let us delete the user we created above whose id is 204776.

We use the API https://gorest.co.in/public/v2/users/204776.

Select the method  DELETE.

Similar to the POST users API, the DELETE users API also requires an access token to perform an operation. So click on the Auth tab and select the option Bearer Token.

Click on the Send button to make an HTTP DELETE request.

HTTP response for the above DELETE request.

response handling exception
 Here, 204 No Content: 204 No Content is an HTTP status code that indicates that the server has successfully processed the request, but there is no content/message to return in the response. This status code is often used in response to a successful DELETErequest.

After deleting a user, if we try to get the deleted user using GET request, we will receive a 404 Not Found response.

 Let's try to get the deleted user.

response handling exception
Here,

404 Not Found: 404 Not Found is a HTTP status code that indicates that the server could not find the requested resource. This status code is returned when a client requests a resource that does not exist on the server, or when the server is unable to locate the requested resource.

Also received a message indicating the resource was not found on the server.

Summary
REST APIs use GET, POST, PUT, and DELETE methods to create, read, update, and delete data on a remote server.

Go Rest API provides resources to perform the CRUD operations.

Postman is an API testing tool that helps us test APIs more easily.

JSON is a data representation format used for exchanging data between client and server.

Authentication and authorization are crucial security mechanisms in REST APIs that determine the identity of a user and control access to resources by enforcing restrictions and permissions.
