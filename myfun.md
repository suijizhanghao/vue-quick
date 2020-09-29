# myfun #

### 计算属性与侦听器 ###
- 计算属性，应该就是：绑定文本与绑定函数的区别；要是能合并到data最好了，能自动识别是个函数。
- 计算属性，只是没有默认的setter
- 基于响应式的东东，一般都是有缓存的，会先diff是否变化，变化之后才会进一步响应；而函数，只要被调用，就会执行一次；这也是计算属性和函数的差别
- computed 和 watch ：看应用场景，以及对数据的理解
- 异步的问题需要进一步确认

### Class与Style绑定 ###
- class作为增强的使用方式，比较常用的依然是计算属性的方式
- 数组的写法与object的略有不同；使用方法以至于交互是不同的；数组的方式，如果key为null，好似就等于object的false了
- class 和 style的bind方式竟然是不同的；这么看的话，都绑定到对象 或者 计算属性，会更加容易理解一些
- style的数组，职能绑定object，是可以绑定多个object的； 和class的数组依然略有不同
- class key 是class；style的value是值

### 条件渲染 ###
- template 可以作为一个代码块，且不会去渲染 template本身
- 如果绑定了v-model，那么key什么时候使用？
- v-if 的dom不会保存在浏览器中，lazy加载模式；v-show已经加载到dom中了，只是没有显示，非lazy加载模式
- v-show不支持template
- v-show 实现原理：控制 style="display: none;"
- v-if 和 v-for不建议在一块使用

### 列表渲染 ###
- 对于任意的标签，都可以使用v-for，不只是li
- for可以对object进行for，依次获取每个key的信息，但是顺序和浏览器有关系；当前测试是和定义的顺序有关系。
- 对于list进行for时，可以有v-bind:key
- 对于重新绑定问题，现在确实让人费解
- 为了不改变数组的值，可以通过计算属性方式重新生成一个值，然后来调用
- v-for="i in 10"这个太奇怪了，没有个ra65