---
title: Jekyll 블로그 만들기
date: 2023-12-19 15:33:00 +0800
categories: [Dev, blog]
tags: [jekyll]
---
## 우분투 설치
윈도우 파워쉘에서 우분투를 설치해주고 사용자계정을 만들어 준다
```
wsl --install -d Ubuntu-22.04
```
## 리눅스 패키지 관리도구 설치
이유는 모르겠으나 root계정으로 ruby를 설치하면 좋지 않다고하니 sudo를 붙여 실행
```
sudo apt-get update
```
## ruby, gem 설치
```
sudo apt-get install ruby-full build-essential zlib1g-dev
sudo gem install jekyll bundler
```
## 블로그 생성
여기부터는 선택지가 나뉜다  
존재하는 테마를 깃 fork 해서 만들어도 되고  
zip파일을 로컬에 복사해서 실행하여도 상관없다  

### 테마를 fork해올경우
원하는 테마가 있는 깃 레포지토리에서 본인 깃으로 fork  
```
git clone 복사한 본인 깃 클론 주소
```
이후는 로컬에서 생성된 블로그를 확인 가능하다 http://127.0.0.1:4000/
### zip으로 복사해올경우  
먼저 본인 깃에 새 레포지토리를 username.gitgub.io 라는 이름으로 생성  
생성한 깃 레포지토리를 클론해오고 해당 레포지토리 하위경로에 블로그생성
```
cd username.gitgub.io/
sudo jekyll new ./ -f
```
기본 jekyll 블로그 생성이 완료되었으면 받아둔 테마 zip파일을 덮어씌운 후  
404.html, about.markdown, index.markdown 파일들을 삭제한다
```
bundle install
bundle exec jekyll serve
```
이후는 로컬에서 생성된 블로그를 확인 가능하다 http://127.0.0.1:4000/
## 진행중 만난 오류
### wsl/installdistro/0x80073d05
우분투 패키지를 마구잡이로 설치하다 만난 오류  
우분투 앱 삭제도 되지 않고 우분투 설치 삭제도 되지않아서 (무한 등록 취소중) 헤매다가  
windows subsystem for linux 이친구를 제어판 설치제거 시도한 뒤 중간에 취소해보았다  
이후 정상작동 확인
### layout: home # index page
zip으로 테마 적용하고 로컬은 정상인데 깃 푸시후 깃블로그에서 해당 오류 발생  
깃 리포지토리 내 setting-> pages-> jekyll Configure -> ruby 버전을 본인 프로젝트의 버전으로 작성하고 커밋한 후 정상작동됨을 확인  
해당 오류는 원인이 여러가지인데 내 경우엔 이 방법으로 해결되었다


