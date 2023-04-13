---
date: 2023-04-14T01:21:08+08:00
description: '跟著影片學習Go，學到哪記錄到哪'
# featured_image: "/images/Pope-Edouard-de-Beaumont-1844.jpg"
featured_image: '/images/code.jpeg'
# images: ['/images/Golang.png']
tags: ['Golang']
categories: 'Golang'
title: '學習Go'
---

跟著影片學習 Go，學習的影片是在 YT 很紅的 Nana 的影片，以下附上連結。
[Golang Tutorial for Beginners | Full Go Course](https://youtu.be/yyUHQIec83I)

## Go Module

一開始必須要在專案的資料夾裡面輸入

```golang
go mod init
```

這樣子就會新增一個 go.mod 會紀錄著有使用到的依賴模組和 Golang 的版本。

## packge, import and func main

go 程式會有的主要結構，看以下範例

```golang
package main

import "fmt"

func main() {
  fmt.Println("Hello Golang");
}

```

go 會有一個 main package 裡面裝了已經寫好讓我們可以使用 go 的程式,

import 主要的功用在匯入別人已經寫好的函式庫（包括 Golang 原本提供的方法）

func main 是主要每個 Golang 程式開始執行的地方。

## Variables

Golang 是一門靜態語言，要求必須要知道變數的類別，方法有兩種，第一種是在建立變數的時候直接標示型別

```golang
var myName string
var myAge uint

myName = "ZZ"
myAge = "25"
```

或者直接在宣告變數的時候賦予值，這時候 Golang 擁有型別推斷的機制(Type Inference)，會自動根據你賦予的值來判斷變數類別。

```golang
var myAge = 25
fmt.Printf("myAge type is %t", myAge) // int
```
