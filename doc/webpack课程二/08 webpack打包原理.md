# webpack打包原理

## plugins编写

webpack基于plugin实现功能

可以学习它自带的plugin编写

## webpack的打包原理

parser 将源码转化成ast
traverse 对ast进行遍历
generator 将ast转化成源码

baseDir 基础目录（会进行针对系统\\与/之间的转换）
entry 入口（会进行相对于入口路径进行处理为相对与根目录）
modules 所有模块

### 步骤

1. 读取文件内容
2. 源代码转化为抽象语法树
3. moduleId获取，即文件路径(使用baseDir，同时会对路径进行转换)
4. module，模块对象设置
5. 调用traverse 遍历语法树（require改为__webpack_require__）
6. 调用generator 将抽象语法树转化为源代码
7. module的_source属性添加并将module放置到modules中

### 实现

利用自定义函数想浏览器添加__webpack_require__方法
