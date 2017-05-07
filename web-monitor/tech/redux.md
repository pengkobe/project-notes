## Redux
> 本项目前端基于 react-redux ，这里做点小小的记录

## 文件结构
```
src/
    - index.html 入口页
    - index.js 初始化
      + 生成全局 store
      + 配置全局路由
      + 指定 history
    - store/
      + configureStore.js
        - 中间件
        - 初始化 reducer
      + configureStore.dev.js
      + configureStore.prod.js
    - reducers/  接收 state 与 action 作为参数
      + reducersGenerate
      + initialState
      + 具体的模块...
    - constants/
      + actionTypes action 常量
    - actions  根据 action 常量配置处理器
      + 具体的模块
   - containers/ 页面容器
   - components/ 组件
   - config/ 请求 API 配置
   - data/  基本的配置信息
   - util/ 包括对 fetch 与 promise 的封装
tools/

```

## 步骤
1. 在 config 中添加 log 地址
2. 在 constants 中添加 action 常量
3. 在 action 中添加对应的处理器
4. 在 reducer 中添加对应的处理器
5. 在 container 中添加容器
6. 在 routes.js 中添加对应的路由映射
