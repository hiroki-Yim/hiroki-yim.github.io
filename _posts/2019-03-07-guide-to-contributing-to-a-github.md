---
title: "깃허브에서 협업하기 (라라벨)"
date: "2019-03-07 10:41:00"
categories: github contributing
author_profile: true
read_time: true
toc: true #Table Of Contents 목차 보여줌
toc_label: "Index" # toc 이름 정의
# toc_icon: "cog" #font Awesome아이콘으로 toc 아이콘 설정
toc_sticky: true # 스크롤 내릴때 같이 내려가는 목차
---

## 참고한 블로그

[협업을 위한 Git](https://gmlwjd9405.github.io/2017/10/27/how-to-collaborate-on-GitHub-1.html)

[Git 최초 설정 블로그](https://git-scm.com/book/ko/v1/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)

---

GITHUB で協業しよう（ララベル）

**깃 기본 명령어**

기본 설정
git config --list 명령을 실행하면 설정한 모든 것을 확인할 수 있음

git config --global user.name "name"

git config --global user.email "email"

상태 확인(현재 브런치, 코드 변경 사항)

git status
->On branch master
->nothing th commit, working tree clean

변경사항 저장
git add [변경 파일명] | . | \*

커밋
git commit -m "쓰고싶은 말"

모든 변경사항 저장 + 커밋
git commit -a -m "쓰고싶은 말"

원격 저장소 업로드
git push -u origin master

---

**협업 과정**

1. 메인 저장소에서 로컬 저장소로 가져오기 (최초작업)

   git clone [저장소 주소]

   composer install

   .env 파일수정 및 파일명 변경 (php artisan key:generate)

2. 브런치 만들기(기능별)

   git checkout -b "branch_name"

브런치 생성한 뒤 그 브런치로 브런치변경

// 위의 명령어는 아래의 두 명령어를 합한 것

\$ git branch [branch name]

\$ git checkout [branch name]

3. 기능 개발 후 로컬에서 add & commit

4. 메인 저장소 업로드 (origin은 repository 주소)

   git push -u origin [branch name]

5. 깃허브에서 pull request & merge(병합)

6. git checkout master로 돌아감

7. (다른 협업자는) 변경사항(github 소스)을 본인 로컬 저장소로 반영(갱신)
   git pull origin master

8. 무한 반복
