---
title: Golang基础语法之六
date: 2019-09-30 10:58:32
tags: 
- Golang
- Golang Days
categories:
- Golang
---

## type关键字

定义类型

```go
// 定义新的类型
type myint int
type mystr string

// 定义函数类型
type myfun func(int, int)(string)

func fun1()myfun{

}

// 类型别名
type bieming = Type

// 别名不能添加本地方法，除非使用type定义新的类型（不使用等号）
// 别名嵌套注意混淆
```

## 错误处理

### 创建错误

```go
if err != nil {
    log.Fatal(err)
    return
}
```

- 使用errors包的New函数创建错误
- 使用fmt包下的Errorf函数创建错误

### 错误类型

断言，然后获取错误信息

错误不要忽略

### 自定义错误

实现`error`接口, 实现方式如文档五所示

### panic和recover

panic恐慌

恐慌后的代码不执行，已经defer的代码会执行

```go
func funcA() {
    fmt.Println("a")
}
func funcB() {

}

```

recover

捕获panic

```go
defer func() {
    if msg := recover; msg!=nil {
        fmt.Println("恢复主函数")
    }
}()
```

适合panic场景：

- 空指针引用
- 下标越界
- 除数为0
- 不应该出现的分支，比如default
- 输入不应该引起函数错误
