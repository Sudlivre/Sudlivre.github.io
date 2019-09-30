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

## 面向对象

面向对象：OOP

Golang的结构体嵌套：

- 模拟继承性：is - a 匿名字段：Person
- 模拟聚合关系 has - a 例如字段：p Person

```go
type Person struct {
    name string
    age int
}

type Student struct {
    Person // 结构体作为匿名字段 Person字段可作为提升字段，可以直接获取属性和方法
    school string
}
```

## 方法

一个方法就是一个包含了接受者的函数，接受者可以是命名类型或者结构体类型的一个值或者是一个指针。
所有给定类型的方法属于该类型的方法集。

语法同函数类似，区别需要有接受者。

### 方法定义

```go
type Work struct {
    name string
    age int
    sex string
}

// 定义方法
func (w Worker) work () {
    fmt.Println(w.name, "is working")
}

func (p *Worker) rest() {
    fmt.Println(p.name, "is sleeping")
}

w1 := Worker{"xs", 24, "girl"}
w1.work()
```

继承性和方法重写

## 接口

接口是一组方法的签名
接口和类型的实现关系，是非侵入式

- 当需要接口类型的对象时，可以使用任意实现类对象代替
- 接口对象不能访问实现类中的属性

```go
// define interface
type USB interface {
    start()
    end()
}

// define struct
type Mouse struct {
    name string
}

type FlashDisk struct {
    name string
}

// define method
func (m Mouse)start() {
    fmt.Println("sss")
}
func (m Mouse)end() {
    ftm.Println("qqq")
}

func (f FlashDisk)start() {
    fmt.Println("sss")
}
func (f FlashDisk)end() {
    ftm.Println("qqq")
}
// test
func testInterface(usb USB) {
    usb.start()
    usb.end()
}
```

多态：一个事物的多种形态，Golang通过接口模拟多态

就一个接口而言

- 看成实现本身的类型，能够访问是想类中的属性和方法
- 看成是对应接口的类型，那就只能访问接口中方法

接口的用法：

- 一个函数如果接受接口类型作为参数，那么实际上可以传入该接口的任意实现类型对象作为参数
- 定义一个类型为接口类型，实际上可以赋值为任意实现类的对象

鸭子类型：

### 空接口

```go
type A interface {

}
// fmt包下面的Print系列函数就是空接口实现的
```

结合slice和map存储不同类型的数据

### 接口嵌套

```go
type A interface {
    test1()
}
type B interface {
    test2()
}
type C interface { // 如果要实现接口C，那么接口A和接口B的方法都要实现
    A
    B
    test3()
}
```

### 接口断言

```go
type Shape interface {
    peri() float64
    area float64
}
type Triangle struct {
    a,b,c float64
}
func (t Triangle) peri() float64 {
    return t.a + t.b + t.c
}
func (t Triangle) area ()float64 {
    p = t.peri() / 2
    s := math.Sqrt(p*(p-t.a)*(p-t.b)*(p-t.c))
}
func getType(s Shape) {
    // 断言  判断s的实际类型
    if ins, ok := s.(Triangle); ok {
        fmt.Println("is triangle")
    }
}
func getType2 (s Shape) {
    switch ins := s.(type) {
        case Triangle:
        fmt.Println("is Triangle")
    }
}
```
