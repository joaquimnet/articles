# Your First NodeJS REST API

TODO: write words

## Requirements

Node - the runtime

npm - the package manager

express - the api framework

cors - cors middleware

### Starting the project

```sh
cd /some/folder
mkdir rest-api
cd rest-api
npm init -y
```

### Install the dependencies

```sh
npm install express cors
```

### Express App

```javascript
// /some/folder/rest-api/index.js
const express = require('express');

const app = express();
```

### Your first route

```javascript
// /some/folder/rest-api/index.js
const express = require('express');

const app = express();

app.get('/', (req, res) => {
  res.send({message: 'Hello and welcome to my API!'});
});
```

### Content

```javascript
// /some/folder/rest-api/index.js
const express = require('express');

const app = express();

app.get('/jokes', (req, res) => {
  const jokes = ['Why do we only have spoons? Because we don\'t fork around.'];
  res.send(jokes[0]);
});

app.get('/', (req, res) => {
  res.send({message: 'Hello and welcome to my API!'});
});

app.use((req, res) => {
  res.status(404).send({message: 'Not found'});
});
```

### Web App Ports

```javascript
// /some/folder/rest-api/index.js
const express = require('express');

const app = express();

app.get('/jokes', (req, res) => {
  const jokes = ['Why do we only have spoons? Because we don\'t fork around.'];
  res.send(jokes[0]);
});

app.get('/', (req, res) => {
  res.send({message: 'Hello and welcome to my API!'});
});

app.use((req, res) => {
  res.status(404).send({message: 'Not found'});
});

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log('Listening on port', PORT);
  console.log('Press Ctrl+C to quit.');
});
```

### Cross Origin Resource Sharing

```javascript
// /some/folder/rest-api/index.js
const express = require('express');
const cors = require('cors');

const app = express();

app.use(cors());

app.get('/jokes', (req, res) => {
  const jokes = ['Why do we only have spoons? Because we don\'t fork around.'];
  res.send(jokes[0]);
});

app.get('/', (req, res) => {
  res.send({message: 'Hello and welcome to my API!'});
});

app.use((req, res) => {
  res.status(404).send({message: 'Not found'});
});

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log('Listening on port', PORT);
  console.log('Press Ctrl+C to quit.');
});
```

### Request logging middleware

```javascript
// /some/folder/rest-api/index.js
const express = require('express');
const cors = require('cors');

const app = express();

app.use(cors());
app.use((req, res, next) => {
  console.log(new Date().toLocaleString(), `${req.method} ${req.path}`);
  next();
});

app.get('/jokes', (req, res) => {
  const jokes = ['Why do we only have spoons? Because we don\'t fork around.'];
  res.send(jokes[0]);
});

app.get('/', (req, res) => {
  res.send({message: 'Hello and welcome to my API!'});
});

app.use((req, res) => {
  res.status(404).send({message: 'Not found'});
});

const PORT = process.env.PORT || 3000;

app.listen(PORT, () => {
  console.log('Listening on port', PORT);
  console.log('Press Ctrl+C to quit.');
});
```
