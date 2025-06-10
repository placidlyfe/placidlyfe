---
title: "Docker Compose"
description: "Docker Compose"
date: 2025-06-10
published: true
---


## Docker Compose 

### 📝 요약

* Docker Compose는 여러 컨테이너 기반 애플리케이션을 한 번에 정의하고 실행할 수 있는 도구

---

### 🔍 배경

* • 하나의 애플리케이션이 웹 서버, 데이터베이스, 캐시 등 복수의 컨테이너로 구성되면서, 매번 `docker run`으로 일일이 설정하는 것은 비효율적
* • 특히 개발/테스트 환경에서 매번 동일한 조건을 손쉽게 재현하려면 자동화된 컨테이너 정의 및 실행이 필요
* • Docker Compose는 `docker-compose.yml` 파일 하나로 전체 환경을 정의하고, 명령어 한 줄로 구성요소 전체를 실행할 수 있도록 지원

### ⚙️ 주요 개념 & 기술

* `docker-compose.yml` — 서비스 정의, 이미지 빌드, 포트 바인딩, 볼륨, 환경변수 설정 등을 모두 하나의 YAML 파일에 작성
* 서비스(Service) — 개별 컨테이너 단위를 의미하며, 예: `web`, `db`, `redis` 등을 독립적으로 정의
* 네트워크 자동 구성 — Compose는 서비스 간 통신을 위한 가상의 네트워크를 자동 생성함. 
  * 컨테이너 이름이 곧 호스트네임
* 볼륨 마운트 — 개발 환경에서 소스코드를 컨테이너에 실시간 반영하거나 DB 데이터를 영속적으로 저장 


### 🛠️ 주요 명령어
  * `docker compose up` : 컨테이너 빌드 및 실행 (백그라운드 실행은 `-d`)
  * `docker compose down` : 실행 중인 모든 컨테이너 중지 및 네트워크 제거
  * `docker compose build` : Dockerfile 기반 이미지 재생성
  * `docker compose logs` : 전체 또는 특정 서비스 로그 확인
  * `docker compose ps` : 현재 실행 중인 서비스 상태 확인

