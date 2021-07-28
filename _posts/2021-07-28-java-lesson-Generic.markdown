---
layout: post
title:  "[Java] 강의 Generic"
subtitle:   "Generic"
categories: programming-language
tags: java
---

## Generic

- object 형태로 배열을 생성하면 다양한 객체를 배열에 담을 수 있다.
	- 추가할때는 편하지만, 사용할 때는 타입 체크 및 변환을 해야 되기 때문에 번거롭다.
	- 배열을 사용시 하나의 객체만 사용하는 경우가 많다.

- Generic
	-  `<T>`의미 : 클래스에서 Generic 타입을 사용할 것이다.


## Generic 사용안하는 코드

```java
package generic;

public class Test {
	public static void main(String[] args) {
		StringContainer sc1 = new StringContainer();
		sc1.setObj("String");
		
		// error
		// The method setObj(String) in the type StringContainer is not applicable for the arguments (Integer)
		sc1.setObj(new Integer(123));
				
	}
}

```

```java
package generic;


public class StringContainer {
	
	private String obj;
	
	public String getObj() {
		return obj;
	}
	
	public void setObj(String obj) {
		this.obj = obj;
	}

}
```

## Generic 사용

```java
package generic;

public class Test {
	public static void main(String[] args) {
		
		GenericContainer<String> gc1 = new GenericContainer<String>();
		gc1.setObj("String");
		
		GenericContainer<Integer> gc2 = new GenericContainer<>(); 		//생략가능
		gc2.setObj(new Integer(1234));
		
	}
}
```

`<T>`의미 : 클래스에서 Generic 타입을 사용할 것이다.

```java
package generic;

public class GenericContainer<T> {
	
	private T obj;
	
	public T getObj() {
		return obj;
	}
	
	public void setObj(T obj) {
		this.obj = obj;
	}

}
```
w