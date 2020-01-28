---
title: "(C++) this call"
date: 2020-01-28 00:00:00 -0000
---

## this call 이란?

> 우선, 함수는 객체마다 따로 만들어 지지않는다 라고 알고 있다.<br>
> (예를들어 아래의 p1, p2의 set이 따로 만들어지지 않음)<br>
> 그럼 p1의 set을 호출시 컴파일러는 어떻게 p1의 set임을 알까?<br>

```cpp
class Point
{
  int x = 0, y = 0;
public:
  void set(int a, int b)
  {
    x = a;
    y = b;
  }
};

int main()
{
  Point p1;
  Point p2;
  
  p1.set(10, 20);
}
```

> 컴파일러에서 어떻게 호출이 되는지 보자.

```cpp
// 컴파일러는 실제로 객체를 다음과 같이 호출하게 된다.
set(&p1, 10, 20);

// 받는쪽에서는
void set(Point* const this, int a, int b)
{
  this->x = a;
}
// 이런식으로 받게됨 -> 이런것을 this call이라 한다.
```

---

## 좀 더 정확하게 보자.

```cpp
p1.set(10, 20);   // 을 호출시
// push 20
// push 10
// (32bits) lea ecx, &p1
// (64bits) lea rcx, &p1
// call Point::set
// Point::set에서는 ecx or rcx를 사용
```

> 참고로 ecx과 rcx는 레지스터이고<br>
> lea는 메모리 복사함수이다.

* 멤버 함수는 1번째 인자로 객체의 주소(this)가 추가된다.

---

## 만약 static 멤버함수는 this call이 어떻게 되나?

```cpp
class Point {
  static void foo(int a)
  {
    x = a;
  }
};

Point::foo(10);
// push 10
// call Point::foo 이렇게 호출하게 되고...
```

```cpp
static void foo(int a)    // void foo(int a)
{
  x = a;    // this->x = a; 선언해야하는데 this가 없으니 error!
}
```

> 이러한 이유로 static멤버함수내에서는 멤버변수에 접근할 수 없다.

* static 멤버 함수는 개체의 주소(this)가 추가되지 않는다.