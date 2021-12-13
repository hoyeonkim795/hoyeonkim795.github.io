---
title: "[Web] Spring Boot 강의 정리 1"
date: 2021-12-13 13:21:40 +0800
categories: [Web]
tags: [springBoot, annotation]
---

# Spring Boot

## Annotation

1. 의미

   - 사전적 의미는 주석이다.

   - 자바에서 사용될 때의 어노테이션은 코드 사이에 주석처럼 쓰여서 특별한 의미, 기능을 수행하도록 하는 기술.

2. 용도

   - 컴파일러에게 코드 작성 문법 에러를 체크하도록 정보 제공
   - 빌드 및 배치시 코드를 자동으로 생성할 수 있도록 정보 제공
   - 런타임 시 특정 기능을 실행하도록 정보 제공

3. 사용 순서

   - 어노테이션 정의

   - 클래스에 어노테이션 배치

   - 코드가 실행되는 중에 Reflection 을 이용하여 추가 정보를 획득하여 기능 실시

     

## @RestController

@Controller 어노테이션과 @ResponseBody 어노테이션을 합쳐놓은 어노테이션이다. 클래스 상단에 @RestController 어노테이션을 선언하면 Method마다 @ResponseBody를 붙여주지 않아도 된다.



## @GetMapping

@RequestMapping(Method=RequestMethod.GET)



## Lombok

- 자바 라이브러리로 코드 에디터나 빌드툴에 추가하여 코드를 효율적으로 작성할 수 있도록 도와줌.

- getter, setter, equals와 같은 method를 따로 작성해야 하는 번거로움을 덜어준다.

@Getter @Setter



# Endpoint

API란 두 시스템, 어플리케이션이 상호작용(소통) 할 수 있게 하는 프로토콜의 총 집합이라면 ENDPOINT란 API가 서버에서 리소스에 접근할 수 있도록 가능하게 하는 URL이다