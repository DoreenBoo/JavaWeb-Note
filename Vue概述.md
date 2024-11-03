# Vue概述

### 什么是Vue？

- vue是一套前端框架，免除原生JavaScript中的DOM操作，简化书写。
- 基于MVVM思想，实现数据的双向绑定，将编程的关注点放在数据上。
- 官网：[Vue.js](https://v2.cn.vuejs.org/)
- 框架：是一个半成品软件，是一套可重用的、通用的、软件基础代码模型。基于框架进行开发，更加快捷、更加高效。

### Vue快速入门

- 新建HTML页面，引入Vue.js文件

  ```
  <script src="js/vue.js"></script>
  ```

- 在JS代码区域，创建Vue核心对象，定义数据模型

  ```
  <script>
      new Vue({
          el:"#app", //vue接管区域
          data:{
              message:"Hello Vue"
          }
      })
  </script>
  ```

- 编写视图

```
    <div id="app">
        <input type="text" v-model="message">
        {{message}}
    </div>
```

![image-20241030182335411](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241030182335411.png)

**双向数据绑定**

**插值表达式：**

形式：{{表达式}}

内容可以是：

- 变量
- 三元运算符
- 函数调用
- 算术运算

# Vue常用指令

- 指令：HTML标签上带有v-前缀的特殊属性，不同指令具有不同含义，例如：v-if，v-if……
- 常用指令：

![image-20241031075635893](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241031075635893.png)

```
 <script>
        //定义Vue对象
        new Vue({
            el:"#app",//vue接管区域
            data:{
                url:"https://www.baidu.com"
            }
        })
    </Script>
```



## v-bind

```
<a v-bind:href="url">链接1</a>
<a :href="url">链接2</a> 
```

## v-model

```
<input type="text" v-model="url">
```

## v-on

```
<input type="button" value="点我一下" v-on:click="handle()">
```

```
    <script>
        //定义Vue对象
        new Vue({
            el: "#app",//vue接管区域
            data: {
                
            },
            methods:{
                handle:function(){
                    alert('你点我了一下')
                }
            }
        })
    </script>
```

## v-if & v-else-if & v-else

```
       年龄<input type="text" v-model="age">经判定，为：
       <span v-if="age <= 35">年轻人（35及以下）</span>
       <span v-else-if="age > 35 && age < 60">中年人（35-60）</span>
       <span v-else="age > 60">老年人（60及以上）</span>

```

## v-show

```
        年龄<input type="text" v-model="age">经判定，为：
        <span v-show="age <= 35">年轻人（35及以下）</span>
        <span v-show="age > 35 && age < 60">中年人（35-60）</span>
        <span v-show="age > 60">老年人（60及以上）</span>
```

全都渲染，只是通过css的display：none不展示出来

## v-for

```
    <div id="app">
        <div v-for="addr in addrs">{{addr}}</div>
        <hr>
        <div v-for="(addr,index) in addrs">{{index + 1}} : {{addr}}</div>
    </div>
```

```
    <script>
        //定义Vue对象
        new Vue({
            el: "#app",//vue接管区域
            data: {
                addrs:['北京','上海','西安','成都','深圳']
            },
            methods: {
              
            }
        })
    </script>
```

# vue生命周期

生命周期：指一个对象从创建到销毁的整个过程

生命周期的八个阶段：每触发一个生命周期事件，会自动执行一个生命周期方法（钩子）

![image-20241103172216679](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241103172216679.png)

![image-20241103172409037](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241103172409037.png)

 

mounted：挂载完成，Vue初始化成功，HTML页面渲染成功。（发送请求到服务端，加载数据）