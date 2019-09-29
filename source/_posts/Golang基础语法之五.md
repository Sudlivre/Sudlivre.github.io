---
title: Golang基础语法之五
date: 2019-09-29 17:03:35
tags: 
- Golang
- Golang Days
categories:
- Golang
---

## 指针

### 定义指针

```go
a := 10 // 实际变量
var b *int // 声名指针变量
b = &a // 指针变量指向a的内存地址

// 指针的指针
var c **int
c = &b
```

### 数组指针

数组指针：存储数组的地址
`*[4]int`

指针数组：存储的数据类型是指针
`[4]*int`

### 函数指针

函数指针：函数默认是一个指针，没有*

指针函数：函数的返回值是一个指针

## 结构体

### 定义结构体

```go
type Person struct {
    name string
    age int
    sex string
    address string
}

var p1 = Person
p1.name = "xiaosi"
p1.age = 24
p1.sex = "girl"
p1.address = "cq"

p2 := Person{}

p3 := Person{name: "jjj", ...}

p4 := Person{"jj", 24, "girl", "cq"}
```

### 结构体指针

结构体是值类型数据结构， 深拷贝

可以定义结构体指针进行浅拷贝`var pp1 *Person`

### new操作

创建某种类型的指针的函数，`p1 := new(Person)` 返回指针

### 匿名结构体

```go
s3 := struct {
    name string
    age int
}{
    name "xs"
    age 24
}
```

### 匿名字段

不写字段名，默认类型作为字段，类型不能重复

### 结构体嵌套

一个结构体中的字段，是另一个结构体类型
