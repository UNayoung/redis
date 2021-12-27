FOSS 2021-2 Final Project - 201820768 우나영
=============

# Lecture - Redis
<img src="https://media.vlpt.us/images/limsubin/post/ac3da3f4-ead2-4790-8cd3-eda18726ac6f/redis.png" width="240" height="80">

## 목차

- [주제 선정 동기](#주제-선정-동기)
- [Redis 란](#redis-란)
    + [정의](#정의)
    + [이점](#이점)
    + [주요 사용 사례](#주요-사용-사례)
- [Redis 설치](#redis-설치)
    + [방법 1 Docker를 통해 Redis 설치하기](#방법-1-docker를-통해-redis-설치하기)
    + [방법 2 Redis 릴리즈를 다운로드하여 설치하기](#방법-2-redis-릴리즈를-다운로드하여-설치하기)
- [Redis-cli 명령어](#redis-cli-명령어)
- [Redis와 Spring Boot 연동](#redis와-spring-boot-연동)
    + [POST /redis](#post--redis)
    + [GET /redis](#get--redis)
    + [PUT /redis](#put--redis)
    + [DELETE /redis](#delete--redis)
- [강의를 진행하며 느낀점](#강의를-진행하며-느낀점)
- [References](#references)

## 주제 선정 동기
- 개발 프로젝트를 진행하며 Redis 데이터 저장소에 대해 알게 되었고 Redis에 관한 지식을 쌓고 싶다는 목표가 생겼다. 따라서 Redis란 무엇인지에 대해 알아본 뒤 설치 및 실습을 진행해보고자 해당 주제를 선정하게 되었다.  
- Redis 데이터 저장소에 대해 관심이 생긴 사람들이 해당 강의를 통해 내가 알고 있는 Redis에 관한 지식을 공유받으면 좋을 것 같다. 나 또한 아직 모르는 부분은 다른 사람의 자료를 통해 공유받음으로써 선순환이 이루어지면 좋을 것 같다.

## Redis 란

#### 정의
Redis란 Key-Value 구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반의 비관계형 데이터베이스 관리 시스템이다.

#### 이점

1. 성능

Redis는 데이터를 메모리에 저장하는 인메모리 데이터 저장소로 데이터 액세스 대기 시간을 낮추고 처리량을 높인다.

2. 유연한 데이터 구조

제한적인 데이터 구조를 제공하는 다른 데이터 저장소와 달리 Redis는 다양한 데이터 구조를 지원한다.
    
3. 단순성 및 사용 편의성

Redis의 경우, 쿼리 언어와 반대되는 단순한 명령 구조를 통해 데이터를 저장하고 액세스할 수 있다. 또한, Java, Python, C, JavaScript, Node.js 등의 다수의 언어를 지원한다.

#### 주요 사용 사례

1. 캐싱

데이터베이스 쿼리 결과 캐싱, 영구 세션 캐싱, 웹 페이지 캐싱은 Redis를 사용한 캐싱의 주요 예이다.

2. 채팅, 메시징

Redis는 pub/sub 기능을 지원한다. pub/sub이란 채널을 구독한 모든 subscriber에게 특정 이벤트를 제공하는 것을 의미한다. Redis는 이러한 pub/sub 기능을 통해 채팅 및 메시징을 유연하게 구현할 수 있다.

3. 머신 러닝

Redis는 머신 러닝 모델을 신속하게 구축하고 학습 및 배포할 수 있는 빠른 인 메모리 데이터 저장소를 제공한다.

## Redis 설치

#### 방법 1 Docker를 통해 Redis 설치하기

1. mkdir redis

2. cd redis

3. vi docker-compose.yml

```
version: "2"
services:
  redis:
    container_name: redis
    image: redis:latest
    ports:
      - "6379:6379"
```

4. docker-compose up


#### 방법 2 Redis 릴리즈를 다운로드하여 설치하기

<https://github.com/microsoftarchive/redis/releases>

설치 완료 후, redis-server.exe 파일을 더블 클릭하여 실행한다.

## Redis-cli 명령어

- 모든 key 값 조회
```
keys *
```

- 데이터 저장
```
set key value
```

- 다수 데이터 저장
```
mset key value key value ...
```

- 해당 문자열이 포함된 key 값 조회
```
keys *string*
```

- 만료시간을 지정하여 데이터 저장
```
setex key seconds value
```

- 남은 만료시간 조회
```
ttl key
```

- key에 해당하는 value 값 조회
```
get key
```

- 다수 key의 value 값 조회
```
mget key key ...
```

- key 이름 변경
```
rename key newkey
```

- key와 value 값 삭제
```
del key
```

- 모든 데이터 삭제
```
flushall
```

## Redis와 Spring Boot 연동

- Redis 저장소에 대한 CRUD REST API 구현

#### POST /redis
![post](/uploads/e2f6683efff3e6887ee3ffa28d67aad9/post.JPG)

#### GET /redis
![get](/uploads/da14df263bb053a454d7de1affb42a7f/get.JPG)

#### PUT /redis
![put](/uploads/078a741bf812e72487e684876ca719f8/put.JPG)

#### DELETE /redis
![delete](/uploads/3b785d99a46ddc80caf89605847d104a/delete.JPG)

## 강의를 진행하며 느낀점
- 강의를 진행하며 다시 한번 아는 것과 이를 설명하는 것은 다르다는 것을 느꼈다. 이미 알고 있던 내용도 직접 설명하려하니 내가 알고 있던 것이 틀린 것은 아닌지 계속해서 찾아보고 확인해보았던 것 같다. 그리고 직접 실습을 진행하면서 동시에 설명까지 같이 하려니 그 또한 쉽지 않음을 느꼈다.
- 이후에 큰 규모로 Redis를 활용할 경우가 생긴다면 해당 프로젝트를 진행하며 알게 된 지식을 더욱 확장시켜볼 수 있을 것 같다.

## References

<https://ko.wikipedia.org/wiki/%EB%A0%88%EB%94%94%EC%8A%A4>

<https://aws.amazon.com/ko/redis/>

<https://freeblogger.tistory.com/10>

<https://github.com/microsoftarchive/redis/releases>

<https://wickies.tistory.com/99>
