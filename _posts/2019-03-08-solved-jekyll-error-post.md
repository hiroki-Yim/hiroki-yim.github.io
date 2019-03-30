---
title: "Github.io Blog, Jekyll 에러 해결기록"
date: 2019-03-08 08:03:00
categories: github error jekyll 開発日記
---

## happening

github.io를 이용해 정적 블로그를 무료로, 그것도 쉽게 구축할 수 있다는 소식을 접하여 commit + bloging을 하고자 인터넷을 찾아 구축하게 되었다.
그러던 중 다른 화려한 git 블로그를 접하게 되면서 theme적용을 결심하게 되었다.[Imreplay님의 JEKYLL + Github.io 블로그 구축](https://imreplay.com/blogging/minimal-mistakes-%ED%85%8C%EB%A7%88%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%B4-githubio-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EA%B5%AC%EC%B6%95%ED%95%98%EA%B8%B0/)
jekyll theme를 적용한 뒤 기존에 있던 file들을 옮기는 과정에서 add, commit, push를 했더니
![image](https://user-images.githubusercontent.com/33077726/53994085-9139b200-4174-11e9-893b-67f862fe4fc8.png)
위와 같은 오류가 발생하면서 올린 파일들이 블로그에 적용되고 있지 않았다.

하지만 어째서인지 어떤 부분에서 어떤 오류가 뜨고 있는지 확인할 수 없었다.
해당 오류는 repository의 settings의 github pages부분에서 확인할 수 있었는데 어떤 오류던 [이 문서](https://help.github.com/en/articles/viewing-jekyll-build-error-messages)를 보여주었다.
해당 문서를 쭉 읽어봤더니 오류를 확인하고 싶으면 로컬에 빌드해서 확인하는 수 밖에 없었는데, ![image](https://user-images.githubusercontent.com/33077726/53994228-09a07300-4175-11e9-8c8f-05eb27dbf824.png)
기존 file을 clone해서 ide에서 markdown으로 작성하고 있었기 때문에
빌드하는 방법을 하나하나 찾아가며 할 수 밖에 없었다.

하여 보았던 문서가 [Setting up your GitHub Pages site locally with Jekyll](https://help.github.com/en/articles/setting-up-your-github-pages-site-locally-with-jekyll)와
[윈도우에 Jekyll 설치하기](https://shryu8902.github.io/_posts/2018-06-22-jekyll-on-windows/) 이 두 가지를 참조하여 설치하였다.

위의 문서를 참조하며 설치하였으나 쉽게 실행되지 않았고, github.io에서 theme를 사용해서 서버를 여는 것과 달리, 직접 필요한 file들을 하나하나 설치 해야했다.

npm과 비슷한 역할을 하는 gem을 사용하기 위해서 ruby를 설치하였고, 블로그에 필요한 패키지는 Gemfile을 참조하여 download받았다.
jekyll serve로 실행하면 되지만, 모듈들의 버전이 맞지않았기에 bundle exec 명령어로 번들하여 실행하니 정상실행 되었다.
또한 bundle exec 명령어로도 안되면 cech65001 명령어로 언어셋을 설정한 다음 실행하면 잘 번들되어 실행된다.

평소 하나에 깊게 빠지지 못하고, 수박 겉핥기 식으로 공부하는 나에게 있어서 이번 이슈는 잘 알지 못하던 여러 가지들을 깊게 공부하게 되면서,
공부를 게을리 하지 말자... 라고 생각하는 계기가 되었다.

![image](https://user-images.githubusercontent.com/33077726/53995174-99472100-4177-11e9-8045-59a117c969b3.png)
(로컬에서 실행한 모습)

에러 발견시간 : 19-03-08 04:00am

에러 해결시간 : 19-03-08 07:30am

---

## 배운 점

1. Gemfile의 역할
2. ruby, jekyll 사용법
3. github.io의 구조
4. folder에 따른 config file작성법

---

## 참고

[JEKYLL 공식 홈페이지](https://jekyllrb.com/)

[사용한 JEKYLL 테마](https://github.com/mmistakes/minimal-mistakes)

---
