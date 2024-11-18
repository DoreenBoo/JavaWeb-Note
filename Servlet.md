# Servlet的实现

问题：继承HttpServlet时找不到HttpServlet类

1. 在web-inf文件夹下建一个lib文件夹
2. 将本项目中使用的tomcat版本，寻找目录中servlet-api.jar
3. 将servlet-api.jar包复制在第一步建立的lib文件下
4. 在项目中点击Add as Library 即可

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/ee9d4e84842dc79534131a7b9bbdb5d4.png#pic_center)

# HttpSerlvletRequest获取请求

## 常用方法

### 1.获取请求时的完整路径（从http开始，到"?"前面结束）

```java
String url = req.getRequestURL() + "";//加空转码为StringButter
System.out.println("获取请求时的完整路径：" + url);
```

### 2.获取请求时的部分路径（从项目的站点名开始，到"?"前面结束）

```java
String uri = req.getRequestURI();
System.out.println("获取请求时的部分路径：" + uri);
```

### 3.获取请求时的参数字符串（从"?"后面开始，到最后的字符串）

```java
String queryString = req.getQueryString();
System.out.println("获取请求时的参数字符串:" + queryString);
```

### 4.获取请求方式（Get和Post）

```java
String method = req.getMethod();
System.out.println("获取请求方式:" + method);
```

### 5.获取当前协议版本（HTTP/1.1）

```java
String prototol = req.getProtocol();
System.out.println("获取当前协议版本:" + prototol);
```

### 6.获取项目的站点名（项目对外访问路径）

```java
String webapp = req.getContextPath();//上下文路径
System.out.println("获取项目的站点名:" + webapp);
```



## 获取请求的参数

###  7.获取指定名称的参数值（重点！！！！！！！！！！）

```java
String uname = req.getParameter("uname");
String upwd = req.getParameter("upwd");
System.out.println("uname:" + uname + ",upwd:" + upwd);
```

### 8.获取指定名称的参数的所有参数值,返回字符串数组（用于复选框传值）

```java
String[] hobbys = req.getParameterValues("hobby");
//判断数组为空
if (hobbys != null && hobbys.length > 0){
    for (String hobby:hobbys) {
        System.out.println("爱好：" + hobby);
    }
}
```

# HttpSerlvletRequest请求转发



可以让请求从服务端跳转到客户端（或跳转到指定servlet）
**特点：**
     1.服务端行为
     2.地址栏不发生改变
     3.从始至终只有一个请求
     4.request数据可以共享

















