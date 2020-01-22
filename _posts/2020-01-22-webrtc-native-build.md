---
title: "(WebRTC) Native Build"
date: 2020-01-22 00:00:00 -0000
---

## depot_tools 설치

```s
$ mkdir depot_tools
$ cd depot_tools
$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
```

---

## 환경변수 설정

`PATH = ~webrtc\depot_tools`

---

## gclient 설치

```s
# 관리자모드 실행
$ gclient
# 자동으로 설치된다.
```

---

## 환경변수 설정2

```s
set DEPOT_TOOLS_WIN_TOOLCHAIN=0
set GYP_MSVS_VERSION=2017
set GYP_GENERATORS=ninja,msvs-ninja
set GYP_DEFINES=component=shared_library target_arch=x64
```

---

## webrtc 다운로드

```s
$ mkdir webrtc-checkout
$ cd webrtc-checkout
$ fetch --nohooks webrtc
$ cd src
$ branch -r
# 최신 버전을 선택
$ git checkout branch-heads/?
$ gclient sync --force
```

---

## 빌드

```s
# in src folder
$ gn gen out/x64/Debug --args="is_debug=true use_rtti=true target_cpu=\"x64\""

# .sln 파일생성
$ gn gen --ide=vs out\Default

# visual studio 자체 빌드가 되지 않기에 빌드는 위에 처럼하거나 아래처럼 간단빌드가능
$ gn gen out\Default
```

---

* [참고사이트1](https://sourcey.com/articles/building-and-installing-webrtc-on-windows)
* [참고사이트2](https://alnova2.tistory.com/1114)