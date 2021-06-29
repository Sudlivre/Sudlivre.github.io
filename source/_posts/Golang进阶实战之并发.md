---
title: Golang进阶实战之并发
date: 2019-10-03 16:03:27
tags: 
- Golang
- Golang Days
categories:
- Golang
---

## go

```go
func main() {
    // goroutine
    // 关键字go 主goroutine，子goroutine结束
    go printNum()
    for i := 1; i < 100; i++ {
        fmt.Println("main:", i)
    }
}

func printNum() {
    for i := 1; i < 100; i++ {
        fmt.Println("child: ", i)
    }
}
```

## 并发模型

GPM

## runtime包

## 临界资源安全

`var wg sync.WaitGroup` // 创建同步等待组对象

- Add
- Wait
- Done

## 互斥锁

`var mutex sync.Mutex` // 创建锁

- Lock
- UnLock

## 读写锁

- 读操作可以同时进行
- 写操作不可以同时进行，啥也不能干，不能读也不能写

## channel通道

实现goroutine之间通信

### 非缓冲通道

```go
ch1 := make(chan int)
ch1 <- 2 // 写
data := <- ch1 // 读
// 读写都是阻塞的，读写时对应的。不然会死锁
```

`close(ch1)` // 关闭通道

可以使用`for ... range ch1`访问通道

### 缓冲通道

- 发送：缓冲区数据满了，才会阻塞
- 接收：缓冲区数据空了，才会阻塞

`ch2 := make(chan int, 5)`

读取类似队列

### 单向通道

```go
ch2 := make(chan <- int) // 只能写
ch2 := make(<- chan int) // 只能读
// 一般用在函数中限制只读，只写
```
