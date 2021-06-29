---
title: Golang基础语法之三
date: 2019-09-29 09:28:06
tags: 
- Golang
- Golang Days
categories:
- Golang
---

## 随机数

伪随机数

```go
package main

import "math/rand"
import "time"

func main() {
    num1 = rand.Int()
    num2 = rand.Intn(10)
    rand.Seed(1) // 设置种子数
    num3 = rand.Intn(10)

    // 时间戳
    timeStamp1 = time.Now().Unix()
    timeStamp2 = time.Now().UnixNano()

    rand.Seed(timeStamp2) // 根据时间戳设置随机种子

    // 生成区间随机数
    num4 = rand.Intn(5) + 5
}
```

## Array

### 数组定义

```go
var variable_name [SIZE] variable_type

var balance1 [10] float 32
var balance2 = [5] floart32{100.0, 2.0, 3.14, 7.0, 99.9}
d := [...] int{1,2,3}
e := [5] int{4: 100} // [0,0,0,0,100]

arrayLen := len(balance1) // 容器中已存储的数据量
arrayCap := cap(balance1) // 容器中能够存储的最大的数量

fmt.Printf("%p\n", &balance1) // 获取数组的地址
```

### 遍历数组

```go
a := [...]float64{5.5, 6.6}
for i, v := range a {
    fmt.Println(i, v)
}
```

>数组是值类型 理解为存储的数值本身

### 多维数组

```go
a2 := [3][4]int{{1,2,3,4}, {5,6,7,8}, {9,10,11,12}}
```

## Slice

### 切片定义

```go
var identifier []type

var slice1 []type = make([]type, len)
// 简写
slice2 := make([]type, len)

slice2 = append(slice2, 3, 4)
slice2 = append(slice2, slice1...) // 加上...代表添加里面的元素
```

>可以从数组初始化切片，切片是引用类型，改变数组内容，切片内容会一起改变。
>如果切片容量不够，会重新拷贝一份数组，这是数组改变不会影响切片内容。

## 深拷贝和浅拷贝

- 值语义 拷贝值 深拷贝
- 引用语义 拷贝地址 浅拷贝

## Map

Map通过hash表实现

使用`make()`函数创建，方法类似Slice。不初始化会创建一个nil map。nil map不能用来存放键值对

```go
var map1 map[key_type]value_type // 声明
var map2 = make(map[key_type]value_type) // 声明并初始化

map2[40] // key不存在获取默认值
value, ok := map[key] // 判断key是否存在

map[3] = 40 // key存在修改，不存在添加

delete(map2, 4) // 删除键值对，不存在不影响

len(map2) // 获取map长度
```

>map是引用类型的数据类型

## string

语法："", ``

```go
s1 := "hello中国"

len(s1) // 11 获取的是字节个数
```

## strings包

使用string的方法需要导包`import "strings"`

## strconv包

实现字符串和基本数据类型进行转换
