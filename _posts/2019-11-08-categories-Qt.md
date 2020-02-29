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
* [7. notify override 해보기](https://goodayth.github.io/Qt-GDI-S2-7/)
* [8. QObject::event override 해보기](https://goodayth.github.io/Qt-GDI-S2-8/)
* [9. Event Filter 사용해보기 : QApplication에 Event Filter 넣기](https://goodayth.github.io/Qt-GDI-S2-9/)
* [10. Event Filter 사용해보기 : QObject에 Event Filter 넣기](https://goodayth.github.io/Qt-GDI-S2-10/)
* [11. qt에서 쓰는 모든 event 이론적 정리](https://goodayth.github.io/Qt-GDI-S2-11/) : window, post, send event
* [12. send, post event 예제](https://goodayth.github.io/Qt-GDI-S2-12/)

### Section 3. Custom Widgets

* [15. 색 선택 위젯 만들기](https://goodayth.github.io/Qt-GDI-S3-15/)
    - 사용 기술
    - `setStyleSheet`
    - `emit`
    - `QGridLayout`
    - `QColor`
    - `QList<QColor>`

<center><img src="/file/image/qt-gdi-s2-15-image-1.png" width="50%" height="50%"></center>

* [16. 현재 시간 출력 위젯 만들기](https://goodayth.github.io/Qt-GDI-S3-16/)
    - `QTimer`
    - `QFont`
    - `QTime::currentTime`
    - `QDate::currentDate`

<center><img src="/file/image/qt-gdi-s3-16-image-1.png" width="50%" height="50%"></center>

* [17. button event 가로채기](https://goodayth.github.io/Qt-GDI-S3-17/)
    - `mouseDoubleClickEvent`
    - `emit`

* [18. 물탱크 신호등 만들기](https://goodayth.github.io/Qt-GDI-S3-18/)
    - `paintEvent`
    - `QPen`
    - `update`

<center><img src="/file/image/qt-gdi-s3-18-image-1.png" width="50%" height="50%"></center>

### Section 4. Painting and Drawing

* [23. QPainter는 logical coordinate에 그린다](https://goodayth.github.io/Qt-GDI-S4-23/)
* [24. QWidget에 그리기(QPixelMap 이용하기)](https://goodayth.github.io/Qt-GDI-S4-24/)
* [25. 다양한 도형 그리기](https://goodayth.github.io/Qt-GDI-S4-25/)

<center><img src="/file/image/qt-gdi-s4-25-image-1.png" width="50%" height="50%"></center>

* [26. QPen 활용기](https://goodayth.github.io/Qt-GDI-S4-26/)

<center><img src="/file/image/qt-gdi-s4-26-image-1.png" width="50%" height="50%"></center>

* [27. QBrush 활용기](https://goodayth.github.io/Qt-GDI-S4-27/)

<center><img src="/file/image/qt-gdi-s4-27-image-1.png" width="50%" height="50%"></center>

* [28. Brush Gradients 활용기](https://goodayth.github.io/Qt-GDI-S4-28/)

<center><img src="/file/image/qt-gdi-s4-28-image-1.png" width="50%" height="50%"></center>

* [29. PainterPath 활용기](https://goodayth.github.io/Qt-GDI-S4-29/)

<center><img src="/file/image/qt-gdi-s4-29-image-1.png" width="50%" height="50%"></center>

* [30. Painter Transform](https://goodayth.github.io/Qt-GDI-S4-30/)
    - `translate`
    - `rotate`
    - `scale`

<center><img src="/file/image/qt-gdi-s4-30-image-1.png" width="50%" height="50%"></center>

* [31. 자동차 그리기 Exmaple](https://goodayth.github.io/Qt-GDI-S4-31/)

<center><img src="/file/image/qt-gdi-s4-31-image-1.png" width="50%" height="50%"></center>

* [32. shape draw widget 만들기](https://goodayth.github.io/Qt-GDI-S4-32/)

<center><img src="/file/image/qt-gdi-s4-32-image-1.png" width="50%" height="50%"></center>

* [37. 그림판 만들기](https://goodayth.github.io/Qt-GDI-S4-37/)

<center><img src="/file/image/qt-gdi-s4-37-image-1.png" width="50%" height="50%"></center>

### Section 5. Drag and Drop / Clipboard

* [40. Drag and Drop 기본적 함수](https://goodayth.github.io/Qt-GDI-S5-40/)
    - `QDrag`
    - `QMimeData`
    - `dragEvent`
    - `manhattanLength`

* [41. Drag and Drop Widget 만들기(TEXT)](https://goodayth.github.io/Qt-GDI-S5-41/)

<center><img src="/file/image/qt-gdi-s5-41-image-1.png" width="50%" height="50%"></center>

* [42. Drag and Drop Widget 만들기(IMAGE)](https://goodayth.github.io/Qt-GDI-S5-42/)

<center><img src="/file/image/qt-gdi-s5-42-image-1.png" width="50%" height="50%"></center>

* [43. Drag Widget 만들기](https://goodayth.github.io/Qt-GDI-S5-43/)

<center><img src="/file/image/qt-gdi-s5-43-image-1.png" width="50%" height="50%"></center>

* [44. Clipboard 컨트롤](https://goodayth.github.io/Qt-GDI-S5-44/)

* [45. 그림판 Clipboard 이미지 삽입](https://goodayth.github.io/Qt-GDI-S5-45/)

<center><img src="/file/image/qt-gdi-s5-45-image-1.png" width="50%" height="50%"></center>

## Etc

* [Windows qt update](https://goodayth.github.io/Qt-update/)
* [qt용 spy++ gammaray](https://goodayth.github.io/Qt-gammaray/)
* [qtCreator 컴파일러 재설정](https://goodayth.github.io/Qt-creator-comfiler/)