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

