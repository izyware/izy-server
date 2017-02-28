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

## NOTE
for more details, visit https://izyware.com
