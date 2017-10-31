## socket.io 一直报 404
其实服务端初始化不正确，说什么头没有设置其实是迷惑人的,具体代码参见 TAG 1.O
参考: https://stackoverflow.com/questions/35713682/socket-io-gives-cors-error-even-if-i-allowed-cors-it-on-server
#### 初始化2次
**TODO:**服务端的一个方法被初始化两次了，但是前段明明只调用了一次啊，通过 clearTimeout 方法临时解决了下，这个还得继续研究


## EGG 
按照[文档](https://eggjs.org/zh-cn/core/deployment.html)部署后，死活运行不成功，其中虽然有提示说
`Db.prototype.authenticate method will...`,但是这个仅仅是警告而已，后来查到该[ISSUE](https://github.com/eggjs/egg/issues/1353),其中
有说到，
> 1. ssh 到服务器上，不用 daemon 启动，看看控制台输出是啥
2. 确认下你的服务器的文档，是不是必须指定环境变量为启动端口，或者 workers 数量有限制 （譬如 leadcloud 和 sinaapp 就有限制，不确定你用的阿里云有没有）  

试着将 daemon 参数去掉，结果运行成功！顺带说一下，--daemon 只是把日志重定向到文件而已，不输出到控制台。  
~~经测试，在 screen -S 新创建的窗口中是可以加上 --daemon 并执行成功的！~~

* 启动后磁盘读写莫名增高，经过一会开始恢复正常，其中有切换端口号进行尝试，不知道是不是这个的影响

#### koa-send
有着自己的一套返回机制，找不到文件时会自动返回 404，自己一直怀疑是路由坏了是没道理的！



## EXPRESS
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

## KOA2
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
