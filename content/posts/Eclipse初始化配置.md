---
title: "Eclipse初始化配置"
date: 2019-11-20T22:27:51+08:00
draft: true
---

### 进入首选项面板

  Windows --> Preferences

### 关闭一些服务

General --> Startup and Shutdown

Eclipse Automated Error Reporting去掉勾

### 设置记录空间数量

General --> Startup and Shutdown --> Workspaces --> Number of recent workspaces to remember:20

### 设置工作空间文件编码

  General --> Workspaces --> Text file encoding --> Other:UTF-8

### 注解格式

  Java --> Code Style --> Code Templates --> Comments --> Types --> Pattern

```
  /**

   \* @ClassName** : ${type_name}

   \* @Description** : **TODO**

   \* @author** : WengShiQuan

   \* @date** : ${date} ${time}

   */
```

### 关闭所有验证

  Validation --> Disable All

### XML一行的字符个数

  XML --> XML Files --> Editor --> Line Width:120

### 设置文件编码

  General --> Content Type --> Text --> Java Properties File --> Default encoding:UTF-8 --> Update



## STS（spring tool suite）修改默认编码

安装STS后首先要做的修改默认编码：

1、windows--perferences--general--workspace，Text file encoding设置成utf-8

2、windows--perferences--general--content types，把里面text的default encoding utf-8

3、windows--perferences--web--jsp files，将encoding设置成utf-8