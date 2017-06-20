## 服务端
使用 koa2 构建服务端，初始化项目参考 smallPath 的 [Blog](https://github.com/smallpath/blog) 项目,带有这些内容
* redis
* mongoose
* log4js
* jwt
* RESTful API
 
#### 附带技术
* 日志分级并做好存储  
* 使用 Redis 作为缓存，并进行高并发量进行测试
* 数据持久化存储使用 Mongodb( mongoose)
* 做好在线监控(埋点等..)
* 试一试分布式

## File Structure
```
mongoRest
  - index， 路由集中生成
  - actions， Rest 操作处理
  - routes,路由

```