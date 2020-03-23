---
title: MIT 6.824中Go的学习
date: 2020-02-18 15:39:26
tags:
- Go
- Distributed System
categories: Learnings
---

# defer关键词

defer和go一样都是Go语言提供的关键字。defer用于资源的释放，会在函数返回之前进行调用。一般采用如下模式：

```go
f,err := os.Open(filename)
if err != nil {
    panic(err)
}
defer f.Close()
```

如果有多个defer表达式，调用顺序类似于栈，越后面的defer表达式越先被调用。

## defer关键词的陷阱

例1：

```go
func f() (result int) {
    defer func() {
        result++
    }()
    return 0
}
```

例2：

```go
func f() (r int) {
     t := 5
     defer func() {
       t = t + 5
     }()
     return t
}
```

例3：

```go
func f() (r int) {
    defer func(r int) {
          r = r + 5
    }(r)
    return 1
}
```

例1的正确答案不是0，例2的正确答案不是10，如果例3的正确答案不是6。

**return xxx这一条语句并不是一条原子指令!**

函数返回的过程是这样的：先给返回值赋值，然后调用defer表达式，最后才是返回到调用函数中。

# buildmode=plugin

Go插件是使用-buildmode = plugin 标记编译的一个包，用于生成一个共享对象（.so）库文件。 Go包中的导出的函数和变量被公开为ELF符号，可以使用plugin包在运行时查找并绑定ELF符号。

编写plugin插件要点

1. 包名称必须是main
2. 没有main函数
3. 必须有可以导出(访问)的变量或者方法

编写完成之后使用编译plugin。





