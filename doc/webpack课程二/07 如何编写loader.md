# 如何编写loader

loader就是个函数，传入source, 返回一个新的source

## loader-runner

### loader类型

叠加顺序 => post(后置) + inline(内联) + normal(正常) + pre(前置)

从右往左执行

### 前缀特殊配置

-！ noPreAutoLoaders 不要前置和普通loader
! noAutoLoaders 不要普通loader
!! noPrePostAutoLoaders 不要前置，后置和普通loader，只要内联loader

### pitch

loader上增加pitch

当调用pitch存在方法时，则直接进行返回，不再继续执行，开始直接执行前面一个的loader

### loader编写

```js
const babel = require('babel-core');

function loader(source, inputSourceMap, data) {
    const options = {
        presets: ['es2015'],
        inputSourceMap: inputSourceMap,
        sourceMaps: true,
        filename: this.request.split('!')[1].split('/').pop()
    }
    let {
        code,
        map,
        ast
    } = babel.transform(source, options);
    return this.callback(null, code, map, ast);
}

module.exports = loader;
```
