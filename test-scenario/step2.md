Now we need to make a directory for our project through the following command:

`mkdir app`{{execute}}

Change into the directory 

`cd app`{{execute}}

While in this directory we have to create a json file. A json file is used within a node project to set predefined dependencies for the project.

`touch package.json`{{execute}}

Set a name and initial version number of your project along with a description of your app. Then change the placeholder author to your name and email address. Further, set main to the same  name as the main file running your server, as well as setting the start script  and express dependencies. 
` 
{
  "name": "dockerApp",
  "version": "1.0.0",
  "description": "NodeExpress with Docker",
  "author": "First Last <first.last@example.com>",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "express": "^4.16.1"
  }
}
`{{copy}}

Now we will run npm install to set up the project with npm. This will install all the dependencies we have specified in the package.json 


`npm install`{{execute}}

Now it is time to create the Node express server. We start out by creating the the file app.js. 


`touch app.js`{{execute}}


Copy and add these lines of code to app.js. 


```javascript
'use strict';

const express = require('express');

// Constants
const PORT = 8080;
const HOST = '0.0.0.0';

// App
const app = express();
app.get('/', (req, res) => {
  res.send('Hello World');
});

app.listen(PORT, HOST);
console.log(`Running on http://${HOST}:${PORT}`);


```{{copy}}

Running npm start in the terminal will then show: "Running on http://0.0.0.0:8080"


We have now set up a basic node express server and can proceed to the next part of this tutorial, using our server with docker. 
