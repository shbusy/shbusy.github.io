---
title: Jekyll 블로그 만들기
date: 2023-12-19 15:33:00 +0800
categories: [Dev, blog]
tags: [jekyll]
---
### 우분투 설치
저는 윈도우에서 작업하기때문에 파워쉘에서 우분투를 설치해주고 사용자계정을 만들어 줍니다
```
wsl --install -d Ubuntu-22.04
```
### 리눅스 패키지 관리도구 설치
이유는 모르겠으나 root계정으로 ruby를 설치하면 좋지 않다고하니 저는 sudo를 붙여줍니다
```
sudo apt-get update
```
### ruby, gem 설치
```
sudo apt-get install ruby-full build-essential zlib1g-dev
sudo gem install jekyll bundler
```
