# Redis
<img src="https://media.vlpt.us/images/limsubin/post/ac3da3f4-ead2-4790-8cd3-eda18726ac6f/redis.png" width="240" height="80">

## 목차

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
- [References](#references)

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
![post](https://user-images.githubusercontent.com/55876368/147932515-e54e8100-6aa3-4597-9fe7-d4b822c224df.JPG)

#### GET /redis
![get](https://user-images.githubusercontent.com/55876368/147932571-ff5a553c-27ff-48eb-b395-319b7b223854.JPG)

#### PUT /redis
![put](https://user-images.githubusercontent.com/55876368/147932597-3a323828-bf3f-4542-95c6-d728a79c93de.JPG)

#### DELETE /redis
![delete](https://user-images.githubusercontent.com/55876368/147932624-06846aa2-211d-4ce3-9a6f-afc146f114bc.JPG)

## References

<https://ko.wikipedia.org/wiki/%EB%A0%88%EB%94%94%EC%8A%A4>

<https://aws.amazon.com/ko/redis/>

<https://freeblogger.tistory.com/10>

<https://github.com/microsoftarchive/redis/releases>

<https://wickies.tistory.com/99>
