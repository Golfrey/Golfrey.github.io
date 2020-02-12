---
title: mac安装jdk以及jdk的设置
date: 2020-02-12 17:11:00
tags:
- java
- macos
categories: Learning
---

# mac安装jdk以及jdk的设置

## 从oracle的网站上安装jdk

安装网址https://www.oracle.com/technetwork/java/javase/overview/index.html

因为Oracle进行下载需要账号和密码，经过了紧张而刺激的测试以后，我发现自己完全做不到能够注册一个自己的号，但是网上还是好心人多啊，所以我进行了baidu搜索，发现了一个别人成功注册时的账号，完美的完成了下载。

账号：2696671285@qq.com

密码：Oracle123

让我们感谢这位好心人。同时，需要注意的是在下载的时候VPN需要挂载全局，否则下一个jdk能下到明年去。

## 下载后的安装与安装位置

下载后的jdk在mac上是pkg格式的，打开后一路点确定就可以了。

安装的默认位置在/Library/Java/JavaVirtualMachines

这时候，如果我们系统里只有一个jdk存在的话，只需要在终端里输入`java -version`即可以进行测试安装的正确性。

## 多个jdk版本的设定

如果你需要在很多jdk版本中进行切换，我们需要做什么呢？

这个问题很好，我们可以这样进行操作。

```bash
vim ~/.bash_profile
```

进入文件后，我们只要在最后加入这样一句话。

```bash
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home
```

这样就可以修改我们默认的jdk版本了。