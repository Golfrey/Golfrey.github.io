---
title: Github连接与更新
date: 2020-02-11 22:10:37
tags: 
- Git

categories: Learning
---

# Git 学习笔记

## Github和本地建立与连接

1. 建立本地git文件夹

   ```bash
   git init
   ```

2. 和远程服务器建立联系

   ```bash
   git remote add origin 
   ```

## 本地更新远程服务器

1. 从远程获取最新版本到本地

   ```bash
   git fetch origin <your want branch>
   ```

   从远程的origin的master主分支下载最新的版本到origin/master分支上

2. 比较本地的master分支和origin/master分支的差别

   `git fetch`和`git pull`的区别在与`git fetch`只是将origin/master的最新内容拉到本地，而不更新本地的master分支。

3. 进行合并

   ```bash
   git merge origin/<the branch you want to merge>
   ```


