# izy-server
Node.js server side components for interoperability with the Izy platform.

## INSTALLATION

If you are using npm (the Node.js package manager) always ensure that your npm is up-to-date by running:

`npm update -g npm`  

Then use:

`npm install izy-server`

## USING THE TOOL

In your node server, you can intercept any url and redirect it to the izy-server by:

```

return require('izy-server')({

/* config object for customizing the izy access */

}).handleRequest(request, response);    
```

For example, the following will create a very simple end point on https://localhost:3000/. It is worth mentionin that the *ui/node/direct* will convert http urls to https when called from https context, so it is important that your local server support https. Here is an example https server:

Generate the private key and certificate by: 

```
openssl genrsa 1024 > key.pem
openssl req -x509 -new -key key.pem > key-cert.pem
```

Then run the server: 

```

const port = 3000;
const https = require('https');
const fs = require('fs');

 var options = {
 key: fs.readFileSync('key.pem'),
 cert: fs.readFileSync('key-cert.pem')
 };

const requestHandler = (request, response) => {
   console.log('requestHandler', request.url);
   return require('izy-server')({}).handleRequest(request, response);
}

https.createServer(options, requestHandler).listen(port);
console.log('Listening on port: ', port);


```

Hitting https://localhost:3000/ will display the following message:

```
izyserver running. Please define processReq function to customize the behavior.
```

## NOTE
for more details, visit https://izyware.com
