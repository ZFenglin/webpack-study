# hash

利用一个插件，将本次编译的结果，上传至七牛云cdn中，设置为强缓存便于后续访问 

占位符

ext 资源后缀名

name 文件名称

path 文件相对路径

folder 文件所在文件夹

hash 每次webpack构建生成的一个唯一的hash值

chunkhash 当前chunk的hash值（不可以和hash一起用），只有代码模块发生改变才改变，被引用的也会改变

contenthash 当前chunk中的文件内容生成 的hash值，只针对内容，被引入的部分内容不变，文件名不变
