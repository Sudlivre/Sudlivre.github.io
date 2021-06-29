---
title: Golang基础语法之二
date: 2019-09-28 16:41:18
tags: 
- Golang
- Golang Days
categories:
- Golang
---

## 输入和输出

输出：

```go
/*
Print() // 打印
Printf() // 格式化打印
Println() // 打印之后换行
*/
```

输入：

```go
/*
fmt.Scanln(&x, &y) 阻塞式

fmt.Scanf("%d, %f", &x, &y)

reader := bufio.NewReader(os.Stdin)
s, _ := reader.ReadString('\n')
*/
```

## if语句

```go
if 布尔表达式1 {
    执行语句
} else if 布尔表达式2 {
    执行语句
} else {
    执行语句
}
```

if语句其他写法

```go
if num := 4; num > 0 {
    fmt.Println(num)
}
// 作用域在if语句里面
// fmt.Println(num) // undefined: num
```

## switch分支语句

```go
switch var1 {
    case val1:
        ...
    case val2:
        ...
    default:
        ...
}
```

switch其他写法

```go
switch { // 直接作用在true上
    case true:
        fmt.Println("true")
    case false:
        fmt.Println("false")
}

switch var1 {
    case val1, val2, val3:
        fmt.Println("true")
    case val4:
        fmt.Println("false")
}

switch var1 := "go"; var1 { // 作用域在switch中
    case val1, val2, val3:
        fmt.Println("true")
    case val4:
        fmt.Println("false")
}
```

>fallthrough: 用于穿透switch，会执行该case后面case的内容，fallthrough在case最后一行

## for循环

```go
for init; condition; post {

}
```

for语句的其他写法

```go
for condition {} // 相当与while循环

for {}

for key, value := range oldMap {
    newMap[key] = value
}
```

- break 跳出循环体
- continue 跳出一次循环

## goto

```go
goto label
..
..
label:
```
