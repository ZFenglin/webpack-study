# tree-shaking

babel-plugin-import

babel 插件的返回一个函数，函数参数为babel，返回值为一个对象，对象存在visitor访问器属性 

```js
const visitor = {
    enter(path, state = {
        opts
    }) {
        const specifiers = path.node.specifiers; //{{flatten, concat}}
        const source = path.node.source; // lodash
        if (
            state.opts.library == source.value && // webpack设置页面的library和lodash对应上
            !types.isImportDefaultSpecifier(specifiers[0])
        ) {
            const declaration = path.node.specifiers.map((specifier, index) => {
                return types.ImportDeclaration(
                    [types.importDefaultSpecifier(specifier.local)], // 普通导入更换为默认导入
                    types.stringLiteral(`${source.value}/${specifier.local.name}`)
                );
            })
            path.replaceWithMultiple(declaration);
        }
    }
}

module.exports = function(babel) {
    return {
        visitor
    }
}
```
