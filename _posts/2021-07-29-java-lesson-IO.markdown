---
layout: post
title:  "[Java] 강의 IO"
subtitle:   "강의요약"
categories: programming-language
tags: java
---

## java.util.Scanner

[Java8 Docs](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)

```
compact1, compact2, compact3
java.util
Class Scanner

java.lang.Object
	java.util.Scanner

All Implemented Interfaces:
Closeable, AutoCloseable, Iterator<String>
```

```java
public final class Scanner 
extends Object
implements Iterator<String>, Closeable
```



Class BufferedOutputStream

Class BufferedInputStream

Class BufferedReader

Class BufferedWriter

Class OutputStreamWriter

Class FileWriter


https://stackoverflow.com/questions/2231369/scanner-vs-bufferedreader


## Scanner와 BufferedReader의 차이점
- `BufferedReader는 동기식` 이지만, Scanner는 아님. `다중 스레드`로 작업하는 경우 `BufferedReader를 사용`해야 함
- BufferedReader는 Scanner보다 훨씬 더 큰 버퍼 메모리를 가지고 있음
- `BufferedReader (8KB byte buffer)`
- `Scanner (1KB char buffer)`
- Scanner가 입력 데이터를 `구문 분석`하고, 
- BufferedReader는 `단순히 문자 시퀀스`를 읽기 때문에 스캐너에 비해 조금 더 빠름



### InputStreamReader

- 한 글자씩 문자열을 읽어들이는 InputStreamReader의 경우 길이가 긴 문자열을 읽어 들일 때 상당히 불편하고 비효율적입니다.
- 이 점을 보완하고자 BufferedReader가 존재합니다.
- BufferedReader는 InputStreamReader에 버퍼링 기능이 추가된 Class입니다.
- 사용자가 요청할 때마다 데이터를 읽어 오는 것이 아닌 일정한 크기의 데이터를 한번에 읽어와 버퍼에 보관 한 후, 사용자의 요청이 있을 때 버퍼에서 데이터를 읽어오는 방식으로 동작합니다.
- https://carpediem0212.tistory.com/11


## Class BufferedWriter

[Java8 Docs](https://docs.oracle.com/javase/8/docs/api/java/io/BufferedWriter.html)


	
```java
java.lang.Object
	java.io.Writer
		java.io.BufferedWriter
```

`All Implemented Interfaces`
```java
Closeable, Flushable, Appendable, AutoCloseable
```

## Class OutputStreamWriter

[Java8 Docs](https://docs.oracle.com/javase/8/docs/api/java/io/OutputStreamWriter.html)

```java
java.lang.Object
	java.io.Writer
		java.io.OutputStreamWriter
```

`All Implemented Interfaces`
```java
Closeable, Flushable, Appendable, AutoCloseable
```


## Class FileOutputStream

[Java8 Docs](https://docs.oracle.com/javase/8/docs/api/java/io/FileOutputStream.html)

```java
java.lang.Object
	java.io.OutputStream
		java.io.FileOutputStream
```

`All Implemented Interfaces`
```java
Closeable, Flushable, AutoCloseable
```