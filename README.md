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

For example, the following will create a very simple end point on localhost:3000


```

const http = require('http')  
const port = 3000

const requestHandler = (request, response) => {  
  console.log('requestHandler', request.url);
  return require('izy-server')({}).handleRequest(request, response);
}

const server = http.createServer(requestHandler);

server.listen(port, (err) => {  
  if (err) {
    return console.log('something bad happened', err)
  }
  console.log(`server is listening on ${port}`)
});


```

Hitting http://localhost:3000/ will display the following message:

```
izyserver running. Please define processReq function to customize the behavior.
```

## NOTE
for more details, visit https://izyware.com
