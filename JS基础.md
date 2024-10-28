# JS基础Day1

## 01-体验js

```
## 

<style>
    .pink{
        background-color: pink;
    }
</style>

<body>
    <button class="pink">按钮1</button>
    <button>按钮2</button>
    <button>按钮3</button>
    <button>按钮4</button>

    <script>
        let bts = document.querySelectorAll('button')
        for(let i = 0;i < bts.length; i++){
            bts[i].addEventListener('click',function(){
                document.querySelector('.pink').className = ''
                this.className = 'pink'
            })
        }
    </script>

</body>
```

## 02-js书写规范

```
<body>

  *<!-- 内部js -->*

    <script>

    *// 页面弹出警示框*

    alert('你好，js')

  </script>

</body>
```

## 03-js书写位置

- 内部
- 内部-写到</body>标签上方
- 外部-但是<script>标签不要写内容，否则会被忽略

## 04-js注释和结束符

- 单行注释//
- 多行注释/**/
- js末尾可加分号，也可以不加。按照自己的喜好写代码。

## 05-输入和输出语法

### 1.输出语法

#### 语法1：文档输出内容

```
document.write('<h1>This is a title<h1>')
```

#### 语法2：页面弹出警示框

```
alert('你好，js')
```

#### 语法3：控制台输出内容（程序员调试使用）

```
console.log('看看对不对')
```

<img src="C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241019121621524.png" alt="image-20241019121621524" style="zoom:80%;" />

** console 控制台；log 日志

** 快捷：输入log自动生成。

### 2.输入语句

语法：

```
prompt('请输入您的年龄')
```

<img src="C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241019122757208.png" alt="image-20241019122757208" style="zoom: 50%;" />

## 06-变量的声明和赋值

### 1.变量怎么理解

变量是一个装东西的盒子

是计算机中用来存储数据的“容器”，可以让计算机变得有记忆

### 2.变量的基本使用

1. 声明变量：

   先创建变量：关键字（let）、变量名（标识）

```
let 变量名
```

​	2.变量赋值：

```
        // 声明的同时直接赋值 变量的初始化
        let age = 18
```

## 07-变量的更新以及输入用户名案例

<img src="C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241019191742757.png" alt="image-20241019191742757" style="zoom: 67%;" />

​								行后报错插件

```
        let age = 18
        age = 19
        console.log(age);//19
```

### 1.变量更新

ps：let不允许多次声明一个变量。

### 2.声明多个变量

（类似css中的并集选择器）

不提倡，可读性不好

## 08-交互两个变量的案例

```
let num1 = 10
let num2 = 20
 //交换
let temp = num1
num1 = num2
num2 = temp
console.log(num1,num2);
```

## 09-变量的本质和命名规则

### 1.变量的本质

**内存：**计算机中存储数据的地方，相当于一个空间

**变量本质：**是程序在内存中申请的一块用来存放数据的小空间

![image-20241019194342728](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241019194342728.png)

### 2.变量的命名规则与规范

js严格区分大小写

## 10-输入姓名案例以及var和let的区别

#### 1.案例

```
        let name = prompt('input u name please')
        let age = prompt('input u name age')
        let gender = prompt('input u name gender')

        document.write(name)
        document.write(age)
        document.write(gender)
```

#### 2.var和let的区别

var——老版js中出现

不合理：先声明 再使用；可以重复声明

## 11-数组的基本使用

### 变量拓展-数组

数组Array——一种将**一组数据存储在单个变量名下**的优雅方式

```
let arr = []
```

#### 数组长度 = 索引号 + 1

```
console.log(arr.length)
```

## 12-常量

使用const声明的量叫常量

```
const G = 9.8
```

- 不允许再次声明，不能更改
- 声明的时候必须赋值

**总结：**不需要重新赋值的数据使用const

## 13-数字数据类型和算数运算符

**js是弱数据类型的语言**，java是强数据类型的语言

- 数字类型Number

  NaN代表一个计算错误(Not a Number)

## 14-字符串数据类型以及拼接

- 字符串类型string

  通过**单引号、双引号、反引号**包裹的数据都叫字符串

  单引号和双引号可以互相嵌套，但是不能自己嵌套自己

  必要时可以使用转义符\

  

## 15-模板字符串***

#### 使用场景：

拼接字符串和常量

#### 语法：

- ··（反引号）
- tab上面那个键
- 内容拼接变量时，用**${}**包住变量

```
        let age = 18
        document.write(`我今年${age}岁了`)
```

## 16-布尔型、null和undefined

boolean

null

undefined：只声明变量，不赋值的情况下

#### typeof关键字检测数据类型

- 作为运算符：typeof(x)
- 函数形式：typeof(x)

有括号和没括号得到的结果是一样的，所以直接使用**运算符**的写法

## 17-隐式转换和显式转换

### 1.隐式转换

- +两边只要有一个是字符串。都会把另外一个转成字符串
- 除了+以外的算术运算符，比如-*/等都会把数据转换成数字类型

#### 技巧：

- +作为正号解析可以转换为数字型
- 任何数据和字符串相加的结果都是字符串 

### 2.显式转换

```
let str = '123'
console.log(Number(str))//123

console.log(parseInt('12px'))//12
console.log(parseInt('12.34px'))//12

console.log(parseFloat('12.34px'))//12.34
```

#### 常见问题:

<img src="C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241021120825409.png" alt="image-20241021120825409" style="zoom: 80%;" />  

## 18-渲染表格案例

```
        <script>
            let price = prompt('请输入商品价格')
            let num = prompt('请输入商品数量')
            let address = prompt('请输入收货地址')
            let total = price * num

​            //页面打印渲染
​            document.write(`  
              <table>
                    <tr>
                        <th>商品名称</th>
                        <th>商品价格</th>
                        <th>商品数量</th>
                        <th>总价</th>
                        <th>收货地址</th>
                    </tr>
                    <tr>
                        <td>小米手机</td>
                        <td>${price}元</td>
                        <td>${num}</td>
                        <td>${total}元</td>
                        <td>${address}</td>
                    </tr>
                </table>`
​            )
​        </script>
```

**table标签可以放在write函数里面

# JS基础Day2

## 01运算符

### 19-赋值运算符

将等号右边的值赋予给左边，要求左边必须是一个容器

其他运算符：+=、-=、*=、/=、%=

### 20-自增运算符

#### 一元运算符

##### 自增：++

- ###### 前置自增：先+1在计算  


```
        // 前置自增
        let i = 1
        console.log(++i + 1);//3
```

- ###### 后置自增：先计算再+1

```
        //后置自增 
        let i = 1
        console.log(i++ + 1);//2 
```

##### 自减：--

### 21-比较运算符

==：左右两边值是否相等

===：左右两边是否类型和值都相等

![image-20241021205428236](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241021205428236.png)

### 22-逻辑运算符

&&逻辑与

||逻辑或

！逻辑非

## 02语句

### 23-if单分支语句

```
if(){
}
```

### 24-if双分支语句

```
if(){
}else{
}
```

### 25-if多分支语句

```
if(){
}else if(){
}else{
}
```

### 

