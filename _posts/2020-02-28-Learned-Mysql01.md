---
layout: categories
title:  "Mysql ODBC Connection"
excerpt: ODBC 학습
toc: true
toc_sticky: true
categories : Database
---

## Mysql
* 대표적인 DBMS(DataBase Management System)의 약자 , 데이터베이스를 관리하는 시스템 또는 소프트웨어 중 대표적인 소프트웨어<br/>
* 간단하게 DB는 데이터의 저장소를 말하며 , DBMS는 이 DB를 관리하는 소프트웨어정도 라고 볼 수 있다.
---
### ODBC ? 
  * 우선 ODBC란 __데이터베이스에 접근하기 위한 소프트웨어의 표준 규격__ 이다.

이렇게 정의를 본다해도 잘 와닿지는 않는다...,,

찾아보니 간단하게 DBMS와 통신할 수 있는 API라고 하면 쉬울 것 같다!

하지만 DBMS마다 API 사용법이 달라서 많은 불펴함이 존재한다고 한다.

그래서 MS사가 ODBC라는 데이터베이스에 접근하기 위한 표준 규격을 통일 시키게 됐다.

이 규격에 따라서 DBMS는 자기네 API에 접근하여 조종하는 "ODBC Driver"라는 것을 제공한다.

---

### 발생 에러
* Visual Studio 2017에서 asp를 활용, 하지만 
`Error “Source character set not supported by client” when field set to uft8mb4_general_ci` 라는 에러가 발생했고 구글링을 통해 이것이 지원하지 않는 형식의 캐릭터 셋이라는 것을 파악했습니다.
그래서 ``ALTER TABLE `my_test_table` CONVERT TO CHARACTER SET utf8 COLLATE utf8_unicode_ci``
<br/>명령을 통해 셋을 변경시켜 정상적으로 작동시켰습니다.

![image](https://user-images.githubusercontent.com/37209763/109606350-e0e7c400-7b69-11eb-8729-665a9b8218aa.png)

<br/> **ODBC를 활용해 mysql에 저장된 데이터들이 정상적으로 웹 페이지에 띄어진 모습**

---