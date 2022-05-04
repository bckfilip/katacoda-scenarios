`mkdir app`{{copy}}

`cd app`{{copy}}

`touch package.json`{{copy}}

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


`npm install`{{excecute}}

`touch app.js`{{copy}}




`
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


`{{copy}}
