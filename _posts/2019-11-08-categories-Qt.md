---
title: "Qt"
date: 2019-11-08 00:00:00 -0000
---

* [Signal and Slot](https://goodayth.github.io/Qt-signal-slot/)
* [Qt SubClassing](https://goodayth.github.io/Qt-subclassing/)
* [Qt win native msg 처리](https://goodayth.github.io/Qt-native-msg/)
* [SingleShot](https://goodayth.github.io/Qt-singleshot/)
* [Action](https://goodayth.github.io/Qt-action/)
* [QTextStream](https://goodayth.github.io/Qt-qtextstream/)
* [QFile](https://goodayth.github.io/Qt-qfile/)
* [QThread1](https://goodayth.github.io/Qt-thread/)
    - thread 확인법
    - thread 생성하기
    - qthread 상속하기
    - threadpool사용
    - mutex 사용
    - semaphoere 사용
    - waitcondition 사용
* [QThread2](https://goodayth.github.io/Qt-thread-2/)
    - thread signal and slot
    - QtConcurrent::run
    - QFutureWatcher

* 간단 정리
    - QString to const char : `qstr.toStdString().c_str();`
    - int to QString : `QString s = QSTring::number(i);`

## Qt GUI

* [qtdesigner이용 .ui파일 및 .h파일 생성하기](https://goodayth.github.io/Qt-qtdesigner/)

## GUI Development - Intermediate

### Section 2. Event Handling

* [3. Event Handler 기본코드](https://goodayth.github.io/Qt-GDI-S2-3/) : mouseEvent처리해 보기
* [4. QWidget의 Event 살펴보기](https://goodayth.github.io/Qt-GDI-S2-4/) : QtCreator에서 Event쓰는 방법 정리
* [5. Event Loop 이론적 내용](https://goodayth.github.io/Qt-GDI-S2-5/)
* [6. 상속을 통한 이벤트 호출순서](https://goodayth.github.io/Qt-GDI-S2-6/) : + 이벤트 ignore했는지 확인해보기(`isAccepted()`)

## Etc

* [Windows qt update](https://goodayth.github.io/Qt-update/)
* [qt용 spy++ gammaray](https://goodayth.github.io/Qt-gammaray/)
* [qtCreator 컴파일러 재설정](https://goodayth.github.io/Qt-creator-comfiler/)