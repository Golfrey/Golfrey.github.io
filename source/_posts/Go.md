---
title: Spring Boot 的mistakes
date: 2019-12-29 21:49:54
tags: 
- Go
categories: Learning
---

# Go语言学习

不知道多少次打开A tour of Go了，为了以后能够尽量少打开这个网站，我决定儒雅随和的写一篇博客。

## Go语言基础

### The Go Playground

In the playground the time begins at 2009-11-10 23:00:00 UTC.

在网站上，运行time.Now()得到的结果永远是上面的结果，这是为什么呢？这是一个小趣闻，这是Go Lang的生日。

### Packeages, variables, and functions

#### Packages

```go
import (
	"fmt"
	"math/rand"
)
```

包的名字是输入路径的最后一个元素，例如"math/rand"包的声明是rand，在使用中我们可以这样使用`rand.Seed(3)`和`rand.Intn(10)`。

#### Imports

```go
import "fmt"
import "math"
```

和

```go
import (
	"fmt"
	"math"	
)
```

是等价的。

#### Exported names

如果一个变量用大写字母开头，那么这个变量是一个exported name。例如Pi。

Pi是math package中的常量，可以用math.Pi来表示。

#### Functions

```go
func add(x int, y int) int {
	return x + y
}
```

#### Functions continued

`(x int, y int)`和`(x, y int)`是等价的。

#### Multiple results

```go
package main

import "fmt"

func swap(x, y string) (string, string) {
	return y, x
}

func main() {
	a, b := swap("hello", "world")
	fmt.Println(a, b)
}
```

#### Named return values

```go
package main

import "fmt"

func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}

func main() {
	fmt.Println(split(17))
}
```

Go的return如果是空的，但是有返回值，那么返回的是定义的同名的变量。

！这应只在短函数中使用，在长函数中使用会破坏可读性。

#### Variables

var定义variables，例如`var c, python, java bool`，是持久的。

#### Variables with initializers

`var i, j int = 1, 2`

#### Short variable declarations

在函数里，：=可以作为var + implicit type的替代品。

`k := 3`

#### Basic types

```go
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32
     // represents a Unicode code point

float32 float64

complex64 complex128
```

#### Zero values

- `0` for numeric types,
- `false` for the boolean type, and
- `""` (the empty string) for strings.

#### Type conversions

T(v) 转化 v 为 T 类型。

Go 只支持显示转化。

#### Constants

用const定义。

```go
const Pi = 3.14
```

