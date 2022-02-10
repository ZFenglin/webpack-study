# 如何编写loader

## loader-runner

### loader类型

叠加顺序 => post(后置) + inline(内联) + normal(正常) + pre(前置)

### 特殊配置

-！ noPreAutoLoaders 不要前置和普通loader
! noAutoLoaders 不要普通loader
!! noPrePostAutoLoaders 不要前置，后置和普通loader，只要内联loader
