# JavaScript

## 01-函数

两种定义方式

```
          function add(a, b) {
             return a + b;
         }
```

```
        let add = function (a,b){
            return a + b
        }
```

## 02-JS对象

### 1.Array

两种定义方式：

```
let 变量名 = new Array(元素列表)//方式一
let arr = new Array(1,2,3,4)
```

```
let 变量名 = [列表元素]
let arr = [1,2,3,4]
```

访问：

```
arr[索引] = 值
```

特点：

**长度可变，类型可变**

![image-20241025082513510](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241025082513510.png)

##### forEach()

```
    let arr = [1,2,3,4]
    arr[10] = 50
    arr.forEach(function(e){
    console.log(e)
```

##### push

```
	arr.push(7,8,9)
	console.log(arr)
```

##### splice(索引,长度)

```
    arr.splice(2,2)
    console.log(arr)//删除从索引2开始往后的两个索引，即删除3，4
```

##### ES6 箭头函数：(...) => {...}   --简化函数定义

```
arr.forEach((e) => {
console.log(e)
})
```

### 2.String

两种方式定义：

```
let 变量名 = new String("...")
```

```
let 变量名 = "..."
```

![image-20241025090443828](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241025090443828.png)

### 3.JSON（JavaScript Object Notation ,JavaScript对象标记法）

#### js自定义对象

定义格式：

```
        let user = {
            name: "Tom",
            age: 20,
            gender: "male",
            eat: function () {
                alert("用膳~")
            }
        }
```

调用格式：

```
        console.log(user.name)
        user.eat()
```

#### JSON

**JSON是通过js对象标记法书写的文本**

JSON格式化工具

由于其语法简单，层次结构鲜明，现多用于作为数据载体，在网络中进行数据传输

定义格式：

```
let 变量名 = '("key1": value1,"key2": value2)'
```

```
        //定义json
        let userStr = '{"name":"Jerry","age":18,"addr":["北京"，"上海"，"西安"]}'
        alert(userStr.name)

        //json字符串-->js对象
        let obj = JSON.parse(userStr)
        alert(obj.name)

        //js对象-->json字符串
        alert(JSON.stringify(obj));
```

### 4.BOM（Brower Object Model）

概念:

浏览器对象模型，允许JS与浏览器对话，JS将浏览器的各个组成部分封装为对象

组成:

- windows
- nacigator
- screen
- history
- location

#### Window

介绍：浏览器窗口对象

获取：直接使用window，其中window.可以省略。

```
window.alert("Hello Window")
alert("Hello Window")
```

属性：

- history: 对history对象的只读引用
- location: 用于窗口或框架的location对象
- navigation：对navigation对象的只读引用

方法：

- alert()

- confirm()——显示带有一段消息以及确认按钮和取消按钮的对话框

  ```
          //有返回值：确认：true 取消：false
           let flag = confirm('您确认删除该记录吗？')
           alert(flag)
  ```

- setlnterval()——按照指定的周期（以毫秒计）来调用函数或计算表达式

  ```
          //定时器 - setInterval -- 周期性的执行某一个函数
          let i = 0
          setInterval(function(){
              i++
              console.log(`定时器执行了${i}次`);
              
          },2000)
  ```

- setTimeout()——在指定的毫秒数后调用函数或计算表达式

```
        //定时器 - setTimeout --延迟指定时间执行一次
        setTimeout(function(){
            alert('js')
        },3000)
```

#### Location

介绍：地址栏对象

获取：location.属性

属性：href：设置或返回完整的URL

```
location.href = "https://www.itcast.cn"
```



### 5.DOM(Document Object Model)

**概念：**文档对象模型

**将标记语言的各个组成部分封装为对应的对象：**

- document：整个文档对象
- element：元素对象
- attribute：属性对象
- text：文本对象
- comment：注释对象

**js通过DOM，就能够对HTML进行操作：**

- 改变HTML元素的内容
- 改变HTML元素的样式（CSS）
- 对HTML DOM事件作出反应
- 添加和删除HTML元素

#### 1.获取Element元素

##### 1.1获取元素-根据ID获取

```
let img = document.getElementById('h1')
alert(img)
```

##### 1.2 获取元素-根据标签获取

```
let divs = document.getElementsByTagName('div')
for(let i = 0;i < divs.length;i++){
    alert(divs[i])
   }
```

##### 1.3 获取元素-根据name属性获取

```
let ins = document.getElementsByName('hobby')
for (let i = 0; i < divs.length; i++) {
     alert(ins[i])        
}
```

##### 1.4 获取元素-根据class属性获取

```
let divs = document.getElementsByClassName('cls')
for (let i = 0; i < divs.length; i++) {
     alert(divs[i])    
    }
```

#### 2.查询参考手册，属性、方法

element.innerHTML   设置或返回元素的内容

```
    let divs = document.getElementsByClassName('cls')
    let div1 = divs[0]

    div1.innerHTML = '传智教育666'
```

## 03-JS事件

### 事件监听

事件：HTML事件是发生在HTML元素上的“事情”，比如：

- 按钮被点击
- 鼠标移动到元素上
- 按下键盘按钮

事件监听：JS可以在事件被侦测到时**执行代码**

```
<body>
    <input type="button" id="btn1" value="事件绑定1" onclick="on()">
    <input type="button" id="btn2" value="事件绑定2">
</body>

<script>
    //方法一：通过HTML标签中的事件属性进行绑定
    function on() {
        alert('按钮1被点击了')
    }
    //方法二：通过DOM元素属性绑定
    document.getElementById('btn2').onclick = function () {
        alert('按钮2被点击了')
    }
</script>
```

### 常见事件

![image-20241028190247349](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241028190247349.png)