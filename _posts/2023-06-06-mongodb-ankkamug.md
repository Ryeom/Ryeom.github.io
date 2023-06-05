---
title: 'MongoDB 메모'
toc: true
toc_sticky: true
categories:
   - DB
last_modified_at: 2023-06-03T00:00:00-00:00
first_writed_at: 2023-06-03T00:00:00-00:00
subtitle: query 정리
---

```mongodb

use gateway_configration //  gateway_configration라는 데이터베이스를 생성
//switched to db gateway_configration

db
//gateway_configration

show dbs // database list 확인 -> gateway_configration 안보임

db.endpoint.insertOne({
    "name" : "achilles",
    "host" : "123.456.789.00",
    "port" : "80",
    "need-load-balancing" : true,
    "is-encrypted" : true,
});

show dbs // database list 확인 -> gateway_configration 보임 (데이터 넣었기때문)




```