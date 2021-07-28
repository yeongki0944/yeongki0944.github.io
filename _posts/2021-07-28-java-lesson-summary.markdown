---
layout: post
title:  "[Java] 강의 디자인 패턴"
subtitle:   "강의요약"
categories: programming-language
tags: java
---
## 디자인패턴

### factory 패턴

**인터페이스**

```java
package design.factory;

public interface Transportation {
	void move();
}
```

**implements**

```java
package design.factory;

public class AirPlane implements Transportation{

	@Override
	public void move() {
		// TODO Auto-generated method stub
		System.out.println("move Car");
	}
	
}
```
```java
package design.factory;

public class Car implements Transportation{

	@Override
	public void move() {
		// TODO Auto-generated method stub
		System.out.println("move AirPlane");
	}
	
}
```

**factory 디자인 패턴**
- 인터페이스를 사용하는 `클래스가 여러개` 일 경우
- `객체를 생성`하는 클래스

```java
package design.factory;


// 대신 객체를 생성해주는 역할
// Transportation 인터페이스를 구현한 클래스의 객체를 생성
public class TransportationFactory {

	//static을 붙이면 TransportationFactory 객체를 생성하지 않아도 되고, 싱글톤도 유지된다.
	public static Transportation getTransportation(String clsf) {
		Transportation t = null;
		switch(clsf) {
			case "A" : t = new AirPlane(); break;
			case "C" : t = new Car(); break;
		}
		return t;
	}
	
}
```

#### Factory 디자인 패턴을 사용안 할 때 문제점
- `사용자의 입장`에서 `imp한 클래스 이름과 생성자 규칙`을 알고 있어야 된다.
- 해결방법 
	- `factory` 디자인 패턴 사용

**main**

```java
package design.factory;

public class Test {

	public static void main(String[] args) {
		
		//인터페이스타입   변수명 = new 인터페이스 구현한 클래스();
		Transportation trans = new Car();
		Transportation trans2 = new AirPlane();
		
		// 문제점 - 사용자의 입장에선 인터페이스 - Transportation만 알아도 객체를 생성해서 사용할 수 있어야 되는데
		// imp한 클래스 이름까지 알아야 된다. 
		// 해결방법 - factory 디자인 패턴 
		
		
		// 인터페이스와 factory를 사용하는 방법만 알면 사용가능.
		//TransportationFactory factory = new TransportationFactory();
		Transportation trans3 = TransportationFactory.getTransportation("C");
		
	}
	
}
```



### method chain

- 언제 사용하는가?
	- `단순 연산`을 `반복`해야 되는 경우
	- `Functional Programming`에서 주로 사용하는 개념
- `public 메소드`의 `리턴타입을 자기자신`으로 설정

```java
package design.methodchain.sol;

public class Calculator {

	
	private int first;
	private int secend;
	
	// void 타입을 자기자신으로 바꾼다. 
	public Calculator setFirst(int first) {
		this.first = first;
		return this;
	}
	
	public Calculator setSecend(int secend) {
		this.secend = secend;
		return this;
	}
	
	
	// 비지니스 로직
	public Calculator showAdd() {
		System.out.println(this.first + " + " + this.secend + " = " +(this.first + this.secend));
		return this;
	}
	
	public Calculator showSub() {
		System.out.println(this.first + " - " + this.secend + " = " +(this.first - this.secend));
		return this;
	}
}
```

```java
package design.methodchain.sol;

public class Test {
	public static void main(String[] args) {
		
		// 일반적으로 Class를 만들고 method를 생성하는 방법
		Calculator c = new Calculator();
		c.setFirst(5);
		c.setSecend(6);
		c.showAdd();

		// 단순 연산을 반복해야 되는 경우
		// Functional Programming에서 주로 사용하는 개념
		c.setFirst(5).setSecend(50).showAdd().setFirst(40).showAdd().showSub();
	}
}
```






