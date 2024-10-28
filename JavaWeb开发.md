# JavaScript

## 01-函数

### 两种定义方式

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

#### 两种定义方式：

```
let 变量名 = new Array(元素列表)//方式一
let arr = new Array(1,2,3,4)
```

```
let 变量名 = [列表元素]
let arr = [1,2,3,4]
```

#### 访问：

```
arr[索引] = 值
```

#### 特点：

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

#### 两种方式定义：

```
let 变量名 = new String("...")
```

```
let 变量名 = "..."
```

![image-20241025090443828](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241025090443828.png)

### 3.JSON（JavaScript Object Notation ,JavaScript对象标记法）

#### js自定义对象

##### 定义格式：

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

##### 调用格式：

```
        console.log(user.name)
        user.eat()
```

#### JSON

**JSON是通过js对象标记法书写的文本**

JSON格式化工具

由于其语法简单，层次结构鲜明，现多用于作为数据载体，在网络中进行数据传输

##### 定义格式：

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

### 4.BOM