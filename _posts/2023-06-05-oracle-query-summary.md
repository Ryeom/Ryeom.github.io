---
title: 'oracle 자주쓰는 query 정리'
toc: true
toc_sticky: true
categories:
   - DB
last_modified_at: 2023-06-03T00:00:00-00:00
first_writed_at: 2023-06-03T00:00:00-00:00
subtitle: query 정리
---

```SQL
SELECT NAME, TYPE, LINE, TEXT, ORIGIN_CON_ID FROM USER_SOURCE WHERE NAME = 'PROC_TYPE_SUBJECT...';

-- NAME,                TYPE,        LINE,  TEXT,                                                                            ORIGIN_CON_ID
-- ==================   ============ ====== ===============================================================================  ===============
-- PROC_TYPE_SUBJECT..,  PROCEDURE,  1,     "PROCEDURE         PROC_TYPE_SUBJECT..",                                           0
-- PROC_TYPE_SUBJECT..,  PROCEDURE,  10,    "(     P_CODE        IN TABLE_NAMEEE.CODE%TYPE      ",                             0
-- PROC_TYPE_SUBJECT..,  PROCEDURE,  11,    "    , P_TYPEE       IN TABLE_NAMEEE.TYPEE%TYPE            ",                      0
-- PROC_TYPE_SUBJECT..,  PROCEDURE,  12,    "    , P_DATE        IN TABLE_NAMEEE.DATEE%TYPE )",                                0
....



```
