# babel

前端开发环境必备工具

需要知道基本配置和使用

## 环境搭建和基本配置

### 环境搭建

安装@babel/cli @babel/core @babel/preset-env @babel/plugin-transform-runtime

### .babelrc 配置

### preset 和 plugins

babel 通过多个plugins进行转化

preset 为预设，是一堆plugins的集合

```js
{
    "preset": [
        ["@babel/preset-env"]
    ],
    "plugins": []

}
```

## babel-polyfill

安装 @babel/polyfill

polyfill 补丁，提供一些不支持的方法 

core.js 一个集成了ES6-新的JS的补丁polyfill， 但是不支持生成器和异步操作

regenerator  generator已经被放弃，改用async/await，regenerator用于支持generator

babel/polyfill  就是两者的集合

在 7.4之后弃用了regenerator，改用async/await，推荐直接使用core.js 和 regenerator

babel只处理语法 ，和符合ES5语法规范

### 按需引入babel-polyfill

```js
{
    "useBuiltIns": "usage",
    "core.js": 3 // babel版本号
}
```

## babel-runtime

babel-polyfill 的问题，污染全局系统，如果是第三方库，则会污染正式 项目的全局变量

利用babel/runtime可以用于处理这种情况，他会重新更改名称

安装 @babel/runtime @babel/plugin-transform-runtime

```js
{
    "preset": [
        ["@babel/preset-env"]
    ],
    "plugins": [
        [
            "@babel/plugin-transform-runtime", {
                "absoluteRuntime": false,
                "corejs": 3,
                "helpers": true,
                "regenerator": true,
                "useESModules": false,
            }
        ]
    ]
}
```
