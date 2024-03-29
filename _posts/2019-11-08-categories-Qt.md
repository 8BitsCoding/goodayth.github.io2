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
* [Model과 View에 관한 사항 정리](https://goodayth.github.io/Qt-model-view/)

* 간단 정리
    - QString to const char : `qstr.toStdString().c_str();`
    - int to QString : `QString s = QSTring::number(i);`

## Qt GUI

* [qtdesigner이용 .ui파일 및 .h파일 생성하기](https://goodayth.github.io/Qt-qtdesigner/)

## Qt Core Intermediate

* [2. QPointer](https://goodayth.github.io/Qt-CI-S1-2/) : qt용 포인터
* [3. QScopedPointer](https://goodayth.github.io/Qt-CI-S1-3/) : `QScopedPointer` 스마트 포인터
* [4. QSharedPointer](https://goodayth.github.io/Qt-CI-S1-4/)
* [5. QList vs QVector](https://goodayth.github.io/Qt-CI-S2-5/)
* [6. QHash](https://goodayth.github.io/Qt-CI-S2-6/)

> 내용이 간단해서 별도로 정리하지 않음.


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

### Section 6. Model View Architecture Advanced

* [51. Model View Architecture 개념](https://goodayth.github.io/Qt-GDI-S6-51/)

* [52. QListWidgetItem 사용](https://goodayth.github.io/Qt-GDI-S6-52/)

<center><img src="/file/image/qt-gdi-s6-52-image-1.png" width="50%" height="50%"></center>

* [53. QTableWidgetItem 사용](https://goodayth.github.io/Qt-GDI-S6-53/)

<center><img src="/file/image/qt-gdi-s6-53-image-1.png" width="50%" height="50%"></center>

* [54. QTreeWidgetItem 사용](https://goodayth.github.io/Qt-GDI-S6-54/)

<center><img src="/file/image/qt-gdi-s6-54-image-1.png" width="50%" height="50%"></center>

* [55. QFileSystemModel 사용](https://goodayth.github.io/Qt-GDI-S6-55/)

<center><img src="/file/image/qt-gdi-s6-55-image-1.png" width="50%" height="50%"></center>

* [56. QStringListModel 사용](https://goodayth.github.io/Qt-GDI-S6-56/)

<center><img src="/file/image/qt-gdi-s6-56-image-1.png" width="50%" height="50%"></center>

* [57. QSortFilterProxyModel 사용](https://goodayth.github.io/Qt-GDI-S6-57/)

<center><img src="/file/image/qt-gdi-s6-57-image-1.png" width="50%" height="50%"></center>

* [58. list, table, tree personal view 만들기](https://goodayth.github.io/Qt-GDI-S6-58/)

<center><img src="/file/image/qt-gdi-s6-58-image-1.png" width="50%" height="50%"></center>

* [59. 58. 예제에 label 추가하기](https://goodayth.github.io/Qt-GDI-S6-59/)

<center><img src="/file/image/qt-gdi-s6-59-image-1.png" width="50%" height="50%"></center>

* [60. item 추가 기능 넣기](https://goodayth.github.io/Qt-GDI-S6-60/)

<center><img src="/file/image/qt-gdi-s6-60-image-1.png" width="50%" height="50%"></center>

* [61. view 동기화 시키기](https://goodayth.github.io/Qt-GDI-S6-61/)

<center><img src="/file/image/qt-gdi-s6-61-image-1.png" width="50%" height="50%"></center>

* [62. item 열 추가](https://goodayth.github.io/Qt-GDI-S6-62/)

<center><img src="/file/image/qt-gdi-s6-62-image-1.png" width="50%" height="50%"></center>

* [64. item paint 기능 추가](https://goodayth.github.io/Qt-GDI-S6-64/)

<center><img src="/file/image/qt-gdi-s6-64-image-1.png" width="50%" height="50%"></center>

* [65. item data 마우스로 컨트롤](https://goodayth.github.io/Qt-GDI-S6-65/)

<center><img src="/file/image/qt-gdi-s6-65-image-1.png" width="50%" height="50%"></center>

* [66. 최종판](https://goodayth.github.io/Qt-GDI-S6-66/)

<center><img src="/file/image/qt-gdi-s6-66-image-1.png" width="50%" height="50%"></center>

* [67. 왼쪽 리스트 컨트롤 아이템 드레그해서 오른쪽 테이블에 넣기](https://goodayth.github.io/Qt-GDI-S6-67/)

<center><img src="/file/image/qt-gdi-s6-67-image-1.png" width="50%" height="50%"></center>

* [68. view drag and drop](https://goodayth.github.io/Qt-GDI-S6-68/)

<center><img src="/file/image/qt-gdi-s6-68-image-1.png" width="50%" height="50%"></center>

* [69. 68에 personal model 적용](https://goodayth.github.io/Qt-GDI-S6-69/)

<center><img src="/file/image/qt-gdi-s6-69-image-1.png" width="50%" height="50%"></center>

* [73. personal model treeview](https://goodayth.github.io/Qt-GDI-S6-73/)

<center><img src="/file/image/qt-gdi-s6-73-image-1.png" width="50%" height="50%"></center>

* [77. 73 응용](https://goodayth.github.io/Qt-GDI-S6-77/)

<center><img src="/file/image/qt-gdi-s6-77-image-1.png" width="50%" height="50%"></center>

### Section 7. Graphics View Framework

* [79. GraphicsView 핵심 컴포넌트](https://goodayth.github.io/Qt-GDI-S7-79/)
* [80. GraphicsView 활용 mouse 클릭 받으면 네모 출력 위젯 만들기](https://goodayth.github.io/Qt-GDI-S7-80/)
    - `QGraphicsScene`
    - `QGraphicsView`
    - `QGraphicsRectItem`

<center><img src="/file/image/qt-gdi-s7-80-image-1.png" width="50%" height="50%"></center>

* [83. GraphicsView event처리](https://goodayth.github.io/Qt-GDI-S7-83/) : 드레그 가능한 네모 그리기

<center><img src="/file/image/qt-gdi-s7-83-image-1.png" width="50%" height="50%"></center>

* [84. GraphicsView 이미지 출력](https://goodayth.github.io/Qt-GDI-S7-84/)
    - `QGraphicsEllipseItem`
    - `QGraphicsPixmapItem`

<center><img src="/file/image/qt-gdi-s7-84-image-1.png" width="50%" height="50%"></center>

* [85. GraphicsView 클릭으로 Item 넣기](https://goodayth.github.io/Qt-GDI-S7-85/)

<center><img src="/file/image/qt-gdi-s7-85-image-1.png" width="50%" height="50%"></center>

* [86. 85 코드 정리](https://goodayth.github.io/Qt-GDI-S7-86/)

<center><img src="/file/image/qt-gdi-s7-86-image-1.png" width="50%" height="50%"></center>

* [87. Transitate, Scale, Shear, Rotation 기능 사용](https://goodayth.github.io/Qt-GDI-S7-87/)
    - Transitate : x, y 위치지정
    - Scale : 말 그대로 Scale
    - Shear : 비틀기
    - Rotation : 각도 틀기

<center><img src="/file/image/qt-gdi-s7-87-image-1.png" width="50%" height="50%"></center>

* [88. view scale 변경](https://goodayth.github.io/Qt-GDI-S7-88/)

<center><img src="/file/image/qt-gdi-s7-88-image-1.png" width="50%" height="50%"></center>

* [93. Resizable item 만들기](https://goodayth.github.io/Qt-GDI-S7-93/)

<center><img src="/file/image/qt-gdi-s7-93-image-1.png" width="50%" height="50%"></center>

* [94. 93 코드정리](https://goodayth.github.io/Qt-GDI-S7-94/)
* [95. view 이미지로 저장하기](https://goodayth.github.io/Qt-GDI-S7-95/)

<center><img src="/file/image/qt-gdi-s7-95-image-1.png" width="50%" height="50%"></center>

* [96. item으로 item 컨트롤](https://goodayth.github.io/Qt-GDI-S7-96/)

<center><img src="/file/image/qt-gdi-s7-96-image-1.png" width="50%" height="50%"></center>

* [100. item drag and drop 적용](https://goodayth.github.io/Qt-GDI-S7-100/)

<center><img src="/file/image/qt-gdi-s7-100-image-1.png" width="50%" height="50%"></center>

> 아래는 git만 올림

* [GraphicsView로 만든 게임 git](https://github.com/GoodayTH/GraphicsViewGame)

<center><img src="/file/image/qt-gdi-s7-101-image-1.png" width="50%" height="50%"></center>

* [GraphicsView로 만든 그림판 최종판 git](https://github.com/GoodayTH/GraphicsViewPainter)

<center><img src="/file/image/qt-gdi-s7-102-image-1.png" width="50%" height="50%"></center>

## Etc

* [Windows qt update](https://goodayth.github.io/Qt-update/)
* [qt용 spy++ gammaray](https://goodayth.github.io/Qt-gammaray/)
* [qtCreator 컴파일러 재설정](https://goodayth.github.io/Qt-creator-comfiler/)