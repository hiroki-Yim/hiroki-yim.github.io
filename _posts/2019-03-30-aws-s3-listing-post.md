---
title: "aws s3를 이용하여 리소스 리스팅하기"
date: "2019-03-30 21:00:00"
categories: aws s3 開発日記
author_profile: true
read_time: true
toc: true #Table Of Contents 목차 보여줌
toc_label: "Index" # toc 이름 정의
# toc_icon: "cog" #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
---

## 들어가며

이번 팀 프로젝트에 필요한 기능 중 하나인 aws s3 리소스 관리 시스템
(listing 하기 전에는 로컬에서 파일을 관리했다.)

![image](https://user-images.githubusercontent.com/33077726/56078958-b03cfb00-5e28-11e9-94c2-9c8939a6f169.png)
(이런 식으로)

![image](https://user-images.githubusercontent.com/33077726/56078962-b3d08200-5e28-11e9-8a85-827db0c20518.png)
(폴더와 리소스 부분)

로컬에서 해당 폴더와 리소스를 불러와서 작업하던 형식이었지만, 여러 회원들에게 각자 폴더를 할당 해 주어야 했고,
작업하는 에디터마다 폴더를 생성하여 리소스를 관리할 수 있도록 해주어야 했기 때문에 Aws의 S3를 이용하기로 하였다.

![AwsS3](https://user-images.githubusercontent.com/33077726/55275614-fcb61000-532b-11e9-9063-dd32c1731af4.png)
(웹에서 버킷으로 접근하여 본인이 업로드한 리소스를 컨트롤 할 수 있게 만들고 싶었음)

![image](https://user-images.githubusercontent.com/33077726/55275652-75b56780-532c-11e9-964d-12937be29938.png)
먼저, 만들고 있었던 방식은 s3 버킷에 직접 접근하여 file과, directory들을 가져와서
클릭이벤트가 발생하면 해당 디렉토리와 리소스에 접근할 수 있도록 만들었으나, 구조가 복잡해짐에 따라
핸들링 하는대에 난항을 겪고 있었다.

이 때, 핸들링하는 방법에 대해 구글링 하던 도중 [S3 Bucket Listing](https://github.com/rufuspollock/s3-bucket-listing)이라는 git repository를 발견 하였다!(띠-용)
이 라이브러리는 기존 존재하는 HTML문서에 Bucket에 대한 정보만 입력하고, 해당 Bucket에 Root에 넣어두기만 해도
자동으로 Bucket의 모든 폴더를 listing해주었다.
![image](https://user-images.githubusercontent.com/33077726/55275706-47845780-532d-11e9-9518-9338379e5571.png)

바로 개발중인 프로젝트에 적용해보았더니 아주 잘 동작하였다.
![image](https://user-images.githubusercontent.com/33077726/55275719-7e5a6d80-532d-11e9-88e5-0d44b60113e4.png)
(비루한 프론트화면...)

이 HTML문서에서는 JS파일을 서버에서 불러서 쓰고 있었는데, 필요한 정보를 화면에 뿌려주기 위하여 수정이 필요하였다.
그래서 JS파일을 HTML문서와 같이 Bucket의 Root폴더에 넣고 지정해주었더니... 역시 잘 되었다 ㅎㅎ
S3는 파면 팔수록 편한 기능과 라이브러리가 많은 것 같다!

---

## 배운 점

1. 직접 개발하기 전에 라이브러리를 찾아보자...
2. S3 Bucket을 웹에서 접근 할 수 있다는 점(?)
3. Bucket 구조
4. Bucket내의 리소스들의 상호관계(?)

---

## 참고

[AWS S3 Listing GitHub](https://github.com/rufuspollock/s3-bucket-listing)

[About AWS S3](https://aws.amazon.com/ko/s3/)

---
