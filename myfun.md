# myfun #

## 基础 ##
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
<<<<<<< HEAD
- v-for="i in 10"这个太奇怪了，没有个range，容易困惑
- v-for可以使用tempalte
- v-for 和 v-if 不要同时使用针对一个元素进行使用；可以分成2个元素，有层次感；如果在同一个元素中使用，那么for的优先级更高一点
- v-for 对于组件而言，必须有key参数

### 事件处理 ###
- 函数中的event是原生DOM事件，好似无论什么情况下都会存在；无论是否增加这个参数，真是奇怪。
- 但是直接调用函数，则不会有event变量
- event如果作为参数传递，那么可以使用$event; 函数内部使用的event就是参数的$event；类似data 和 $data 使用的位置不同
- v-on:click.stop 阻止传播，阻止冒泡
- v-on:click.prevent 阻止表单提交，即阻止 表单、a 的默认行为
- click修饰符可以串联： v-on:click.stop.preventv-on:click.stop.prevent
- v-on:click.capture 改变冒泡顺序，优先触发capture，再处理内部的东东；是不是适合拦截功能？
- stop 可以阻止capture
- v-on:submit 只能用在表单中，其他地方不好使
- 表单不提交： v-on:click.prevent  用于非form中； v-on:submit.prevent v-on:submit.prevent="xxx"用于form中
- 多个capture那么从最外层的优先级最高
- v-on:click.self 只自身元素点击时才响应
- v-on:click.once 只运行1次
- v-on:click.passive 告诉浏览器，进行响应，不用等待校验是否被阻止
- 对于更加复杂的键盘操作，需要在使用时，继续研究，目前看，各种各样的都是可以

### 表单输入绑定 ###
- 复选框的model，和点击顺序有关；复选select和 排列有关
- value 的值是不是最好也使用v-bind？？？
- radio checkbox 的value 竟然可以是object
- v-model.number 如果是数值，则返回number类型；如果无法被parseFloat解析，则返回原始类型，可能是string，或者其他
- v-model.trip：没写trip时，前后的空格竟然屏幕可能不会打印出来；但是确实被写入了变量中。

### 基础组件 ###
- 组件的data必须是函数，主要是为了创建不同作用域的值；如果不是函数，那么所有的组件都将为同一个值。
- v-on:functionname 来自定义子组件的函数；这样子就可以被调用
- 得回过头来再重新查看

## 深入了解组件 ##
### 注册组件 ###
- Vue.component 为全局注册，本地注册，直接在Vue中增加相关属性即可；确实得看下源码，这些问题都在源码中了
- 全局注册的行为必须在根 Vue 实例 (通过 new Vue) 创建之前发生
- 那么，怎么组织所有的组件呢，可以在main.js即入口处把所有的东东都集中起来，一次性导入所需要的。
- require.context在具体使用时再研究

### Prop ###
- 标签不区分大小写，但是代码一般要区分大小写，那么就存在转换的问题
- 不仅仅是标签的定义，属性的定义也有这个问题；所有的大写都不好使；包括props定义
- 最终都需要强的数据类型；但是强的数据类型会不会增加前端的复杂性？
- 
=======
- v-for="i in 10"这个太奇怪了，没有个ra65
>>>>>>> 7b23bcee342b13f32e24b87439ee28f86db0d97d
