---
title: "AWS를 이용해 프로젝트를 옮겨보자 ()."
date: "2019-04-13 20:10:00"
categories: study AWS
author_profile: true
read_time: true
toc: true #Table Of Contents 목차 보여줌
toc_label: "Index" # toc 이름 정의
# toc_icon: "cog" #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
---

# AWS란?

![image](https://user-images.githubusercontent.com/33077726/56800720-b2ef1580-6856-11e9-9bce-492b9d8b8ede.png)

A. Amazon Web Services의 약자로, 네트워킹을 기반으로 가상 컴퓨터(ex.centOS)와 저장공간(Storage),

네트워크 인프라 구축 등 Amazon에서 제공하는 cloud service이다.

Q. AWS얘기가 나오면 항상 따라오는 Cloud computing이란 뭘까?

우리가 흔히 접하는 데스크탑 등의 물리적인 컴퓨팅 리소스를 네트워크 기반 서비스 형태로 제공하고 있다는 것.

![image](https://user-images.githubusercontent.com/33077726/56801023-68ba6400-6857-11e9-8f69-dfd5838260d5.png)

덕분에 패키지를 설치하고 복잡한 서버 환경을 구축할 필요 없이 5분만에 원하는 운영체제를 설치해서 서비스를 배포할 수 있다.

## 개요 (How to deploy a local project on a server (ec2) using AWS)

카카오톡을 주제로 한 프로젝트를 개발한 적이 있었는데, 주위에 자랑하고픈 마음에 ip주소로 접속을 유도 하였으나

학교 와이파이를 이용하고 있었기 때문에 같은 와이파이접속자 외에는 접근하기가 여간 어려운것이 아니었다.

![image](https://user-images.githubusercontent.com/33077726/56801080-90113100-6857-11e9-8c0e-433cd9037d2b.png)

그렇게 하여 생각한게 흔히 알려진 AWS의 클라우드 컴퓨팅 서비스를 이용하게 되었다.

본인이 학생이고, 증명할 수 있다면 프리티어 서비스에 한하여 1년간 무료로 서비스를 사용할 수 있다.

## EC2 시작하기

_회원가입 및 크레딧 등록 이후의 과정부터 설명_

0. 서버를 구축할 리전을 선택한다.

---

[IAM 설정](https://tech.cloud.nongshim.co.kr/2018/10/11/%EC%B4%88%EB%B3%B4%EC%9E%90%EB%A5%BC-%EC%9C%84%ED%95%9C-aws-%EC%9B%B9%EA%B5%AC%EC%B6%95-2-iam-%EC%9C%A0%EC%A0%80-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0/)

1. EC2 대시보드에 있는 Create Instance를 누른 뒤 구축하고 싶은 OS의 프리티어 버전을 고른다.(AMI)

![image](https://user-images.githubusercontent.com/33077726/56801249-f433f500-6857-11e9-8a74-d52176048e54.png)

- CPU와 메모리 갯수, Network Performance에 따라 가격이 다르게 책정된다.

- 1년간 무료로 사용할 수 있는 프리티어 계정이기에 step2~6 까지는 FreeTire에 맞게 설정해준다.(기본 설정)

[IAM 생성 참고문서](https://tech.cloud.nongshim.co.kr/2018/10/11/%EC%B4%88%EB%B3%B4%EC%9E%90%EB%A5%BC-%EC%9C%84%ED%95%9C-aws-%EC%9B%B9%EA%B5%AC%EC%B6%95-2-iam-%EC%9C%A0%EC%A0%80-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0/)

![image](https://user-images.githubusercontent.com/33077726/56802384-d74cf100-685a-11e9-8684-f4555e1fc26a.png)

---

2. 마지막으로 설정한 인스턴스를 검토한다.

![image](https://user-images.githubusercontent.com/33077726/56802529-40ccff80-685b-11e9-92bb-5310422d4a7d.png)

---

3. AWS 서비스를 사용하기 위한 Private, public Key 설정

시작하기(Launch)버튼으로 AWS를위한 Key를 설정한다.

private key는 로컬에 저장하고 다음 로그인 부터 사용하게 된다.

![image](https://user-images.githubusercontent.com/33077726/56805565-64e10e80-6864-11e9-94ee-0d4e1006d078.png)

Create a New Key pair를 선택 한 뒤 Key pair name을 설정해준다.

여기서 생성된 private key는 Download Key 버튼으로 다운로드 할 수 있고, .pem형식으로 다운로드 받을 수 있다.

Linux의 경우에는 /.ssh/ 디렉토리로 복사하고, chmod 400 ~/.ssh/keyname.pem 명령어로 권한을 설정해준다.

Window의 경우에는 putty와 같은 가상 단말기 프로그램을 이용해서 원격으로 접속할 때 여기서 발급받은 key를 ppk로 변한한 뒤 인증키로 사용할 수 있다.
(puttygen 사용)

---

4. ssh로 AWS 접속하기.

여기선 Window에서 putty를 이용하여 ssh로 접속하는 방법을 사용하겠다.

![image](https://user-images.githubusercontent.com/33077726/56847869-6c63ee80-691c-11e9-89c9-2adf6d497019.png)

1. putty 설정 (ppk등록, UI설정 등)

2. 원격 서버 ip를 적는 곳 (EC2의 IP)

3. 원격 서버의 접속 포트 (ssh사용 22번 포트)

4. 원격 서버로 접속할 방식 지정 (방식에 따라 포트 번호도 달라짐 22번 포트 ssh)

5. 자주 접속할 원격 서버의 설정을 저장 또는 불러와서 접속

ubuntu로 접속 시

![image](https://user-images.githubusercontent.com/33077726/56847941-66bad880-691d-11e9-8b78-fe96621231c0.png)

---

5. 서버를 구축하기 위한 패키지 설치(Laravel)

[Installing Laravel on Ubuntu 18.04 LTS](https://www.howtoforge.com/tutorial/install-laravel-on-ubuntu-for-apache/)

sudo apt-get install vsftpd(ftp 포트설정을 위해 vsftpd 설치)

- vsftpd.conf
  anonymous_enabled=NO 를 YES로 변경 (비계정(guest)의 접속을 허용)
  write_enable=YES에 걸려있는 주석을 제거 (업로드 허용)
  local_umask=022 (마스킹 처리가 되기 때문에 022로 하면 해당파일은 755 라고 설정된다)에 걸려있는 주석을 제거
  root 계접 접속을 허용하려면? \$sudo vi /etc/ftpusers
  root 계정에 앞에 주석처리 해준다 (또는 삭제)

- sshd_config # Authentication:
  LoginGraceTime 120
  PermitRootLogin prohibit-password
  StrictModes yes

PHP, LARAVEL, COMPOSER, git, node.js, npm 설치

- Git 계정 등록
  \$ sudo git config --global user.name "본인 계정 입력"
  \$ sudo git config --global user.email "본인 메일 주소 입력"
  \$ sudo git config --global color.ui "auto"

---

6. 설정이 끝났다면 옮길 프로젝트의 git을 clone한다.

- github clone 순서

1. clone repository
2. sudo chmod -R 755 repository/
3. chmod -R o+w repository/storage
4. make .env file
5. composer update
6. sudo /etc/init.d/apache2 restart

여기까지 제대로 왔다면 주소창에 EC2 ip를 입력하여 접속해보자.
![image](https://user-images.githubusercontent.com/33077726/56848078-53a90800-691f-11e9-8aa6-58d57dc31f45.png)

아뿔싸 500에러가 떴다.
[500에러가 떴을 때 참조](https://stackoverflow.com/questions/31543175/getting-a-500-internal-server-error-on-laravel-5-ubuntu-14-04)

이제 정말 설정 다 했다. EC2 IP로 접속하여 보자.

![image](https://user-images.githubusercontent.com/33077726/56848471-71c53700-6924-11e9-94a9-5854d4915313.png)

이전 로컬에서만 접속할 수 있었던 자신만의 프로젝트를 원격 서버로 배포하고 있기 때문에
ip주소만 알면 어디서든지 접속하여 동일한 화면을 볼 수 있다!

나는 여기서 godaddy와 같은 dns사이트를 이용하여 1년간 .space라는 주소를 구매하여 사용하고 있다.

### 주의

나는 EC2를 사용하는 김에 데이터베이스도 AWS의 서비스인 RDS를 이용하여 구축하였다.

하지만 실제 서비스를 하지않고, 자기 만족으로 사용하던 사이트라는 마음에 보안규칙을 설정하지 않고 돌리고 있었다.

어느 날 로그인이 되지않아 heidi와 같은 DB프론트 소프트웨어를 사용하여 테이블을 확인하였는데 원래 있어야 할 데이터가 아닌 한 통의 편지가 칼럼의 한켠을 차지하고 있었다...

![image](https://user-images.githubusercontent.com/33077726/56848582-cc12c780-6925-11e9-9d70-76db6f72345d.png)

엥 이게 뭐지?

![image](https://user-images.githubusercontent.com/33077726/56848590-de8d0100-6925-11e9-8a2a-d4f5b657db68.png)

holy moly shit 이때까지 친구들과 업로드 했던 많은 게시물이 한 순간에 사르르 녹았다...

RDS를 사용할 예정이라면 보안 규칙을 제대로 설정하고 사용하자...
