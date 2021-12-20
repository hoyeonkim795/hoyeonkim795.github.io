---
title: "[Framework] EchoFramework를 사용해서 웹 브라우저에 Hello World 띄우기"
date: 2021-04-13 13:21:40 +0800
categories: [Framework, Echo]
tags: [echoframework, 고랭, 고, 에코프레임워크]
---

# Echoframework

웹 브라우저 상에 Echoframework를 활용하여 "Hello World" 띄운다.

[소스코드링크](https://github.com/hoyeonkim795/golang_lesson/tree/master/lesson21/myapp)

## Installation 

```bash
$ mkdir myapp && cd myapp
$ go mod init myapp
$ go get github.com/labstack/echo/v4
```

## Server.go

```go
package main

import (
	"net/http"

	"github.com/labstack/echo/v4"
)

func main() {
	e := echo.New()
	e.GET("/", func(c echo.Context) error {
		return c.String(http.StatusOK, "Hello, World!")
	})
	e.Logger.Fatal(e.Start(":1323"))
}
```

- `New()` : echo instance 생성
- `GET` : 새로운 `GET` 루트를 등록하고 path를 라우터에 매칭시킨다. 위 코드에서는 "/" 가 path

- `Context`: 컨텍스튼느 현재 `HTTP` 요청의 컨텍스트를 나타낸다. 요청을 보유하고 응답 객체, 경로, 경로 매개 변수, 데이터 및 핸들러 등을 hold한다.

  ```go
  	context struct {
  		request  *http.Request
  		response *Response
  		path     string
  		pnames   []string
  		pvalues  []string
  		query    url.Values
  		handler  HandlerFunc
  		store    Map
  		echo     *Echo
  		logger   Logger
  		lock     sync.RWMutex
  	}
  ```

- `Logger` : 로그 인터페이스
- `Start` : HTTP 서버 시작