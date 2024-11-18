# Maven(java项目的构建工具)

### 什么是Maven

maven是apache旗下的一个开源项目，是一款用于**管理和构建java项目的工具**。

### Maven的作用

#### 依赖管理

方便快捷的管理项目依赖的资源（jar包），避免版本冲突问题

简单修改信息后，maven会自动联网下载

#### 统一项目结构

提交标准、统一的项目结构

把所有开发工具（eclipse、idea等等）统一为maven结构

#### 项目结构

标准跨平台（macOS、Windows、Linux）

## 01 Maven概述

#### 介绍

- 是一个项目要管理和构建工具，基于项目对象模型（POM）的概念，通过一小段描述信息来管理项目的构建。
- 作用：
- - 方便的依赖管理
  - 统一的项目结构
  - 标准的项目构建流程
- 官网：[Maven – Welcome to Apache Maven](https://maven.apache.org/)

![image-20241109205122548](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241109205122548.png)



#### 安装

![image-20241109205942131](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241109205942131.png)



bin——存放可执行文件  指令：mvn

conf——存放maven的配置文件

lib——存放maven依赖的架包文件



#### 配置maven本地仓库

#### （在conf的setting.xml里面）

![image-20241109210459336](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241109210459336.png)

新建文件夹mvn_repo

#### 配置环境变量

在任意指令下可以使用maven指令

![image-20241109211153756](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241109211153756.png)

## 02 IDEA集成Maven

### 配置Maven环境（当前工程）白雪

File——Settings——Build,Execution,Deployment——Build Tools——Maven

设置IDEA使用本地安装的Maven，并修改配置文件及本地仓库路径

### 配置Maven环境（全局）

PS：idea版本不一样造成的差异很大，建议高版本

起始页（关闭工程退回）——Customize——All Settings

![image-20241110150159083](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241110150159083.png)

### 创建Maven项目

**1.创建模块，选择Maven，点击Next**

- 问题一：

2023版本idea在新建项目中直接创建java，点击下面的maven，在高级选项里配置组ID和工件ID

<img src="C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241110153834190.png" alt="image-20241110153834190" style="zoom:50%;" />

新建完成之后如果报错：无法解析插件，重启idea

- 问题二：

  - 现象：本地仓库（mvn-repo）中没有自动下载好文件

  - 原因：**文件夹没有修改权限！！！！**

  - 解决方法：更改users修改权限即可——文件夹右击-属性-安全-编辑-把允许下面的勾上

重新添加maven项目自动下载完成，问题解决

**2.填写模块名称，坐标信息，点击finish，创建完成**

**3.编写HelloWorld，并运行**



##### Maven坐标

- 什么是坐标？

  - maven中的坐标是资源的唯一标识，通过该坐标可以唯一定位资源位置

  - 使用坐标来定义项目或引入项目中需要的依赖

- maven坐标主要组成

  - groupId：定义当前Maven项目隶属组织名称（通常是域名反写：com:dodo）

  - artifactId：定义当前Maven项目名称（通常是模块名称，例如order-service、goods-service）

  - version：定义当前项目版本号

### 导入Maven环境

方法一：idea右侧

![15383048d7e0ffa00082df793e78dad0](F:\QQ\Documents\Files\Tencent Files\1317025828\nt_qq\nt_data\Pic\2024-11\Ori\15383048d7e0ffa00082df793e78dad0.png)

**选择pom.xml文件即可导入**

方法二：

项目结构——模块

![f3413bf6ccf0077a35b9958b5f34349d](F:\QQ\Documents\Files\Tencent Files\1317025828\nt_qq\nt_data\Pic\2024-11\Ori\f3413bf6ccf0077a35b9958b5f34349d.png)



## 依赖管理

### 依赖配置

- 依赖：当前项目运行所需要的jar包，一个项目中可以引入多个依赖

- 配置：

  - 在pom.xml中编写<dependencies>标签

  - 在<dependencies>标签中使用<dependency>引入标签

  - 定义坐标groupId，artifactId，version

  - 点击刷新按钮，引入最新加入的坐标

  

  官网：https://mvnrepository.com/

  ![image-20241111140407386](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241111140407386.png)

  更改依赖：

  ![d86d7d326772a561eb2809a205dec4d1](F:\QQ\Documents\Files\Tencent Files\1317025828\nt_qq\nt_data\Pic\2024-11\Ori\d86d7d326772a561eb2809a205dec4d1.png)

粘贴到<dependencies>标签中，scope不需要，删掉

![image-20241111140547542](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241111140547542.png)

然后点击右上角出现的加载按钮 重新加载

随后右侧Maven面板的logback版本就会更改



**注意事项：**

- 如果引入的依赖在本地仓库不存在，将会连接远程仓库/中央残酷，下载依赖
- 如果不知道依赖的坐标信息，可以到官网中搜索

### 依赖传递

依赖具有传递性：直接依赖、间接依赖

![image-20241111141345718](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241111141345718.png)

显示依赖图表：

![image-20241111141717481](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241111141717481.png)

![image-20241111141727435](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241111141727435.png)

排除依赖：![image-20241111142025082](C:\Users\13170\AppData\Roaming\Typora\typora-user-images\image-20241111142025082.png)

### 依赖范围

<scope>用于设置其作用范围

作用范围：

- 主程序范围有效（main文件夹范围内）
- 测试程序范围有效（test文件夹范围内）
- 是否参与打包运行（package指令范围内）

### 生命周期

为了对所有的maven项目构建过程进行抽象和统一

maven中有3套**相互独立**的生命周期：

- clean：清理工作
- default：核心工作，如：编译、测试、打包、安装、部署等
- site：生成报告、发布站点等

**执行指定生命周期的两种方式：**

- 在idea中，右侧的maven工具栏，选中对应的生命周期，双击执行
- 在命令行中，通过命令执行

# SpringBoot Web 基础篇

## SpringBootWeb入门

### spring

- 官网：[Spring | Home](https://spring.io/)
- Spring发展到今天已经形成了一种开发生态圈，Spring提供了若干个子项目，每个项目用于完成特定的功能。
- 非常快速的构建应用程序、简化开发、提高效率

**后端的开发从SpringBoot开始，贯穿始终**

### 快速入门

1. 创建springboot工程，并勾选web开发相关依赖

   文件——新建模块——Spring Initializr——

   ![image-20241115171159073](E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241115171159073.png)

2. 定义HelloController类，添加方法hello，并添加注解

   ```java
   package com.dodo.controller;
   
   import org.springframework.web.bind.annotation.RequestMapping;
   import org.springframework.web.bind.annotation.RestController;
   
   //请求处理类
   @RestController
   public class HelloController {
       @RequestMapping("/hello")
       public String hello(){
           System.out.println("hello world~");
           return "Hello World";
       }
   }
   ```

3. 运行测试

   <img src="E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241115173300219.png" alt="image-20241115173300219" style="zoom:50%;" />

## Http协议

### http概述

概念：**H**yper **T**ext **T**ransfer **P**rotocol，超文本传输协议，规定了浏览器和服务器之间数据传输的规则。

特点：

1. 基于TCP协议：面向连接，安全
2. 基于请求-响应模型的：一次请求对应一次响应
3. HTTP协议是无状态的协议：对于事务处理没有记忆能力。每次请求-响应都是独立的。

- 缺点：多次请求间不能共享数据
- 优点：速度快

### http请求协议

1.请求行：请求数据的第一行（请求方式、资源路径、协议）

2.请求头：第二行开始，格式key：value

- Host：请求的主机名
- User-Agent：浏览器版本
- Accept：浏览器能接受的资源类型
- Accept-Language：浏览器偏好的语言
- Accept-Encoding：浏览器可以支持的压缩类型
- Content-Type：请求主体的数据类型
- Content-Length：请求主体的大小（单位：字节）

3.请求体：POST请求，存放请求参数

![image-20241115192426598](E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241115192426598.png)

- 请求方式-GET：请求参数在请求行中，没有请求体。如：/01.GET-POST.html?name=dodo&password=123。GET请求大小是有限制的。
- 请求方式-POST：请求参数在请求体中，POST请求大小是没有限制的。

### http响应协议

- 响应行：响应数据第一行（协议、状态码、描述）
- 响应头：第二行开始，格式：key：value
- 响应体：最后一部分，存放响应数据

![image-20241115192726949](E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241115192726949.png)

![image-20241115193243472](E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241115193243472.png)

*1xx：你说，我在听     2xx：彳亍     3xx：绕另一边去     4xx：你干嘛呢？     5xx：我干嘛呢？*

状态码大全可以上网搜

### http协议解析

tomcat：一个软件程序，对http协议进行封装

## Web服务器-Tomcat

### 简介

- 概念：Apache核心项目，开源免费轻量级Web服务器，支持Servlet/JSP少量JavaEE规范
- JavaEE：java企业版。指java企业级开发的技术规范总和。包含13项技术规范：JDBC、JNDI、EJB、RMI、JSP、Servlet、XML、JMS、Java IDL、JTS、JTA、JavaMail、JAF
- Tomcat也被称为Web容器、Servlet容器。Servlet程序需要依赖于Tomcat才能运行
- 官网：[Apache Tomcat® - Welcome!](https://tomcat.apache.org/)



**小结：**

1.Web服务器

- 对HTTP协议操作进行封装，简化web程序开发。
- 部署web项目，对外提供网上信息浏览服务。

2.Tomcat

- 一个轻量级的web服务器，支持servlet、jsp等少量javaEE:规范。
- 也被称为web容器、servlet容器。

### 基本使用

http协议默认端口为80

### 入门程序解析

SpringBoot内置Tomcat，所以Tomcat可以不用下载安装（不过课内的Servlet还是要用滴）。

## 请求响应

- 请求：HttpServletRequest，获取请求数据

- 响应：HttpServletResponse，设置响应数据

- **BS架构**：Brower/Server，浏览器/服务器架构模式。客户端只需要浏览器，应用程序的逻辑和数据都存储在服务端。维护方便、体验一般。

  （京东、淘宝、唯品会。。。都是BS架构）

- CS架构：Client/Server，客户端/服务器架构模式。开发、维护麻烦、体验好。

  （微信、百度网盘、企业微信。。。都是CS架构）

### 请求

- #### Postman

前后端分离开发

postman是功能强大的网页调试与发送网页Http请求的Chrome插件

作用：常用于进行接口测试

安装：。。。

- #### 简单参数

原始方式：在原始的web程序中，获取请求参数，需要通过HttpServletRequest对象手动获取。

**SpringBoot方式**：

​	简单参数：参数名与形参变量名相同，定义形参即可接受参数

```java
    //SpringBoot方式
@RestController
public class RequestController {
    @RequestMapping("/simpleParam")
    public String simpleParam(String name , Integer age){//形参名
        System.out.println(name + ":" + age);
        return "OK";
    }
}
```

![a779b67ef82f3de7072c935976cc9b35](E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\a779b67ef82f3de7072c935976cc9b35.png)

**@RequestParam**中的required属性默认为true，代表该请求参数必须传递，如果不传递将报错。如果该参数是可选的，可以将required属性设置为false。

- #### 实体参数

![image-20241116154445372](E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241116154445372.png)

**简单实体参数：**

新建实体类User

```java
    private String name;
    private Integer age;
```

然后alt+insert生成对应的getter+setter+toString

```java
    @RequestMapping("/simplePojo")
    public String simplePojo(User user){
        System.out.println(user);
        return "OK";
    }
```

在RequestController类中调用User实体类



**复杂实体参数：**

新建实体类Address

```java
private String province;
private String city;
```

然后alt+insert生成对应的getter+setter+toString

在User加一个address的成员变量，生成getter和setter，重新生成toString

```java
    @RequestMapping("/complexPojo")
    public String complexPojo(User user){
        System.out.println(user);
        return "OK";
    }
```

在RequestController类中调用User实体类

在postman中send数据：

<img src="E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241116155108503.png" alt="image-20241116155108503" style="zoom: 50%;" />

即可在后台得到：

```
User{name='DODO', age=19, address=Address{province='北京', city='北京'}}
```



**小结：**

实体对象参数：请求参数名与形参对象属性名相同，即可直接通过POJO接受。



- #### 数组集合参数

element中的复选框组件（多选）



数组参数：请求参数名与形参中数组变量名相同，可以直接使用数组封装

```java
//用数组封装
	@RequestMapping("/arrayParam")
    public String arrayParam(String[] hobby){
        System.out.println(Arrays.toString(hobby));
        return "OK";
    }
```

集合参数：请求参数名与形参集合名称相同且请求参数为多个，@RequestParam绑定参数关系

```java
//用集合封装
    @RequestMapping("/listParam")
    public String listParam(@RequestParam List<String> hobby){
        System.out.println(hobby);
        return "OK";
    }
```



- #### 日期参数

- @DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss"规定格式。

  注意！！！：MM和HH必须为大写

- LocalDateTime方法获取时间

```java
    //4.日期时间参数
    @RequestMapping("/dateParam")
    public String dateParam(@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss") LocalDateTime updateTime){
        System.out.println(updateTime);
        return "OK";
    }
```



- #### Json参数

json参数：JSON数据键名与形参对象属性名相同，定义POJO类型形参即可接受参数，需要使用@RequestBody标识

```java
    @RequestMapping("/jsonParam")
    public String jsonParam(@RequestBody User user){
        System.out.println(user);
        return "OK";
    }
```



- #### 路径参数

通过请求URL直接传递参数，使用{...}来标识该路径参数，需要使用@PathVariable获取路径参数

```java
    @RequestMapping("/path/{id}")
    public String pathParam(@PathVariable Integer id){
        System.out.println(id);
        return "OK";
    }
```

获取多个路径：

```java
    @RequestMapping("/path/{id}/{name}")
    public String pathParam2(@PathVariable Integer id,@PathVariable String name ){
        System.out.println(id + ":" + name);
        return "OK";
    }
```



### 响应

统一响应结果：

```java
    public class Result{
        //响应码，1代表成功，0代表失败
        private Integer code;
        //提示信息
        private String msg;
        //返回的数据
        private Object data;
        //……
    }
```

### 分层解耦

#### 三层架构

![image-20241117163923972](E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241117163923972.png)

- controller：控制层，接受前端发送的请求，对请求进行处理，并响应数据。
- service：业务逻辑层，处理具体的业务逻辑。
- dao：数据访问层（Data Access Object）（持久层），负责数据访问操作，包括数据的增、删、改、查。

![image-20241117164738236](E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241117164738236.png)

#### 分层解耦

- 内聚：软件中各个功能模块内部的功能联系。
- 耦合：衡量软件中各个层/模块之间的依赖、关联的程度。
- 软件设计原则：高内聚低耦合

![image-20241119074253735](E:\markdown笔记\JavaWeb开发笔记\后端Web开发.assets\image-20241119074253735.png)



#### IOC&DI入门

#### IOC详解

#### DI详解







# MySQL

# SpringBoot Mybatis

# SpringBoot Web开发篇

# SpringBoot Web进阶篇