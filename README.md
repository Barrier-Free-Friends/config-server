# Config Server

Barrier Free Friends MSA의 중앙 설정 관리 서버입니다. Spring Cloud Config Server 기반으로, 각 서비스가 실행 시 원격 Git 저장소의 설정 파일을 불러올 수 있도록 제공합니다.

전체 서비스 구성은 [조직 README](https://github.com/Barrier-Free-Friends)를 참고하세요.

## 기술 스택
- Java 21, Spring Boot 3.5.7
- Spring Cloud Config Server
- Eureka Client, Actuator/Prometheus

## 동작 방식
- 설정 원본: [`project-config`](https://github.com/Barrier-Free-Friends/project-config) 저장소 (`configs/common`, `configs/{application}` 경로 탐색)
- 각 서비스는 `optional:configserver:` 형태로 이 서버를 참조해 공통/개별 설정을 가져옵니다.
- Eureka Server에 등록되어 서비스 디스커버리에 참여합니다.

## 실행

```bash
./gradlew bootRun
```

기본 포트: `3100`

## Docker

```bash
docker build -t config-server .
docker run -p 3100:3100 config-server
```
