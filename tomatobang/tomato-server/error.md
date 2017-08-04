# socket.io 一直报 404
其实服务端初始化不正确，说什么头没有设置其实是迷惑人的
参考: https://stackoverflow.com/questions/35713682/socket-io-gives-cors-error-even-if-i-allowed-cors-it-on-server

#### EXPRESS
```javascript
app.set('port', port);
var server = http.createServer(app);
/**
 * Create HTTP server.
 */
var server = http.createServer(app);

/*
* setup socket.io, and socket-session
*/
var socketIO = require('socket.io');
var io = socketIO(server);
```

#### KOA2
```javascript
let server=  app.listen(config.serverPort, () => {
    log.info(`Koa2 is running at ${config.serverPort}`);
});
var io = require('socket.io').listen(server);
```
还有人直接使用到了库来解决问题: https://github.com/mattstyles/koa-socket  / https://github.com/LnsooXD/koa-socket.io
此外有些人事这样子写的,但是我硬是没有试验成功
```javascript
let server = require('http').Server(app.callback());
    let io     = require('socket.io')(server);
    require('./main')(io);
    return server;
```
