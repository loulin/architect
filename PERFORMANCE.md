# Load Balance

## Node.js cluster module

```javascript
var cluster = require('cluster');  
var http    = require('http');  
var os      = require('os');

var numCPUs = os.cpus().length;

if (cluster.isMaster) { 
  for (var i = 0; i < numCPUs; ++i) {
    cluster.fork();
  }
} else {
  // Worker: HTTP servers share the same TCP connection via IPC
  http.createServer(function(req, res) {
    res.status(200).end("Hello World");
  }).listen(8080);
}
```

## PM2 Built-in clustering

`pm2 start app.js -i <number of workers>` pm2 auto restarts died workers.
`-i 0` is equal to `-i <number of cpu cores>`
`pm2 reload app.js` restarts the workers one by one.
`pm2 gracefulReload app.js` sends a shutdown signal via IPC.
```javascript
process.on('message', function(message) {  
  if (message === 'shutdown') {
    // custome tasks can be performed
    process.exit(0);
  }
});
```

## Load Balance Server
Nginx / Cloud LBS

# Profiling
