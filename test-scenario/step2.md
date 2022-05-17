# Creating a Node applictaion

Starting off we first need to CD into the correct directory

`cd example`{{execute}}

Then we need to make a directory for our project, let's call it app.

`mkdir app`{{execute}}

Now we enter the directory

`cd app`{{execute}}

While in the directory we create a new file called package.json. A json file is used within a node project to set predefined dependencies for the project.

`touch package.json`{{execute}}

In this json-file, set a name and initial version number of your project along with a description of your app. Then change the placeholder author to your name and email address. Further, set main to the same name as the file running your server, as well as setting the start script and express dependencies.

<pre class="file" data-target="clipboard">
{ 
  "name": "dockerApp", 
  "version": "1.0.0", 
  "description": "NodeExpress with Docker", 
  "author": "First Last <first.last@example.com>", 
  "main": "app.js", 
  "scripts": { "start": "node app.js" }, 
  "dependencies": { "express": "^4.16.1" } 
}
</pre>

Now we will run npm install to set up the project with npm. This will install all the dependencies we have specified in the package.json

`npm install`{{execute}}

Now we will create the main server through the file app.js. It is important to give the file the same name as declared in package.json.

`touch app.js`{{execute}}

Add this code to the app.js.

<pre class="file" data-target="clipboard"> 
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


</pre>

Running npm start in terminal will then show: Running on http://0.0.0.0:8080

We have now set up a basic node express server and can proceed to the next part of this tutorial, using our server with docker.

Please type `ctrl + c`{{execute}} before going to the next step, to ensure all commands run as they should.
