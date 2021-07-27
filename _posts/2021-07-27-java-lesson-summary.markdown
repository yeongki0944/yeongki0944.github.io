---
layout: post
title:  "[Java] 강의 요약"
subtitle:   "강의요약"
categories: programming-language
tags: java
---
## Java - 인터페이스
- 인터페이스
	- 인터페이스
	- 구현
- 싱글톤 디자인패턴
	- 다중 인터페이스로 구현시 getInstance 부분이 복잡해져야 된다 -> 디자인 패턴으로 확장


## Exception
- Java언어의 특징
	- 여러 디바이스에서 동작 가능한 프로그램 / 자바의 철학 중 하나
		- 예측 가능한 상황에 대해서 선제적으로 대응(JVM이 대응하도록)	- 네트워크를 기반으로 제작했음
		- java.io / java.net이 주요 API였음.
		- 예측가능한 상황은 API에 최대한 구현함.
		- 예측불가능한 것은 RuntimeException

## Error vs Exception 
- Error : 예측 불가능 / JVM이나 코드를 수정
- Exception : 예측 가능 / 컴파일러가 예측가능한 상황

## FileNotFoundException
[FileNotFoundException API Docs](https://docs.oracle.com/javase/8/docs/api/java/io/FileNotFoundException.html)

```java
java.lang.Object
	java.lang.Throwable
		java.lang.Exception
			java.io.IOException
				java.io.FileNotFoundException
```


## RuntimeException

[RuntimeException API Docs](https://docs.oracle.com/javase/8/docs/api/java/lang/RuntimeException.html)

```java
java.lang.Object
	java.lang.Throwable
		java.lang.Exception
			java.lang.RuntimeException
```
- RuntimeException의 하위 Exception이 아닌것을 골라라. 
- RuntimeException이 발생할 경우 try-catch로 잡을 수 있지만, 코드를 고쳐야 된다.

## throws Exception

```java
package Exception;

import java.io.FileInputStream;

public class ExceptionTest {
	
	// #1 throws Exception 호출한 쪽으로 위임 
	public static void main(String[] args) throws Exception {
		FileInputStream fis = new FileInputStream("input.txt");
		
	}
}
```


## try-catch-finally 
- 실무 프로젝트시 로깅을 해야 된다. 
- 로그파일은 누구 책임인지 분별하기 위해서 사용

```java
package Exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class ExceptionTest {
	
	public static void main(String[] args) {
		
		// #2 try-catch-finally => 내가 처리
		try {
			// 예외가 발생 할 수 있는 코드
			FileInputStream fis = new FileInputStream("input.txt");
		} catch (FileNotFoundException e) {
			// 발생된 예외를 처리
			// TODO: handle exception

			// 로깅
			e.printStackTrace();
			
			//inform - 로그 발생을 알리는 코드
			
			//멈출 것인가? 계속 무언가를 진행 할 것인가?
			
		}finally {	
			// 예와가 발생하든, 안하든 반드시 실행되어야 하는 코드 (ex. 자원반납 - close() )
			
		}
		
		
	}
}
```

## try-finally 코드
- 아래 코드는 예외 발생 
	- Unhandled exception type FileNotFoundException

```java
package Exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class ExceptionTest {
	
	public static void main(String[] args) {
		
		// #2 try-catch-finally => 내가 처리
		try {
			// 예외가 발생 할 수 있는 코드
			FileInputStream fis = new FileInputStream("input.txt");
		} finally {	
			// 예와가 발생하든, 안하든 반드시 실행되어야 하는 코드 (ex. 자원반납 - close() )
			
		}
		
		
	}
}
```

- Runtime Exception이 발생시 try-fianlly로 코드 작성 가능

```java
package Exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class ExceptionTest {
	
	public static void main(String[] args) {
		
		// #2 try-catch-finally => 내가 처리
		try {
			// 예외가 발생 할 수 있는 코드
			// 런타임 에러 발생할 수 있는 코드
		} finally {	
			// 예와가 발생하든, 안하든 반드시 실행되어야 하는 코드 (ex. 자원반납 - close() )
			
		}
		
		
	}
}

```
## throw new 

```java
package Exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class ExceptionTest {
	
	public static void main(String[] args) throws FileNotFoundException {
		
		// #2 try-catch-finally => 내가 처리
		try {
			// 예외가 발생 할 수 있는 코드
			FileInputStream fis = new FileInputStream("input.txt");
		} catch (FileNotFoundException e) {
			// 발생된 예외를 처리
			// TODO: handle exception

			// 로깅
			e.printStackTrace();
			
			//inform 
						
			throw new FileNotFoundException();
			
		}finally {	
			
		}
		
		
	}
}
```

- Unhandled exception type FileNotFoundException 
	- main에서 throws FileNotFoundException을 선언하지 않아서 발생하는 오류 메시지
	- Add thorws declaration



## Exception 여러개 다루기

```java
package Exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class ExceptionTest {
	
	public static void main(String[] args) throws FileNotFoundException, ClassNotFoundException  {
		
		// #2 try-catch-finally => 내가 처리
		try {
			// 예외가 발생 할 수 있는 코드
			FileInputStream fis = new FileInputStream("input.txt");
			Class.forName("abc");
		} catch (FileNotFoundException e) {
			e.printStackTrace();
			throw new FileNotFoundException();
		} catch(ClassNotFoundException e) {
			e.printStackTrace();
			throw new ClassNotFoundException();
		} catch(Exception e) {
			e.printStackTrace();
		}finally {	
			
		}
		
		
	}
}
```

- 아래 처럼 코드 작성시 에러가 발생함. 
	- Unreachable catch block for FileNotFoundException. It is already handled by the catch block for Exception
	- Exception이 모든 예외를 받을 수 있음.
	- equals 구현시 instaceof object 하면 다 걸리는 것과 유사한 개념.


```java
package Exception;

import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class ExceptionTest {
	
	public static void main(String[] args) throws FileNotFoundException, ClassNotFoundException  {
		
		// #2 try-catch-finally => 내가 처리
		try {
			// 예외가 발생 할 수 있는 코드
			FileInputStream fis = new FileInputStream("input.txt");
			Class.forName("abc");
		} catch(Exception e) {
			e.printStackTrace();
		} catch (FileNotFoundException e) {
			e.printStackTrace();
			throw new FileNotFoundException();
		} catch(ClassNotFoundException e) {
			e.printStackTrace();
			throw new ClassNotFoundException();
		} finally {	
			
		}
		
		
	}
}
```