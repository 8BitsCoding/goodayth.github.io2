---
title: "(C++) exception"
date: 2020-01-10 00:00:00 -0000
---

### 목차

* [C방식 오류 처리의 단점](#C방식-오류-처리의-단점)
* [예외와 클래스](#예외와-클래스)
* [noexcept](#noexcept)
* [](#)
* [](#)

---

### C방식 오류 처리의 단점

C 방식의 오류 처리 단점

1. 반환 값과 실패를 나타내는 거싱 명확히 분리되어 있지 않음
2. 정상적인 실행흐름과 오류처리의 코드가 분리되어 있지 않음
3. (개발자의 실수로) 오류를 무시할 수 있다.

=> 예외(exception)의 탄생

```cpp
// 기존의 C문법
#include <iostream>

int readFile()
{
    FILE* f = fopen("a.txt", "rt");
    
    if( f == 0 )
        // return -1;
        throw "FileNotFound";
    // ...
    fclose(f);
    return 0;
}

int main()
{
    try
    {
        int ret = readFile();
        // ...
    }
    catch( const char* s )
    {
        std::cout << s << std::endl;    // FileNotFound 출력
    }
    catch( int n )    // 이런식으로 다 잡을 수 있음.
    {
    }
    catch( ... )      
    // 가변인자로 어떠한 인자라도 잡음(제일 위에 있으면 불안스)
    {
    }
    
    /*    // C문법
    if( ret == -1 )
    {
        // 실패
    }
    */
}
```

### 예외와 클래스

> 예외에 더 많은 정보를 담기 위해서는 클래스를 넘기는게 가장 좋다.
> 
> 또한 되도록 std::exception으로 상속 받아서 만들면 더 좋다!

```cpp
#include <iostream>

class FileNotFound : public std::exception
{
public:
    virtual const char* what() const noexcept // noexcept 에 대한 설명은 아래에서..
    {
        return "File not Found";
    }
};

void foo()
{
     throw FileNotFound();
}

int main()
{
    try
    {
        foo();
    }
    // catch(FileNotFound e)
    catch(std::exception& e)   // 좀 더 다양하게 받을 수 있게 처리
    // 참조형으로 받는 이유는 그냥 받으면 복사본을 출력하게 됨(주의!!)
    {
        std::cout << e.what() << std::endl;
    }
}
```

---

### noexcept

> 함수가 예외가 없음(있음)을 표기하는 방법

![](/file/image/cpp-exception-image-01.png)

> 예외는 왜 표기하나?
> 
> 1. 예외가 없는 함수가 컴파일러 최적화가 더 잘 된다.
> 2. 예외가 있는지 없는지 조사후에 다른 알고리즘을 사용할 수 있다.

```cpp
void foo()  // 예외가 있다.
void foo() noexcept(false) // 예외가 있다.
void foo() noexcept // 예외가 없다.
{

}

int main()
{
    try
    {
        foo();
    }
    catch( ... )
    {
        
    }
}
```

```cpp
#include <iostream>

void foo()
{
}

int main()
{
    bool b = noexept( foo() );
    
    std::cout << b << std::endl;
}
```