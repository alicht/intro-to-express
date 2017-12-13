# Intro to Express
A huge portion of the Internet’s data travels over HTTP/HTTPS through request-response cycles between clients and servers. Every time that you use a website, your browser sends requests to one or many servers requesting resources. Every image, meme, post, and video is requested by a client and sent in a response from a server.
Express is a powerful but flexible Javascript framework for creating web servers and APIs. It can be used for everything from simple static file servers to JSON APIs to full production servers.


we’ll learn the necessary skills to create a CRUD app

Starting a server

How to run a Node.js server
This blogpost expertly details how to
https://blog.risingstack.com/your-first-node-js-http-server/


Why is express the framework of choice for many popular web services?

## Installing
lets install express using NPM (node package manager)

```npm install express``` 

![Alt Text](https://media.giphy.com/media/glJV9Sa6bq9SE/giphy.gif)

-  hello newman app 
first thing we do is require the express library

when we run that function we get an application instance, which we store in the app variable



```javascript
let express = require('express');
let app = express();
```
on the app object we can call functions that create routes:

-  the GET function creates a route that accepts HTTP GET requests

![im1](https://user-images.githubusercontent.com/6153182/33916991-b7bebb0e-df79-11e7-8870-c21ca13f8114.png)

and a callback function that will run each time our application receives a get request on the root path
## Request and response
The callback takes a request and response object and we'll use the response object to send us back the text "hello" 

Lastly, we bind our application to TCP port 3000

![img2](https://user-images.githubusercontent.com/6153182/33916961-92d47630-df79-11e7-976d-e8396f785a8a.png)

-  express also has other functions:
app.post
app.put
app.patch
app.delete


```
app.listen(3000

);
```

once our server's up its going to print listening on port 3000

![img3](https://user-images.githubusercontent.com/6153182/33917004-c6a7cf02-df79-11e7-8cd6-10e99b3bb043.png)

### To run our app we use node app.js

whenever we change code we have to restart our server

express extends node.js

![im4](https://user-images.githubusercontent.com/6153182/33916974-a00533c6-df79-11e7-897e-aa3b5edbc784.png)

## review concept of extends and how it is applicable
Inheritance gives us the ability to call express functions from express apps

![im5](https://user-images.githubusercontent.com/6153182/33916948-8513a5d4-df79-11e7-8619-2178715a39c8.png)

#### we'll want to serialize things in JSON

to do this we use the send function

![im6](https://user-images.githubusercontent.com/6153182/33916985-ad6475e0-df79-11e7-877e-b13d29282703.png)

# NPM
The node package manager (NPM) provides access to hundreds of thousands of reusable packages. It also has best-in-class dependency resolution and can also be used to automate most of the build toolchain.

# Why use Express?
A: This is an Node server
```javascript
// Load HTTP module
var http = require("http");

// Create HTTP server and listen on port 8000 for requests
http.createServer(function(request, response) {

   // Set the response HTTP header with HTTP status and Content type
   response.writeHead(200, {'Content-Type': 'text/plain'});
   
   // Send the response body "Hello World"
   response.end('Hello World\n');
}).listen(8000);

// Print URL for accessing server
console.log('Server running at http://127.0.0.1:8000/');
```

Other common web-development tasks are not directly supported by Node itself. If you want to add specific handling for different HTTP verbs (e.g. GET, POST, DELETE, etc.), separately handle requests at different URL paths ("routes"), serve static files, or use templates to dynamically create the response, then you will need to write the code yourself, or you can avoid reinventing the wheel and use a web framework!

# Enter Express

-  Write handlers for requests with different HTTP verbs at different URL paths (routes).
-  Integrate with "view" rendering engines in order to generate responses by inserting data into templates.
-  Set common web application settings like the port to use for connecting, and the location of templates that are used for rendering the response.
-  Add additional request processing "middleware" at any point within the request handling pipeline.

While Express itself is fairly minimalist, developers have created compatible middleware packages to address almost any web development problem. There are libraries to work with cookies, sessions, user logins, URL parameters, POST data, security headers, and many more. 


# What does Express code look like?

In a traditional data-driven website, a web application waits for HTTP requests from the web browser (or other client). When a request is received the application works out what action is needed based on the URL pattern and possibly associated information contained in POST data or GET data. Depending on what is required it may then read or write information from a database or perform other tasks required to satisify the request. The application will then return a response to the web browser, often dynamically creating an HTML page for the browser to display by inserting the retrieved data into placeholders in an HTML template.

Express...
-  provides methods to specify what function is called for a particular HTTP verb (GET, POST, SET, etc.) 
-  and URL pattern ("Route")
-  methods to specify what template ("view") engine is used
-  where template files are located
-  and what template to use to render a response. 

You can use Express middleware to add support for cookies, sessions, and users, getting POST/GET parameters, etc. You can use any database mechanism supported by Node (Express does not define any database-related behaviour).


# Hello Newman


Let's run through Express code and what it would look like in the browser:

```javascript
let express = require('express');
let app = express();

app.get('/', function(req, res) {
  res.send('Hello, Newman.');
});

app.listen(3000, function() {
  console.log('Example app listening on port 3000!');
});
```

-  We first need to go to our directory and run it in our terminal using the `node app.js` command.
-  Then we have to go to our browser and listen on a localhost and we'll see our code

![Alt Text](https://media.giphy.com/media/eSMZFmPb6pbk4/giphy.gif)

### What happened?

-  1) The first two lines require() (import) the express module and create an Express application. 

This object, which is traditionally named app, has methods for routing HTTP requests, configuring middleware, rendering HTML views, registering a template engine, and modifying

-  2) The middle part of the code (the three lines starting with app.get) shows a route definition. The app.get() method specifies a callback function that will be invoked whenever there is an HTTP GET request with a path ('/') relative to the site root. The callback function takes a request and a response object as arguments, and simply calls send() on the response to return the string "Hello World!"

-  3) The final block starts up the server on port '3000' and prints a log comment to the console. With the server running, you could go to localhost:3000 in your browser to see the example response returned.

# Modules
Express is itself a module!

-  A module is a JavaScript library/file that you can import into other code using Node's require() function. Express itself is a module, as are the middleware and database libraries that we use in our Express applications.

The code below shows how we import a module by name, using the Express framework as an example. First we invoke the require() function, specifying the name of the module as a string ('express'), and calling the returned object to create an Express application. We can then access the properties and functions of the application object.

```javascript
let express = require('express');
let app = express();
You can also create your own modules that can be imported in the same way.
```

# Demonstrating Asynchronous API
let's type this code into our browser
```javascript
console.log('First');
console.log('Second');
```
but what if we were to run this asynchronously?
```javascript
setTimeout(function() {
   console.log('First');
   }, 3000);
console.log('Second');
```

Using non-blocking asynchronous APIs is even more important on Node than in the browser, because Node is a single threaded event-driven execution environment. "single threaded" means that all requests to the server are run on the same thread (rather than being spawned off into separate processes). This model is extremely efficient in terms of speed and server resources, but it does mean that if any of your functions call synchronous methods that take a long time to complete, they will block not just the current request, but every other request being handled by your web application.






