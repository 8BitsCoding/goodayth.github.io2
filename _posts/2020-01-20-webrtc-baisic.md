---
title: "(WebRTC) WebRTC 기초 다지기"
date: 2020-01-20 00:00:00 -0000
---

### 목차

* [WebRTC in a Single Browser](#WebRTC-in-a-Single-Browser)
* [간단한 Node.js서버 띄워보기](#간단한-Node.js서버-띄워보기)

---

### WebRTC in a Single Browser

#### nvm설치

> 우선 다양한 버전의 node.js를 사용하기 위해서 nvm이 필요하다.

* [다운로드 github : nvm](https://github.com/nvm-sh/nvm)
* [다운로드 github : nvm-windows](https://github.com/coreybutler/nvm-windows)
* [nvm-windows installer](https://github.com/coreybutler/nvm-windows/releases) : setup으로 다운로드

* [nvm windows 설치 참고사이트](http://hong.adfeel.info/backend/nodejs/window%EC%97%90%EC%84%9C-nvmnode-version-manager-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/)

> 기존의 Node.js를 삭제한다. -> 삭제 시 `C:\Users\AppData\Roaming\npm`경로의 npm 관련데이터까지 완전삭제를 해야한다.
>
> nvm-setup을 다운로드 후 nvm을 설치한다.
>
> 관리자권한으로 커멘드 창을 열어 필요버전의 node.js를 설치한다.

```s
# 설치가능 버전확인
$ nvm list available
```

```s
# 이 강좌에서는 v0.12.0을 사용
$ nvm install v0.12.0
```

```s
# 버전이 잘 설치되었는지 확인하자
$ nvm list
```

![](webrtc-baisic_Image_01.png)

```s
# 사용버전을 선택하자
$ nvm use v0.12.0
```

---

#### Setting Up Your Node.JS Application

> 위에서 설치한 버전이 install이 안되는거 같아 버전 변경

```s
$ nvm install 12.14.1
$ nvm use 12.14.1
```

> 우선 버전 프로젝트를 생성하는데 필요한 버전정보 확인

```s
$ npm show ejs version
$ npm show express version
```

> package.json을 다음과 같이 작성 후 프로젝트 생성

```json
{
    "name": "intro-webrtc",
    "version": "0.0.1",
    "private": true,
    "dependencies": {
        "express": "4.x",
        "ejs": "3.x"
    }
}
```

```s
$ npm install
```

---

### 간단한 Node.js서버 띄워보기

> server.js 파일생성

```js
var express = require('express');
var app = express();
console.log('server started');

app.get('/', function(req, res){
    res.render('index.ejs');
});

app.listen(3000);
```

> public, views 폴더생성

> views 폴더내에 index.ejs파일 생성

```html
<!DOCTYPE html>>
<html lang="en">
    <head>
        <title>0'Reilly Introduction to WebRTC</title>
    </head>
    <body>
        Hello WebRTC
    </body>
</html>
```

> localhost:3000으로 접속해본다.

![](webrtc-baisic_Image_02.png)