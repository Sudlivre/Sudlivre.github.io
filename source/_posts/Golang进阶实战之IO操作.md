---
title: Golang进阶实战之IO操作
date: 2019-10-03 15:33:33
tags: 
- Golang
- Golang Days
categories:
- Golang
---

## 文件读写

```go
func main() {
    // file文件操作
    fileInfo, err := os.Stat("aaa.txt")
    if err != nil {
        fmt.Println("error")
        return
    }
    fmt.Println(fileInfo)
    fmt.Println(fileInfo.Name())
    fmt.Println(fileInfo.Size())
    fmt.Println(fileInfo.IsDir())
    // 文件权限
    fmt.Println(fileInfo.Mode())
    fmt.Println(fileInfo.ModTime())

    // 路径
    fileName1 := "aaa.txt"
    fmt.Println(filepath.Abs(fileName1))
    fmt.Println(filepath.IsAbs(fileName1))

    // 创建目录
    err = os.MkdirAll("aa", os.ModePerm)
    if err != nil {
        fmt.Println("error")
        return
    }
    // 创建Create 打开Open OpenFile 关闭Close 删除Remove RemoveAll
    file, err2 := os.Create("fileName2.txt")
    if err2 != nil {
        fmt.Println("error")
        return
    }
    fmt.Println(file)
}
```

## 数据读写

```go
func main() {
    // io
    // 读取数据: Read
    file, err := os.Open("aaa.txt")
    if err != nil {
        return
    }
    defer file.Close()

    bs := make([]byte, 4, 4)
    //n, err := file.Read(bs)
    //println(err)
    //println(n)
    //println(string(bs))
    //
    //n, err = file.Read(bs)
    //println(err)
    //println(n)
    //println(string(bs))
    //
    //n, err = file.Read(bs)
    //println(err)
    //println(n)
    //println(string(bs))

    n := -1
    for {
        n, err = file.Read(bs)
        if n == 0 || err == io.EOF {
            break
        }
        fmt.Println(string(bs[:n]))
    }

    // 写入数据: Write
    file2, err2 := os.OpenFile("bbb.txt", os.O_CREATE|os.O_WRONLY|os.O_APPEND, os.ModePerm)
    if err2 != nil {
        return
    }
    defer file2.Close()
    bs2 := []byte{44,55,66}
    n2, err4 := file2.Write(bs2)
    if err4 != nil {
        return
    }
    fmt.Println(n2)
}

```

## io相关

```go
func main() {
    // copy
    // 可以用Read和Write利用切片实现复制文件
    // io.Copy()
    // ioutil.ReadFile() ioutil.WriteFile()

    // Seek接口设置读写文件偏移量

    // 断点续传 ；利用临时文件记录传输了多少数据

    // bufio 添加缓冲区 提高io效率
    // buifo.NewReader(file)
    // Flush() 刷新缓冲区

}
```
