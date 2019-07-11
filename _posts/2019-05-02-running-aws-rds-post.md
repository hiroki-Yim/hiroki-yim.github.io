---
title: "AWS의 RDS를 이용해보자"
date: "2019-05-02 20:10:00"
categories: study AWS RDS
author_profile: true
read_time: true
toc: true #Table Of Contents 목차 보여줌
toc_label: "AWS" # toc 이름 정의
# toc_icon: "cog" #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
---

# RDS란?

![RDS](https://user-images.githubusercontent.com/33077726/61046541-5e504500-a418-11e9-91a0-2d3e90f2a755.png)

아마존 관계형 데이터베이스 서비스(Amazon Relational Database Service)
아마존이 서비스하는 분산 관계형 데이터베이스로서 관계형 데이터베이스를 쉽게 설정하고, 운영 및 유지보수 할 수 있는 서비스.

## RDS의 특징

1. 간단한 사용법 - 몇 번의 클릭으로 원하는 인스턴스, 버전, 설정셋을 적용한 인스턴스가 수분 내에 생성됨

2. 간편한 백업 - 등록된 데이터를 S3의 스냅샷 기능으로 백업이 가능

3. 스토리지 및 iops(단위 시간당 읽기/쓰기 횟수)확장이 용이함

### 지원하는 인스턴스

RDS의 기본은 클라우드에 있는 분리된 DB환경의 DB인스턴스로서

Amazon Aurora, MySQL, MariaDB, PostgreSQL, Oracle 및 Microsoft SQL Server DB 엔진을 지원함.

## RDS 인스턴스 생성 및 이용

1. 먼저 사용하고자 하는 DB를 고른다. (프리티어의 경우 프리티어 전용 옵션을 사용하면 과금이 되지않는다.)
   ![image](https://user-images.githubusercontent.com/33077726/61046671-ad967580-a418-11e9-8bca-39edee0df13a.png)

2. RDS에 대한 설정을 한다.
   ![image](https://user-images.githubusercontent.com/33077726/61046792-f51d0180-a418-11e9-952c-cbd42320227f.png)
   사용자 이름과 암호는 이후 해당 DB에 접근할 때 사용할 것으로 설정.

3. 고급 설정(보안그룹 및 DB명, 파라미터 그룹 포트번호 등)
   ![image](https://user-images.githubusercontent.com/33077726/61046935-4c22d680-a419-11e9-9960-af9b0311bb1d.png)
   여기서 db의 언어셋이나 시간등을 설정할 수 있다. (데이터베이스 이름은 이후 DB에 접근할 때 사용됨.)

4. 생성완료!
   ![image](https://user-images.githubusercontent.com/33077726/61047129-b3408b00-a419-11e9-9e76-ba81d9b519a8.png)
   설정을 완료하고 등록하면 수분 내에 활성화 되며 접근 가능한 상태가 된다.

5. 이후 활성화된 rds의 엔드포인트를 통해 heidisql과 같은 DB관리 툴이나, 서버의 .env의 파일에 등록 후, 로컬에서 사용한 것과 같이 사용할 수 있게된다.
   ![image](https://user-images.githubusercontent.com/33077726/61047407-64dfbc00-a41a-11e9-9e60-c90e138a06c3.png)
