---
title: "[My project] 취향의 나눔"
date: 2020-06-17 01:12:30 +0800
categories: [My project, 취향의 나눔]
tags: [ssafy, 취향의 나눔, project]  
---



# 취향의 나눔

> 2020.06.11~2020.06.17
>
> 

UCC 영상 https://youtu.be/MtCmQCIbkI8

## 프로젝트 배경

![배경](https://user-images.githubusercontent.com/60081199/85346341-14307880-b530-11ea-8706-4cea7b9c46bd.jpg)

- 영화를 본 후 영화에 대한 감상을 나누고 싶어 하는 사람들의 니즈 발견
- 영화 정보 전달 위주의 기존 영화 사이트
- 영화 감상 공유에 초점을 둔 영화 사이트를 만들어보자!

## 프로젝트 목표 및 기능

![목표](https://user-images.githubusercontent.com/60081199/85346339-14307880-b530-11ea-884d-330066fe6421.jpg)

- 웹 사이트 명: **취향의 나눔**
- 대상 : 영화에 대한 감상을 자유롭게 공유하고 싶은 사람 누구나
- 슬로건 : 당신과 닮은 취향을 가진 사람과 영화와 세계를 보는 시선을 공유해보세요.
- 목표
  - 영화 정보 조회
    - TheMovieDataBase API, Youtube API를 활용
    - 포스터, 제목, 평점, overview, 예고편 등
  - 영화를 통해 자신의 취향과 개성을 표출
    - 회원이 작성한 리뷰 해당 영화의 평점을 기준으로 장르와 언어 추천
    - 유저 개개인에게 추천 영화 서비스 제공
    - 작성한 리뷰, 좋아하는 영화가 차곡차곡 쌓이는 개인 페이지
    - 팔로우 기능
  - 영화 감상 공유
    - 사용자가 감상 공유를 원하는 영화에 대해 방을 만들면 입장하여 그 영화에 대해 이야기를 나눌 수 있는 서비스 제공 (영화 리뷰 CRUD)
    - 최근 본 영화에 대한 다른 사람들의 리뷰를 한 눈에 볼 수 있도록 UI를 구성하여 회원간 자유로운 교류 유도
  - 회원 프로필 기능
    - 회원별 프로필 커스텀 기능 (프로필 이미지, 자기소개, 회원별 작성한 리뷰 목록, 팔로워 수, 팔로우 기능)
  - 회원 관리 기능
    - 로그인
    - 회원가입
    - 로그아웃

## 프로젝트 일정

![일정](https://user-images.githubusercontent.com/60081199/85346342-14c90f00-b530-11ea-9f6c-eed1ecdb88c2.jpg)



## 개발환경

1) Python Web Framework

- Django 2.1.15
- Python 3.7 +

2) 개발 아기텍쳐

- Django & Vanila JS

## 사용 API

1) The Movie Database(TMDb) API

2) Youtube Data API



## 페이지별 기능 및 UX 구상

