---
title: Github two accounts settings
date: 2020-03-25 17:33:17
tags:
- Github
- Git
- Settings
categories: Learning
---

这篇文章主要讲一下如何在同一台电脑上进行两个github账号的设置。

## 需求分析

为什么需要两个github账号呢，理由有很多，比如说，工作账号和个人账号，个人账号和小号。至于为什么github都需要小号，那当然是因为原来的账号实在是显得太一事无成了，所以新创建github账号。

## SSH设置

```bash
ssh-keygen -t rsa -f ~/.ssh/id_rsa_2 -C "yourmail@xxx.com"
```

这样我们就可以在～/.ssh里面看到

在 `.ssh` 文件夹下新建 `config` 文件并编辑，另不同 Host 实际映射到同一 `HostName`，但密钥文件不同。Host 前缀可自定义，例子中`new`

```bash
# default                                                                       
Host github.com
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa
# two                                                                           
Host new.github.com
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa_2
```

这个文件是什么意思呢，就是将github.com对应为new.github.com，然后对应的ssh为`~/.ssh/id_rsa_2`。

## 添加至Github

相信这里就不需要教学了，如果有需要的话，可以自行Google。

## Clone Repo

将

```bash
git clone git@github.com:XXX
```

更改为

```bash
git clone git@new.github.com:XXX
```

即可。