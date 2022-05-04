`mkdir app`{{execute}}

`cd app`{{execute}}

`touch package.json`{{execute}}

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


`npm install`{{execute}}

`touch app.js`{{execute}}




```
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
