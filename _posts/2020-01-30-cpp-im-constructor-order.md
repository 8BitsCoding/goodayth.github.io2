---
title: "(C++) 생성자 호출순서"
date: 2020-01-30 00:00:00 -0000
---

```cpp
class Base
{
public:
  Base() { cout << "B()" << endl; }
  Base(int a) { cout << "B(int)" << endl; }
  ~Base() { cout << "~B()" << endl; }
};

class Derived : public Base
{
public:
  Derived() { cout << "D()" << endl; }
  Derived(int a) { cout << "D(int)" << endl; }
  ~Derived() { cout << "~D()" << endl; }
};

int main()
{
  Derived d;
  // Base()
  // Derived()
  // ~Derived()
  // ~Base()
  // 파생 클래스 생성시 기반 클래스의 생성자가 먼저 호출된다.
  
  Derived d1(5);
  // Base()
  // Derived(int)
  // ~Derived()
  // ~Base()
  // 기반 클래스의 생성자는 항상 디폴트 생성자가 호출된다.
  
  // 만약 기반 클래스의 디폴드 생성자가 없다면 객체를 만들 수 없다.
}
```

> 좀 더 자세히 살펴보자.

```cpp
class Base
{
public:
  Base() { cout << "B()" << endl; }
  Base(int a) { cout << "B(int)" << endl; }
  ~Base() { cout << "~B()" << endl; }
};

class Derived : public Base
{
public:
  Derived() // : Base() - 컴파일러가 암묵적으로 넣어준다.
  { 
    cout << "D()" << endl; 
  }
  Derived(int a) : Base(a) // 만약 사용자가 다음과 같이 정의한다면 컴파일러는 별도로 생성하지 않는다.
  { 
    cout << "D(int)" << endl; 
  }
  ~Derived() { cout << "~D()" << endl; }
};

int main()
{
  Derived d(5);
}
```

```cpp
class Animal
{
protected:
  Animal() {}
};

class Dog : public Animal
{
public:
  Dog() : Animal() {}
};

int main()
{
  Animal a;   // error
  Dog d;      // ok
}
```

* protected constructor - 자신은 객체를 만들 수 없지만, 파생클래스의 객체는 만들 수 있게한다.

---

