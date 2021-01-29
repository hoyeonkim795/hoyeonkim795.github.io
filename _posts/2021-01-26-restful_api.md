---
title: "[Network] 정렬 알고리즘"
date: 2021-01-26 09:12:30 +0800
categories: [Computer Science, Web]
tags: [rest api, web, restful api, rest]  
---



# RESTful API

이전 포스트에서 REST API란 무엇인지에 대해 알아보았습니다. 오늘은 REST의 특징 그리고 RESTful API에 대해 알아보겠습니다.😉

# REST의 특징

REST의 특징은 총 6개로

- Uniform Interface
- Stateless
- Caching
- Self-descriptiveness
- Client-Server
- Hierarchical system

가 있다. 

### 1. Uniform Interface

Uniform Interface는 HTTP 표준만 맞는다면, URI로 지정한 리소스에 대한 동작을 통일되게 하고, 어떠한 기술로도 가능한 인터페이스 스타일을 말한다. 예를들어, REST API 정의를 HTTP + JSON으로 정했다면, C, JAVA, PYTHON 의 어떠한 언어든 IOS 플랫폼 등 특정 언어나 기술에 종속 받지 않고 사용이 가능한 구조를 말한다. 

### 2. Stateless

REST는 작업을 위한 상태 정보를 따로 저장하거나 관리하지 않는다. 즉, 세션이나 쿠키 정보를 따로 관리하지 않기 때문에 API 서버는 그저 들어오는 요청만을 단순히 처리하기만 하면 되는 것이다. 따라서 서비스의 자유도가 높아지고 서버에서 불필요한 정보를 관리하지 않아도 된다. 그렇기 때문에, 한편으로는 REST API 실행 중 실패가 발생한 경우, Transaction 복구를 위해 기존의 상태를 저장할 필요가 있다. (POST method 제외)

### 3. Caching

REST는 HTTP라는 기존 웹 표준을 그대로 사용하기 때문에, 웹에서 사용하는 기존의 인프라를 당연히  활용할 수 있다. 따라서 HTTP가 가진 캐싱 기능을 사용할 수 있다. HTTP 프로토콜 표준에서는 Last-Modified 태그나 E-Tag를 이용하면 캐싱 구현이 가능하다.

### 4. Self descriptiveness

Self descriptiveness 는 REST API 메시지만 보아도 이것이 무엇을 의미하는지 쉽게 이해할 수 있다는 표현 구조로 되어있다는 것을 의미한다.

### 5. Client - Server

REST 서버는 API를 제공하고 클라이언트는 사용자 인증, 컨텍스트 (세션, 로그인 정보) 등을 관리하는 구조로 각각의 역할이 확실히 구분되어있다. 따라서, 클라이언트와 서버에서 개발해야 할 내용이 명확하기 때문에 서로에 대한 의존성이 줄어들게 된다. 

### 6. Hierarchical system

REST 서버는 다중 계층으로 구성될 수 있어 로드밸런싱, 보안, 암호화 계층을 추가해서 구조상의 유연성을 둘 수 있고 PROXY, 게이트웨이 같은 네트워크 기반의 중간 매체를 사용할 수 있다. 

# RESTful API

그렇다면 REST API와 다르게 RESTful API 라는 것은 무엇일까? 결국 같은말인데 REST의 특징을 잘 살려서 REST API의 디자인 가이드를 잘 치키며 설계한 즉 RESTful 하게 만든 API라고 할 수 있다. 여기서  RESTful 하게 설계하는 것의 기본적인 규칙은 아래의 두가지이다.

- URI는 **정보의 자원**을 표현해야 한다.
- 자원에 대한 행위는 **HTTP Method (GET, POST, PUT, DELETE 등)** 으로 표현한다.

예를들어, 1번 사용자에게 정보를 받아야할때 아래와 같은 API는 좋지 못한 예시이다.

```json
GET /users/show/1
```

여기서 `show`는 불필요한 표현이다. 정보를 받아야하는 것은 행위 `GET`에 이미 포함되어있다. 따라서 아래의 예시가 옳바른 예시이다.

```json
GET /users/1
```

또 다른 예시를 살펴보자. 만약 사용자를 추가해야할때면 아래의 예시는 좋지 못한 예시이다.

```json
POST /users/insert/2
```

마찬가지로 `POST`에 이미 추가의 행위가 포함되어있으므로 `insert`는 불필요한 표현이다. 아래의 예시가 옳바른 예시이다.

```json
POST /users/2
```

추가적으로 URI 설계시 주의해야할 점을 살펴보자.

1. 슬래시 구분자(/)는 계층 관계를 나타내는데 사용한다.
2. URI 마지막 문자로 슬래시(/)를 포함하지 않는다.
3. 하이픈(-)을 사용하여 URI 가독성을 높이는데 사용하자.
4. URI에 밑줄(_)은 사용하지 않는다.
5. URI 경로에는 소문자를 지향하자.
6. 파일 확장자(ex. png, jpg 등)는 URI에 포함하지 않는다.