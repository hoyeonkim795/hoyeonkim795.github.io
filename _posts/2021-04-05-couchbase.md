---
title: "[Database] 카우치베이스(Couchbase)"
date: 2021-04-05 18:13:40 +0800
categories: [Computer Science, Database]
tags: [카우치베이스, couchbase, database, NoSQL]
---

# Couchbase

## Overview

**카우치베이스** 는 쉽게 수평 확장이 가능하고 고성능의 매우 유연한 문서 기반의 NoSQL 솔루션 이다.

특징

- 응답시간이 매우 빠르다
- 대량의 동시 사용자 처리가 가능하다.
- 다운타임이 거의 없이 365일 가동할 수 있는 솔루션
- Json 문서 객체를 지원하기에 정보 저장과 변경도 매우 유연하면서 쉽다.
- 성능 확장 시 서버 시스템을 실시간으로 추가하면서 서비스 용량 확장이 가능하기 때문에 유지 보수 측면에서 매우 편리
- 적용예, PayPal, draw something (사용자가 원하는 그림을 그려서 올리는 앱)

- 일반적으로 카우치베이스 서버는 여러 서버로 구성된 **클러스터** 로 구성됨