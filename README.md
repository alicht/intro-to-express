# Intro to Express

# Demonstrating Asynchronous API

## Narwhal coffee shop
![screen shot 2017-12-12 at 11 46 50 pm](https://user-images.githubusercontent.com/6153182/33922157-c8d8f3ce-df96-11e7-9b53-353bb79cd3e2.png)



let's type this code into our browser
```javascript
console.log('First');
console.log('Second');
```
but what if we were to run this asynchronously?
```javascript
setTimeout(function() {
   console.log('fancy coffee order');
   }, 3000);
console.log('black coffee');
```

Using non-blocking asynchronous APIs is even more important on Node than in the browser, because Node is a single threaded event-driven execution environment. "single threaded" means that all requests to the server are run on the same thread (rather than being spawned off into separate processes). This model is extremely efficient in terms of speed and server resources.

# MVC

![Alt Text](https://media.giphy.com/media/ACpKIKVrOXuKY/giphy.gif)

# Why use Express? ie what can Express do that Node can't?
A: This is an Node server
```javascript
// Load HTTP module
let http = require("http");

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



## Let's create Quotes app using Node and Express - I do - You do (20 min)

Get to it:

1. `mkdir express-quotes`
2. `cd express-quotes`
3. `npm init` (Hit enter to accept the defaults and see the new [package.json](https://docs.npmjs.com/cli/init) file
4. `npm install express --save` (The `--save` option adds the module as a dependency in your package.json file. This allows anyone looking at your app (i.e. a dev team member) to be able to see what your app is "made of" and if they clone your app and run `npm install` all dependencies will be installed.
5. `touch app.js` in express-quotes directory

Check out the package.json file:

```json
"dependencies": {
  "express": "^4.11.1"
}
```

Let's start coding!

```javascript
// app.js
const express = require('express');
const app     = express();
const port    = process.env.PORT || 3000;

app.listen(port);
console.log(`express-quotes app running on port ${port}...`);
```
Notice the `listen` verb here - this can also be use, post, put, delete, etc. (As these are methods of the instance of [Express](https://expressjs.com/en/api.html)).

Notice `.env.PORT` we could hardcode the port and set it to 3000, but it's not the best practice, since the port may be not available...

In order for this to work, we need to
```bash
touch .env
```
and inside set `PORT=5000`.

Then, we need to run our app. In your `package.json`, modify "scripts" to reflect this:

```js
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node app.js",
    "dev": "nodemon app.js"
  },
```
What is `nodemon` you ask? It is a utility that will monitor your source file (app.js in our case) and automatically restart server. Otherwise, you would need to run `node app.js` after every small change in your file, annoying right 🙄 . We also need to install it first, hence in your terminal run

```bash
npm install --save nodemon
```

Navigate to `http://localhost:3000` and voila!

Now this is pretty awesome (isn't it?) but it doesn't really do anything. Plus, what if we want to start creating pages instead and render stuff on the page.

## Routing in Express - Intro (5 mins)

**Definition:** Routing refers to the definition of application end points (URIs) and how they respond to client requests. They can receive any of the http verbs (GET, POST, PUT, DELETE), and need to be prepared to handle them accordingly. Consider them resource identifiers, where a typical resource can be an image, webpage, music file, or a request to take kick off a function call. A function call could be something like executing a call to update/delete/put an entry in a database.

### Let's break down selective parts of a router

- **"/"**: Sets the pattern for our route. In this case, it's the root page
- **req**: Represents incoming http `request` object for end point resource.
- **res**: Represents the `resource` object that you give to the user/client/requestor. Resource can be a webpage, video file etc...
**Since both `req` and `res` are objects, they have various methods we can use to manipulate**
- **res.send:** is one of the methods of `response` object. It sends the response back to the requestor.

[ExpressJS 4.0](https://scotch.io/tutorials/learn-to-use-the-new-router-in-expressjs-4) comes with the new Router. Router is like a mini Express application. It doesn’t bring in views or settings but provides us with the routing APIs like `.use`, `.get`, `route` etc..

### Benefits of using express.Router():

- Helpful in separating out concerns
- Always has a dedicated handler to address any routes being requested.
- Modularity, mountable, and helps keep things DRY

Let's look at routes and handler callback functions in Express routes:
Example:
```javascript
app.get('/', function(req, res) {
  res.send('HELLOoOOOoOOoOOOooO, WORLD! <h1>This is ROOT (home) route</h1>');

});
```
Routes in Express are created using methods named after HTTP verbs. In the example above, we created a route to respond to GET requests at the root of the app. You will have a corresponding method on the app object for all the HTTP verbs.  In this example, we'll send back text as a response.

## Add routes to our application Codealong (20 min)

```javascript
const express = require('express');
const app     = express();
const port    = process.env.PORT || 3000;

app.get('/', function(req, res) {
  res.send('HELLOoOOOoOOoOOOooO, WORLD! <h1>This is ROOT route</h1>');
});

app.get('/quotes', function(req, res) {
  res.send('You hit quotes route');
});

app.get('/cats', function(req,res){
  res.send('This is cats route');
})
```

At the bottom of `app.js` add  this it will tell express middleware to use everything associated with quotes route and add a callback `quotes` to be executes on call:

```javascript
app.use('/quotes', quotes);
```
Then move to work in `routes/quotes.js` and ...
First we import express into `quotes.js` then we define our _router_ . This is what handles our routing. It's normally better to use this way of doing routes (and extracting them into their own files) as it makes applications more modular, and you won't have a 500 line app.js.

This way we created a dedicated router for this resource (quotes) and namespace its routes.
Hence we can separate all the route handlers in the different file: `routes/quotes.js` => Take out the from `app.js`

```js
function(req, res) {
  res.send('You hit quotes route');
}
```
and bring it to the quotes module, give a name to that function, and...

REMEMBER: to export it! 👍


#### Creating a quotes module

Let's move this module into another file to separate it from our `app.js`

```bash
$ mkdir routes
$ touch routes/quotes.js
```

Inside this file we need to move all of our route handlers for `quotes` and at the end of the file, we need to export our router:

```javascript
const router  = express.Router();

router.get('/', function(req, res) {
  res.send('This still works 👍');
});

module.exports = router;
```
> Note: don't forget to import the quotes as well :)

Now inside our app.js, let's require this router at the top:

```javascript
const quotes = require('./routes/quotes');

```

## Restful Routing - Intro (10 mins)

We will use the RESTful (should be familiar for you since Vince introduced it on Monday) standard to build our web apps. Today, we will only cover how to handle GET requests, but we can create callbacks for all types of requests. Let's create some routes for our quotes!

```javascript
// set up root route using 'GET' http verb
// get ALL quotes
router.get('/', function(req, res){
  res.json({
    quotes
  });
});

router.get('/:id', function(req, res){
  // let's reassign our parameter to `id` for readability
  let id = req.params.id;
  // id is passed as a string
  // need to parse it first
  parseInt(id);
  // now we can render it on the page!
  res.send(
    `
    <h1>${quotes[id].text}</h1>
    <h2>Genre: ${quotes[id].genre}</h2>
    <h3> By ${quotes[id].author}</h3>
    `
  )
});
```
## Independent Practice (30 minutes)

In the LECTURE directory you will find a `lab` folder. Look for instructions there.

## Conclusion (5 mins)
A framework can be overwhelming at the start, after a couple of days you will see how it makes your life easier.  We will work more on how to make RESTful controllers, this is just an introduction.





