---
title: "IndexedDB"
description: "IndexedDB"
date: 2025-06-08
tags:
    - IndexedDB
    - BrowserStorage
# published: false
---

### IndexedDB

* **IndexedDB란?**

  * 브라우저 내장 비관계형(키‑값) 데이터베이스
  * 오프라인·대용량(수백 MB 이상) 클라이언트 저장소 제공

* **저장 구조**

  * 데이터베이스(DB) → 오브젝트 스토어(Object Store) → 레코드(키·값)
  * 인덱스(Index)로 검색 성능 향상 가능
  * 버전 관리: `onupgradeneeded` 이벤트에서 스키마 정의

* **주요 API 흐름**

  1. `indexedDB.open(name, version)` → IDBOpenDBRequest 반환
  2. `request.onupgradeneeded` → 오브젝트 스토어/인덱스 생성
  3. `request.onsuccess` → `db` 객체 획득
  4. 트랜잭션(`db.transaction([...], mode)`) 생성 후 CRUD 수행

* **트랜잭션 모드**

  * `readonly` | `readwrite` | `versionchange`
  * 자동 커밋, 실패 시 전부 롤백

* **대표 메서드**

  * `objectStore.add(value, key?)`
  * `objectStore.put(value, key?)`
  * `objectStore.get(key)` / `getAll()`
  * `objectStore.delete(key)` / `clear()`
  * `objectStore.index(indexName)` → 인덱스 접근

* **장점**

  * 대용량 바이너리(Blob) 저장 가능
  * 비동기 + 트랜잭션 지원으로 UI 블로킹 최소화
  * 인덱스 기반 고속 검색

* **단점**

  * 콜백/프라미스 체인 복잡 → wrapper 라이브러리 권장
  * 동기 API 없음(워커 제외)
  * 스키마 변경 시 마이그레이션 코드 필요

* **활용 예시**

  * PWA 오프라인 캐시(글·이미지·지도 타일)
  * 실시간 편집 앱(노트, To‑Do) 임시 저장
  * 대용량 로그/분석 데이터 클라이언트 보관

* **브라우저 지원** (2025‑06 기준)

  * 크롬, 사파리, 파이어폭스, 엣지: 최신 버전 기본 지원
  * iOS 15+ safari 지원(CORS/키 범위 일부 제한 주의)

* **간단 팁**

  * `idb`(Jake Archibald)·Dexie.js 등 프라미스 래퍼 사용 시 코드 간결
  * 일괄 삽입 시 트랜잭션 범위 하나로 묶어 성능 ↑
  * 불필요한 인덱스 남발 시 쓰기 성능 ↓

* **참고 자료**

  * MDN IndexedDB Guide
  * W3C IndexedDB Level 3 Spec
  * Jake Archibald "IndexedDB Promised" 블로그
