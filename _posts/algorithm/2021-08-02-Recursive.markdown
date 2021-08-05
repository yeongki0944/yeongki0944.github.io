---
layout: post
title:  "Recursive 기초"
subtitle:   "Recursive 기초"
categories: algorithm
tags: recursive
---


## Base case

`Base case` - 재귀가 멈추는 조건 



## Recursive - Base case가 없는 경우

* Exception in thread "main" `java.lang.StackOverflowError`

```java
public class BASIC_RecursiveCall {
	
	public static void main(String[] args) {
		m1();
	}
	
	static void m1() {
		System.out.println("m1");
		m1();
	}
}
```


## Recursive - Base case 위치가 잘못 된 경우

```java
public class BASIC_RecursiveCall {
	
	public static void main(String[] args) {
		m2();
	}

	static int m2_count = 5;
	
	static void m2() {
		System.out.println("앞 m2_count = " + m2_count);
		
		if( m2_count > 0 ) {
			m2_count--;
			m2();
		}
		
		System.out.println("뒤 m2_count = " + m2_count);
	}
}

```

`실행결과`

```
앞 m2_count = 5
앞 m2_count = 4
앞 m2_count = 3
앞 m2_count = 2
앞 m2_count = 1
앞 m2_count = 0
뒤 m2_count = 0
뒤 m2_count = 0
뒤 m2_count = 0
뒤 m2_count = 0
뒤 m2_count = 0
뒤 m2_count = 0
```

## Recursive - Base case 전에 코드가 실행 될 경우

```java
public class BASIC_RecursiveCall3 {
	
	public static void main(String[] args) {
		m3();
	}

	static int m3_count = 5;
	
	static void m3() {
		
		System.out.println("앞 m3_count = " + m3_count);
		
		if(m3_count == 0) return;

		m3_count--;
		m3();
		
		System.out.println("뒤 m3_count = " + m3_count);
	}
}
```

`실행결과`

```
앞 m3_count = 5
앞 m3_count = 4
앞 m3_count = 3
앞 m3_count = 2
앞 m3_count = 1
앞 m3_count = 0
뒤 m3_count = 0
뒤 m3_count = 0
뒤 m3_count = 0
뒤 m3_count = 0
뒤 m3_count = 0
```

## Recusive - Base case가 맨 앞에 있는 경우

```java
public class BASIC_RecursiveCall4 {
	
	public static void main(String[] args) {
		m4();
	}

	static int m4_count = 5;
	
	static void m4() {
		
		if(m4_count == 0) return;
		
		System.out.println("앞 m4_count = " + m4_count);
		

		m4_count--;
		m4();
		
		System.out.println("뒤 m4_count = " + m4_count);
	}
}
```

`실행결과`

```
앞 m4_count = 5
앞 m4_count = 4
앞 m4_count = 3
앞 m4_count = 2
앞 m4_count = 1
뒤 m4_count = 0
뒤 m4_count = 0
뒤 m4_count = 0
뒤 m4_count = 0
뒤 m4_count = 0

```


## Recusive - Base case 이후 값을 사용할 경우 

```java
public class BASIC_RecursiveCall5 {
	
	public static void main(String[] args) {
		m5();
	}

	static int m5_count = 5;
	
	static void m5() {
		
		if(m5_count == 0) return;
		
		System.out.println("앞 m5_count = " + m5_count);
		

		m5_count--;
		m5();
		m5_count++;
		
		System.out.println("뒤 m5_count = " + m5_count);
	}
}
```

`실행결과`

```
앞 m5_count = 5
앞 m5_count = 4
앞 m5_count = 3
앞 m5_count = 2
앞 m5_count = 1
뒤 m5_count = 1
뒤 m5_count = 2
뒤 m5_count = 3
뒤 m5_count = 4
뒤 m5_count = 5
```


## Recusive - Base case 파라미터

```java
public class BASIC_RecursiveCall_Parameter {
	
	public static void main(String[] args) {
		p1(5);
	}

	
	static void p1( int p1_count ) {
		
		if(p1_count == 0) return;
		
		System.out.println("앞 p1_count = " + p1_count);
		

		p1(p1_count - 1);
		
		
		System.out.println("뒤 p1_count = " + p1_count);
	}
}

```

`실행결과`

```
앞 p1_count = 5
앞 p1_count = 4
앞 p1_count = 3
앞 p1_count = 2
앞 p1_count = 1
뒤 p1_count = 1
뒤 p1_count = 2
뒤 p1_count = 3
뒤 p1_count = 4
뒤 p1_count = 5
```


## Recusive - Base case 파라미터 with 전,후위 연산자


### 후위연산자

`p1(p1_count--);` - Stack Overflow 발생


```java
public class BASIC_RecursiveCall_Parameter {
	
	public static void main(String[] args) {
		p1(5);
	}

	
	static void p1( int p1_count ) {
		
		if(p1_count == 0) return;
		
		System.out.println("앞 p1_count = " + p1_count);
		

		p1(p1_count--);
		
		
		System.out.println("뒤 p1_count = " + p1_count);
	}
}
```


### 전위연산자

`base 조건이 한번 실행됨` 

```java
public class BASIC_RecursiveCall_Parameter {
	
	public static void main(String[] args) {
		p1(5);
	}

	
	static void p1( int p1_count ) {
		
		if(p1_count == 0) return;
		
		System.out.println("앞 p1_count = " + p1_count);
		

		p1(--p1_count);
		
		
		System.out.println("뒤 p1_count = " + p1_count);
	}
}
```

`실행결과`

```
앞 p1_count = 5
앞 p1_count = 4
앞 p1_count = 3
앞 p1_count = 2
앞 p1_count = 1
뒤 p1_count = 0
뒤 p1_count = 1
뒤 p1_count = 2
뒤 p1_count = 3
뒤 p1_count = 4
```







