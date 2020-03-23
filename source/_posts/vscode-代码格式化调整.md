---
title: vscode 代码格式化调整
date: 2020-03-23 21:45:38
tags:
- Settings
- Vscode
categories:
---

经过了很长时间对.clang.format进行调整的尝试后，发现了自己的失败，然后发现了一种更简单的方法。

# VSCode Preference更改

选项：C_Cpp: Clang_format_fallback Style

更改为{BasedOnStyle: Google, IndentWidth: 4}

![](https://raw.githubusercontent.com/golfrey/picbed/master/img/20200323215144.png)

