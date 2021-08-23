---
layout: post
title:  "c++  레퍼런스 ~ 클래스   "
---

**레퍼런스

레퍼런스 : 다른 대상을 참조하게 만들어주는 기능이다.
          참조를 하게 되면 그 대상에 접근하여 값을 변경할 수 있다.
          단 레퍼런스는 처음 레퍼런스 변수 생성시 참조 대상을 지정해야한다.
          변수타입 &레퍼련스 = 변수명


```C++
#include <iostream>
using namespace std;

int main()
{
        int iNumber = 100;
    int iNumber1 = 9999;
    int& iRefNum = iNumber;

    iRefNum = 1234;

    iRefNum = iNumber1;

    cout << iNumber << endl;
    cout << sizeof(iRefNum) << endl;

    return 0;
}
```

**클래스 

객체 (object) : 모든 사물을 의미한다. 각 변수들도 객체로 취급할 수도 있다. 하지만 객체지향 프로그래밍을 지원하기 위해 제공되는 수단은 class이다.
                class는 객체가 아니라 객체를 찍어내는 틀이다.
객체지향 프로그램 (oop) : 객체들의 관계를 설정하여 부품을 조립하듯 객체들을 조립하여 완성된 프로그램을 만들어 나가는 방식이다. 

클래스 선언방법 : class 클래스명 {}; 의 형태
코드블럭안에 맴버변수를 넣을 수 있고 함수도 멤버로 만들수 있다. 
클래스의 4가지 속성
1.캡슐화 : 클래스 안에 속하는 여러 변수 ,함수를 하나의 클래스로 묶는 기능  
2.은닉화 : 쿨랴수 안에 속하는 여러 변수 ,함수를 내가 원하는 부분만 공개하거나 숨길 수 있다.
    -public : 클래스 내부 외부 다공개 
    -protected : 클래스 내부 + 자식 클래스 내부에서 공구 
    -private : 클래스 내부에서만 공개, default 값으로 private 사용
3.상속성 : 클래스만에 부모 자식관계를 형성 할 수 있다.   
4.다형성 : 부모 자식 관계가 형성된 클래스간에 서로 형변환 이 가능한 성질

**생성자와 소멸자
생성자 : 어떤 클래스를 이용해서 객체를 생성할때 자동으로 호출되는 함수 이다. 객체 생성시 호출되는 함수이기 때문에 객체의 맴버를 초기화 할때 유용하다.
         생성자를 만들어 주지 않을경우 내부적으로 기본 생성자가 제공되어서 기본 생성자를 자동으로 호출하게 된다.
클래스명()
{
}
의 형태

소멸자 : 클래스를 이용하여 생성한 객체가 메모리에서 해지될때 자동으로 호출되는 함수 ,객체를 사용하고 난 뒤 마무리 작업을 할때 유용하게 사용할 수 있다.

-클래스명 ()
{
}
```c++

#include <iostream>

using namespace std;


class CTracer
{
public:
	CTracer()
	{
		cout << "생성자 " << endl;
		strcpy_s(m_strName, "트레이서");
	}
	CTracer(const char* pName)
	{
		strcpy_s(m_strName, pName);
	}
	CTracer(const char* pName, int iFlash, int iBack):
		m_iBack(iBack)
	{
		strcpy_s(m_strName, pName);
		m_iFlash = iFlash;
		cout << "Name , Flash , Back 생성자" << endl;
		
	}
	~CTracer()
	{
		cout << "소멸자" << endl;
	}
	char	m_strName[32];

public:
	int		m_iAttack;
	int		m_iHP;

private:
	int		m_iFlash;

private:
	int		m_iBack;

public:
	void Output()
	{
		cout << " Tracer Output" << endl;
		cout << "NAME:" << m_strName << endl;
	}

};

int main()
{
	CTracer tr1("한조", 3, 1);
	

	//tr1.m 퍼블릭 키워드만 접근 가능
	// 오버로딩 인자의갯수 또는 타입이 다를때 사용이 가능하다.
	
	tr1.Output();

	return 0;

}

```