![페이지](https://user-images.githubusercontent.com/60081282/85231562-17920a00-b433-11ea-9a23-a0d133090649.PNG)

## 데이터베이스 모델링(ERD)

![erd](https://user-images.githubusercontent.com/60081199/85346314-0da20100-b530-11ea-9066-48719fc8c3fa.jpg)

## 영화 추천 알고리즘

> 가장 선호하는 장르, 언어의 영화를 추천해주었다.

1. 가장 좋아하는 장르 찾기

   - 유저가 작성한 리뷰에 대해 해당 영화가 속한 장르에 따라 평점의 평균 값을 구해준다

     [![추천1](https://user-images.githubusercontent.com/60081199/85346343-1561a580-b530-11ea-906d-b75be96c5b5d.jpg)](https://user-images.githubusercontent.com/60081199/85346343-1561a580-b530-11ea-906d-b75be96c5b5d.jpg)

   - 즉, 장르별 평점의 평균(총 평점/리뷰 횟수)을 구해준 후 가장 높은 평균 점수를 가진 장르를 찾는다.

     [![추천2](https://user-images.githubusercontent.com/60081199/85346344-15fa3c00-b530-11ea-8758-999a7f46b823.jpg)](https://user-images.githubusercontent.com/60081199/85346344-15fa3c00-b530-11ea-8758-999a7f46b823.jpg)

2. 가장 좋아하는 언어 찾기

   - 유저가 리뷰를 작성한 영화 중 가장 많은 언어를 찾는다.

     [![추천3](https://user-images.githubusercontent.com/60081199/85346345-1692d280-b530-11ea-9406-78075a333f1d.jpg)](https://user-images.githubusercontent.com/60081199/85346345-1692d280-b530-11ea-9406-78075a333f1d.jpg)

3. 선호하는 장르와 언어의 영화를 인기도 순으로 내림차순 한 후, 이미 본 영화를 제외하여 5개의 영화를 선택한다.

   [![추천4](https://user-images.githubusercontent.com/60081199/85346349-1692d280-b530-11ea-8012-52d9ba1b065c.jpg)](https://user-images.githubusercontent.com/60081199/85346349-1692d280-b530-11ea-8012-52d9ba1b065c.jpg)

## 핵심기능

1. 첫 페이지

   ![템플릿2](https://user-images.githubusercontent.com/60081199/85346352-17c3ff80-b530-11ea-8b55-f3d251028d86.jpg)

   - 사이트에 대한 컨셉
   - 로그인/회원가입

2. 홈 페이지

   ![영화추천1](https://user-images.githubusercontent.com/60081282/85231758-dac71280-b434-11ea-8416-6fa1212b92d5.PNG)

   - 로그인한 사용자에게 영화 추천

   ![영화추천2](https://user-images.githubusercontent.com/60081282/85231760-dc90d600-b434-11ea-8c2d-dbe9491a6218.PNG)

   - 유저가 최근 작성한 리뷰에 대한 다른 사용자들의 리뷰를 한 눈에 볼 수 있게 구성

3. 개인 페이지

   ![프로필](https://user-images.githubusercontent.com/60081282/85231790-1235bf00-b435-11ea-9f80-e8b36b22256b.PNG)

   - 프로필 이미지 등록 및 변경
   - 팔로우 기능
   - 해당 유저가 작성한 리뷰 및 영화 조회

4. 영화 목록 페이지

   ![movielist](https://user-images.githubusercontent.com/60081282/85231761-df8bc680-b434-11ea-87bc-3999dee55200.PNG)

   - 평점순, 최신순으로 영화 분류 및 정렬
   - 검색 기능 추가하고 싶었으나 시간 관계상 하지 못함

5. 영화 디테일 페이지

   ![moviedetail](https://user-images.githubusercontent.com/60081282/85231767-e1558a00-b434-11ea-86cb-b78584920ae5.PNG)

   - 예고편
   - 영화에 대한 상세 정보(평점, 개봉일, 누적 관객 등)

6. 리뷰 목록 페이지

   ![reviewlist](https://user-images.githubusercontent.com/60081282/85231768-e31f4d80-b434-11ea-9a0e-78847a0409ac.PNG)

   - 감상 공유를 원하는 영화에 대한 리뷰 방을 만들 수 있다.

7. 리뷰 디테일 페이지

   ![기능6](https://user-images.githubusercontent.com/60081199/85346330-11ce1e80-b530-11ea-8c07-2e5d2885cfed.jpg)

   - 한 영화에 대한 유저들의 감상 조회 및 작성, 수정, 삭제 가능

     ![reviewdetail](https://user-images.githubusercontent.com/60081282/85231769-e4507a80-b434-11ea-80bc-7035427c0a28.PNG)

     ![reviewdetail2](https://user-images.githubusercontent.com/60081282/85231772-e61a3e00-b434-11ea-9b60-ab12d8bc4661.PNG)

   - 해당 리뷰에 대해 댓글 조회 및 작성, 수정, 삭제 가능