# webpack热更新

webpackHotDevClient 

## 步骤

1. webpack
2. webpack-dev-middleware，处理请求的返回值，如'/'返回index.html
3. webpack-dev-server
4. Wecsocket服务器，使用socket.io启动服务
5. webpack使用监听模式进行编译，编译成功后先把hash值发给客户端，再发送ok事件（hash事件设置curentHash，ok事件用于执行hotCheck）
