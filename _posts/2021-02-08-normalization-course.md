---
title: "[Database] 정규화(Normalization) 과정 (1NF, 2NF, 3NF, BCNF)"
date: 2021-02-08 21:30:00 +0800
categories: [Computer Science, Database]
tags: [normalization, 정규화, 정규화 과정, 1NF, 2NF, 3NF, BCNF]
---

# 정규화 과정

정규화가 무엇인지에 대해 알고싶다면 [정규화](https://hoyeonkim795.github.io/posts/normalization/) 를 참고하자.

## **제1 정규화 (1NF)**

애트리뷰트의 도메인이 오직 **원자값**만을 포함하고, 튜플의 모든 애트리뷰트가 도메인에 속하는 하나의 값을 가져야 한다. 즉, 복합 애트리뷰트, 다중값 애트리뷰트, 중첩 릴레이션 등 비 원자적인 애트리뷰트들을 허용하지 않는 릴레이션 형태를 말한다.

1. 어떤 Relation에 속한 모든 Domain이 원자값(atomic value)만으로 되어 있다.
2. 모든 attribute에 반복되는 그룹(repeating group)이 나타나지 않는다.
3. 기본 키를 사용하여 관련 데이터의 각 집합을 고유하게 식별할 수 있어야 한다.

**예시**

Telephone Number에 2가지가 들어가 있기 때문에 제1 정규형을 만족할 수 없게 된다.

- 관계형 데이터 베이스의 경우 기본적으로 도메인은 모두 원자값이기 때문에 제1 정규형은 지켜져 있다.

![Untitled.png](\assets\img\normalizationCourse\Untitled.png)

Telephone Number에 여러개를 갖기에 1번 원자성 조건 위반 사례

![Untitled 1.png](\assets\img\normalizationCourse\Untitled 1.png)

그룹이 반복되는 경우이기에 2번 조건 위반 사례

![Untitled 2.png](\assets\img\normalizationCourse\Untitled 2.png)

ID가 더이상 고유하게 식별할 수 있는 키가 아니기에 3번 조건 위반 사례

최종! 제 1 정규화 만족

![Untitled 3.png](\assets\img\normalizationCourse\Untitled 3.png)

위의 디자인은 Customer Name과 Customer Telephone Number가 One-to-Many의 관계를 형성하는 것을 알 수 있다.

- 결과적으로 1차 정규화를 함으로써 데이터 redundancy는 더 증가하였다. → 데이터의 논리적 구성을 위해 이 부분을 희생하는 것으로 볼 수 있다.

## **제2 정규화 (2NF)**

모든 비주요 애트리뷰트들이 주요 애트리뷰트에 대해서 완전 함수적 종속이면 제 2 정규형을 만족한다고 볼 수 있다. 완전 함수적 종속이란 X -> Y 라고 가정했을 때, X 의 어떠한 애트리뷰트라도 제거하면 더 이상 함수적 종속성이 성립하지 않는 경우를 말한다. 즉, 키가 아닌 열들이 각각 후보키에 대해 결정되는 릴레이션 형태를 말한다.

즉, 제 2정규화는 테이블의 모든 컬럼이 **완전 함수적 종속**을 만족한다.

→ 부분 함수적 종속을 모두 제거

![Untitled 4.png](\assets\img\normalizationCourse\Untitled 4.png)

부분 함수 종속을 제거해보자!

![Untitled 5.png](\assets\img\normalizationCourse\Untitled 5.png)

 **제 2 정규화를 만족한 테이블**

![Untitled 6.png](\assets\img\normalizationCourse\Untitled 6.png)

**예시 2**

![Untitled 7.png](\assets\img\normalizationCourse\Untitled 7.png)

학번, 과목코드 → 성적

학번, 과목코드 → 학부

학번, 과목코드 → 등록금

학번 → 학부

학번→ 등록금

두 개의 부분 함수 종속성을 가진다.

이를 제거하여 제2 정규화를 시킬 수 있다.

![Untitled 8.png](\assets\img\normalizationCourse\Untitled 8.png)

하지만 조금 더 복잡한 테이블의 경우, 갱신 이상을 겪기도하는데 이를 해결하는 것이 바로 3차 정규화이다.

- 제 2 정규화를 만족하면 이상현상이 없어질까?

    **삽입이상 :** 새로운 학부가 생기는 경우 등록된 학생(학번)이 없다면 학번속성이 NULL이 되므로 삽입할 수 없다.

    **갱신이상 :** 컴퓨터공학부 등록금이 400으로 오르는 경우 20800399, 21500399 둘 모두 바꾸어 주지 않으면 데이터 불일치 문제가 발생한다.

    **삭제이상 :** 21400001 학번을 가진 학생이 자퇴하는 경우, 기계공학부에 대한 정보가 함께 사라진다.

    제2정규형에서도 이상현상이 발생하는 이유는 이행적 함수 종속이 존재하기 때문이다. 이행적 함수 종속을 없애주는 과정이 제 3 정규화이다.

## **제3 정규화**

어떠한 비주요 애트리뷰트도 기본키에 대해서 이행적으로 종속되지 않으면 (기본키 이외의 다른 컬럼이 그외 다른 컬럼을 결정할 수 없는 것) 제 3 정규형을 만족한다고 볼 수 있다. 이행 함수적 종속이란 X - >Y, Y -> Z의 경우에 의해서 추론될 수 있는 X -> Z의 종속관계를 말한다. 즉, 비주요 애트리뷰트가 비주요 애트리뷰트에 의해 종속되는 경우가 없는 릴레이션 형태를 말한다. 

정확하게 다음 두 조건을 만족하면 제 3 정규화라 볼 수 있다.

1. Relation이 제 2정규화 되었다.(The relation is in second normal form)
2. 기본 키(primary key)가 아닌 속성(Attribute)들은 기본 키에만 의존해야 한다.

**예시**

{Tournament, Year} 후보키

Winner Date of Birth은 기본키가 아닌 속성인 Winner를 거쳐 {Tournament, Year}에 의존하고 있다. → 2번 조건을 위반합니다.

![Untitled 9.png](\assets\img\normalizationCourse\Untitled 9.png)

**제3 정규화를 만족하는 테이블**

![Untitled 10.png](\assets\img\normalizationCourse\Untitled 10.png)

이때 후보키를 여러개 가지고 있는 릴레이션에서는 제3정규형을 만족하더라도 이상현상이 생길 수 있다.

⇒ 이를 해결하기 위한 정규형이 보이스-코드 정규형 (BCNF; Boyce-Codd Normal Form)이다. 제3정규형보다 조금 더 엄격한 제약조건을 가지기 때문에 Strong 3NF 라고도 한다.

3NF 를 만족하는 릴레이션 R의 후보키가 1개 밖에 없고, R의 후보키가 기본키가 되고, 3NF를 만족하면 항상 BCNF 를 만족한다. 즉, 3NF 를 만족하는 릴레이션들은 모두 후보키가 1개 밖에 없었기 때문에 3NF 를 만족시키는 정규화를 했지만 BCNF 도 만족한다. 

## **BCNF**(Boyce and Codd Normal Form) **: 결정자 중 후보키가 아닌 것들은 제거**

BCNF란 3차정규형을 만족하면서 **모든 결정자가 후보키 집합에 속한 정규형이**다.

- 3차 정규형을 조금 더 강화한 버전으로 볼 수 있습니다.

    → 3차 정규형으로 해결할 수 없는 이상현상 해결 가능

    ![Untitled 11.png](\assets\img\normalizationCourse\Untitled 11.png)

    BCNF 위반하는 경우

    위 릴레이션은 1NF 는 만족한다는 가정하에,

    - 기본키가 아닌 모든 속성이 기본키에 완전 함수 종속이므로 2NF 를 만족한다.
    - 기본키가 아닌 모든 속성이 기본키에 이행적 함수 종속이 되지 않으므로 3NF 를 만족한다.

    → 하지만 결정자인 C 가 슈퍼키가 아니기에 BCNF 를 위반한다. 

**예시 - 강좌 신청 릴레이션**

- 제약사항 : 한명의 강사는 한 개의 인터넷 강좌만 담당할 수 있다. 참고로 학생은 여러 강좌 선택 가능하다.

![Untitled 12.png](\assets\img\normalizationCourse\Untitled 12.png)

BCNF 위반 테이블

{Student, Course}로 Instructor가 결정되는 것을 알 수 있다.

{Student, Instructor} 로 Course를 결정할 수도 있다.

→ 즉 후보키가 두개가 된다. 하지만 PK는 하나만 되어야하기에 둘 중 하나만 선택하기 ⇒ 원하는것 선택하면 된다! 예시는 {Student, Course} 선택! 

### 3NF 까지 만족하지만 BCNF 를 만족하지 않는 경우 이상 현상 정리

- **삽입이상**

    Algorithms 라는 수업이 Dijkstra 에 의해 열렸다고 하자. 하지만 수강생이 아무도 없는 경우 삽입할 수 없다.

- **갱신이상**
James Gosling 이 담당하는 강의가 바뀌게 될 경우 수강생의 수만큼 갱신해줘야 하므로 하나라도 빠뜨리면 데이터 불일치 문제가 발생할 여지가 있다.
- **삭제이상**
모찌가 자퇴해서 Computer Architecture 수업의 수강생이 없어지면 Alan Turing 이라는 강사도 사라진다.

### BCNF 를 위반하는 릴레이션에 대한 분해

![https://s3.ap-northeast-2.amazonaws.com/yaboong-blog-static-resources/etc/bcnf-violation-resolved.png](https://s3.ap-northeast-2.amazonaws.com/yaboong-blog-static-resources/etc/bcnf-violation-resolved.png)

BCNF를 만족하는 두 개의 릴레이션으로 분해

분해한 두 개의 릴레이션에서 기존 릴레이션에서 결정자역할을 했던 속성을 키로 해준다. 그러면 BCNF 까지 만족시키는 릴레이션 두 개가 생기게 된다.

**제4 정규형 : 다치 종속 제거**

**제5 정규형 : 조인 종속성 제거**