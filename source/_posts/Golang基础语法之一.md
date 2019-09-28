---
title: Golang基础语法之一
date: 2019-09-28 08:26:25
tags: 
- Golang
- Golang Days
categories:
- Golang
---

## Start golang

### Hello World

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello World")
    // Print 不换行
    fmt.Print("Go Go Go!!!")
}
```

### Run

```shell
go run

go build

go install
```

### go help

```shell
go help

The commands are:

        bug         start a bug report
        build       compile packages and dependencies
        clean       remove object files and cached files
        doc         show documentation for package or symbol
        env         print Go environment information
        fix         update packages to use new APIs
        fmt         gofmt (reformat) package sources
        generate    generate Go files by processing source
        get         add dependencies to current module and install them
        install     compile and install packages and dependencies
        list        list packages or modules
        mod         module maintenance
        run         compile and run Go program
        test        test packages
        tool        run specified go tool
        version     print Go version
        vet         report likely mistakes in packages
```

## 变量

- 静态语言：强类型语言
- 动态语言：弱类型语言

go语言特性

```go
var num int
num = 3
var num2 = 4
// 类型推断
var name = "string"
// 简短定义
num := 100
```

> - 变量必须先定义才能使用。
> - 变量的类型和赋值必须一致。
> - 同一个作用域内，变量名不能冲突。
> - 简短定义方式，左边的变量名至少有一个是新的。
> - 简短定义的方式，不能定义全局变量。
> - 变量的零值。也叫默认值。
> - 变量定义了就要使用否则无法通过编译。

## 常量

```go
// 显式类型定义
const b string = “abc”
// 隐式类型定义
const b = “abc”

const (
    a int = 100
    b
    c string = "go"
    d
    e
)
```

> 一组常量中，如果某个常量没有初始值，默认和上一行一致

### iota

```go
const (
    a = iota // 0
    b = iota // 1
    c = iota // 2
)
```

## 数据类型

基本数据类型：

- 布尔类型
- 数值类型
- 字符串

符合数据类型：

- array
- slice
- map
- function
- pointer
- struct
- interface
- channel
  
## 运算符

- 算术运算符
- 关系运算符
- 逻辑运算符  --  / && / || / ! /
- 位运算符 / 按位& / 按位| / 异或^ / 位清空&^ / 左移运算<< / 右移运算 >> /  
- 赋值运算符
