---
title: "SpringToolSuite快速创建一个springboot项目"
date: 2019-11-19T14:05:58+08:00
draft: true
---
首先下载一个专为Spring设计的eclipse版本——sts，官网链接：[Spring tool suite 4]( https://spring.io/tools )，这个IDE和eclipse非常相似，下载解压后可以直接运行；

#### 开始创建项目，本篇讲述从STS直接创建项目  

##### new——>Spring Starter Project

<img src="https://github.com/wengshiquan/imgs/blob/master/blog/001-SpringToolSuite%E5%BF%AB%E9%80%9F%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AAspringboot%E9%A1%B9%E7%9B%AE/001-01.png?raw=true" alt="001-01.png" style="zoom: 33%;" />

##### 接着，name填入项目名称，group随意，其他的不用管，这里的service URL指Spring boot官网地址。

<img src="https://github.com/wengshiquan/imgs/blob/master/blog/001-SpringToolSuite%E5%BF%AB%E9%80%9F%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AAspringboot%E9%A1%B9%E7%9B%AE/001-02.png?raw=true" alt="001-02.png" style="zoom: 50%;" />

##### next，version选择1.5.11（如果是2.0以上的也可以），Available中输入查找web选择和DevTools选项，选中。

<img src="https://github.com/wengshiquan/imgs/blob/master/blog/001-SpringToolSuite%E5%BF%AB%E9%80%9F%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AAspringboot%E9%A1%B9%E7%9B%AE/001-03.png?raw=true" alt="001-03.png" style="zoom: 50%;" />

##### 点击next/finish均可，项目创建完毕，目录如下：

<img src="https://github.com/wengshiquan/imgs/blob/master/blog/001-SpringToolSuite%E5%BF%AB%E9%80%9F%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AAspringboot%E9%A1%B9%E7%9B%AE/001-04.png?raw=true" alt="001-04.png" style="zoom: 67%;" />

这个目录结构与eclipse中建立的maven项目基本一致。



注意：

项目创建过程中，会发现首次使用maven的时候从中央仓库下载jar包非常慢，这里可以使用阿里提供的镜像。找到STS/项目使用的maven的setting.xml文件，在其中的<mirrors>中添加如下代码：

```
<mirror>

   <id>alimaven</id>

   <name>aliyun maven</name>

   <url>http://maven.aliyun.com/nexus/content/groups/public/</url>

   <mirrorOf>central</mirrorOf>    

  </mirror>
```

这个代码的意思是指定从阿里的镜像仓库下载jar包，配置完毕后重新创建项目即可。

##### 写一个简单的示例  

```
SpringBoot项目创建好了，但是这个项目怎么用呢，它好像和之前接触的项目结构不大一样。下面讲述一个简单的实现前端请求与后端返回页面的功能示例；  
```

 在src/man/java中创建如下Controller类：

![001-05.png](https://github.com/wengshiquan/imgs/blob/master/blog/001-SpringToolSuite%E5%BF%AB%E9%80%9F%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AAspringboot%E9%A1%B9%E7%9B%AE/001-05.png?raw=true)

```
package com.example.demo.controller;
 
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
 
 
@Controller //标识一个控制器 接收用户请求,RestController=Controller+ResponseBody
public class TestController {
	
	@RequestMapping("/index.do")//HTTP请求
	public String test() {
		System.out.println("TestController>>>test>>>is running....return a string");
		return "index";//返回一个视图（HTML页面）
	}
}
```

在src/man/resources中的template文件夹下创建一个index.html（注意SpringBoot默认是不支持jsp的）  

```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<title>Insert title here</title>
</head>
<body>
  hello,this is index.html2...
</body>
</html>
```

跟着，为了使得SpringBoot能够返回前端界面，需要在pom.xml中添加一个依赖。

```
<dependency>
		  <groupId>org.springframework.boot</groupId>
		  <artifactId>spring-boot-starter-thymeleaf</artifactId>
		  <scope></scope>
</dependency>
```

然后，我们可以在src/main/resouces中创建一个配置文件application.properties，说明如代码所示。

```
#server config
#快捷键 crtl + /
#配置服务器
 
#端口
server.port=80
#上下文访问路径
server.servlet.context-path=/test
```

下面点击项目run as——>Spring Boot App，在浏览器中输入localhost:80/test/index.do，就会跳出index.html的内容。

<img src="https://github.com/wengshiquan/imgs/blob/master/blog/001-SpringToolSuite%E5%BF%AB%E9%80%9F%E5%88%9B%E5%BB%BA%E4%B8%80%E4%B8%AAspringboot%E9%A1%B9%E7%9B%AE/001-06.png?raw=true" alt="001-06.png" style="zoom:50%;" />

ok，一个简单的SpringBoot项目示例写好了

