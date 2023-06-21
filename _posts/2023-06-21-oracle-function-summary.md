---
title: 'oracle 내장함수 정리'
toc: true
toc_sticky: true
categories:
   - DB
last_modified_at: 2023-06-03T00:00:00-00:00
first_writed_at: 2023-06-03T00:00:00-00:00
subtitle: 내장함수 정리
---

* dual : 단순한 계산부터, 산술연산, 함수결과 등 쿼리 결과를 간편하게 확인해볼 수 있는 임시테이블
```SQL
SELECT GREATEST(100, 200, 300, 400, 500) FROM dual;
SELECT LEAST(100, 200, 300, 400, 500) FROM dual;
SELECT GREATEST('AAA', 'BBB', 'CCC', 'DDD') FROM dual;
SELECT SYSDATE, GREATEST(SYSDATE, SYSDATE + 1, SYSDATE + 2) FROM dual;

SELECT GREATEST(100, 200, 300, 400, NULL) FROM dual; -- null은 안돼...! -> 결과가 NULL로 나옴
SELECT GREATEST(100, 200, 300, 400, 'AAA') FROM dual; -- 데이터 형식 달라도 안됨


```
