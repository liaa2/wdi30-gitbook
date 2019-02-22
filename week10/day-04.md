# Day 04

### Express

Express is a light-weight web application framework to help organise your web application into an MVC architecture on the server side. You can use a variety of choices for your templating language \(like EJS, Jade, and Dust.js\). EJS would be a similar syntax to what we're use to with Rails erb.html files.

You can then use a database like MongoDB with Mongoose \(for modeling\) to provide a backend for your Node.js application. Express.js basically helps you manage everything, from routes, to handling requests and views.

### _Installing Express_ <a id="installing-express"></a>

Navigate to the root directory of your project and install express.

```bash
npm install --save express
```

`require` function is the easiest way to include modules that exist in separate files. The basic functionality of `require` is that it reads a javascript file, executes the file, and then proceeds to return the exports object.

```javascript
const express = require('express');
const app = express();

const server = app.listen(3000, () => {
  console.log("Server listening on port 3000...");
});
```

Now run `node server.js` from the terminal,  we should be able to get the following output:

```javascript
ba-express-server-no-db$ node server.js
Server listening on port 3000...
```

### Enable server restart on file changes <a id="enable-server-restart-on-file-changes"></a>

Any changes you make to your Express website are currently not visible until you restart the server. It quickly becomes very irritating to have to stop and restart your server every time you make a change, so it is worth taking the time to automate restarting the server when needed. One of the easiest such tools for this purpose is [nodemon](https://github.com/remy/nodemon). This is usually installed globally \(as it is a "tool"\), but here we'll install and use it locally as a developer dependency, so that any developers working with the project get it automatically when they install the application. Use the following command in the root directory for the skeleton project:

```bash
npm install --save nodemon
```

