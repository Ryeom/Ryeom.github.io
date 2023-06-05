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
    "seq" : 0, 
    "name" : "achilles",
    "host" : "123.456.789.00",
    "port" : "80",
    "need-load-balancing" : true,
    "is-encrypted" : true, 
});

show dbs // database list 확인 -> gateway_configration 보임 (데이터 넣었기 때문)


// TTL collection 생성
db.signatrue.createIndex({"createdAt":1},{expireAfterSeconds : 120}) //createdAt을 기준, 해당 value값의 시점보다 120초 이후면 삭제되도록 index생성
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}


db.signatrue.createIndex({"expiredAt":1 }, {expireAfterSeconds:0}) //expiredAt 필드를 기준, 해당 시점과 현재 시점이 같을경우 삭제하도록 생성
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}

// 주의 : mongodb의 TTL은 1분에 한번씩 동작한다. 코드로 적용할때 주의



db.endpoint.createIndex({name:1,seq:1},{unique:true}) // endpoint collection에 name과 seq를 유니크로 설정
// 두개를 PK로 지정 및 index 설정


db.endpoint.dropIndex({name:1,seq:1,host:1}) // 삭제도 이렇게 진행~

```