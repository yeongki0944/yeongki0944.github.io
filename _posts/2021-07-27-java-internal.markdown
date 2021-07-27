---
layout: post
title:  "[Java Internal] Java Internal"
subtitle:   "java internal"
categories: programming-language
tags: java
---
## JAVA 동작방식


## JVM 구조

[참고중인 사이트](https://thinkground.studio/%EC%9E%90%EB%B0%94-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EA%B5%AC%EC%A1%B0-java-memory-structure/)
### 일반적인 JVM구조
- Class Loader
- Garbage Collector
- Execution Engine
- Runtime Data Area
	- Method Area
	- Heap Area
	- Stack Area
	- PC Register
	- Native Method Stack

### 각 벤더별 JVM구조

### JVM 특징
- JVM은 `스택기반` 가상머신
- `심볼릭 레퍼런스` : 클래스 파일은 JVM이 프로그램을 실행할 때 필요한 API를 Link할 수 있도록 심볼릭 레퍼런스를 가진다.  심볼릭 레퍼런스를 런타임 시점에 메모리 상에서 실제로 존재하는 물리적인 주소로 대체하는 Linking 작업이 일어난다. 심볼릭 레퍼런스는 참조하는 대상의 이름을 지칭하고, 클래스 파일이 JVM에 올라가게 되면 심볼릭 레펀선스는 실제 메모리 주소가 아닌 이름에 맞는 객체의 주소를 찾아서 연결하는 작업을 수행한다. 
 - 기본 자료형을 명확하게 정의함으로써 플랫폼 독립성 보장 : C++은 플랫폼에 따라 int의 크기가 다르다.
- 심볼릭 레퍼런스는 프로그램 실행을 위한 `API를 클래스가 직접 가지는 것이 아닌 이름을 통한 참조값을 이용`해서 실행할 때 메모리 상에서 API를 호출할 수 있도록 이름을 주소로 대체하는 특징을 의미한다.

## 레퍼런스
### JVM책 추천
- [Java Performance Fundamental](http://www.yes24.com/Product/Goods/3577335)
- [The Java® Virtual Machine Specification Java SE 8 Edition](https://docs.oracle.com/javase/specs/jvms/se8/html/)

### JVM과 메모리 관련
- [1장 - Java Virtual Machine](https://www.slipp.net/wiki/pages/viewpage.action?pageId=8880250)
- [Naver D2 - Java Reference와 GC](https://d2.naver.com/helloworld/329631)
- [자바(JAVA) JVM 메모리구조](https://freestrokes.tistory.com/63)
- [[Java] 자바의 동작원리와 JVM Architecture](https://dev-donghwan.tistory.com/6)
- [JVM의 구조와 Java의 실행과정, Garbage Collectoin 동작원리](https://codeinlife.tistory.com/40)
- [JVM 메모리 구조 및 동작원리](https://move02.github.io/articles/2019-06/JVM-%EC%A0%95%EB%A6%AC)
- [자바의 구동 원리와 JVM(Java Virtual Machine)](https://gbsb.tistory.com/2)
- [JVM 구조와 동작 원리](https://doll6777.github.io/android/2020/02/17/about-jvm/)
- [[JAVA/JVM]메모리 구조(부제 :  성능개선을 위한 GC의 활용)(https://stophyun.tistory.com/37)
- [⭐⭐⭐ / [ JAVA ] JAVA의 동작 방식와 JVM 메모리 구조](https://gyubgyub.tistory.com/m/68?category=896977)
- [⭐⭐⭐ / 자바 메모리 구조 (Java Memory Structure)](https://thinkground.studio/%EC%9E%90%EB%B0%94-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EA%B5%AC%EC%A1%B0-java-memory-structure/)
- [⭐ / 자바 메모리 동작 단계](https://pinkcolor.tistory.com/17)
- [⭐ / 자바 가상머신 JVM](https://lkhlkh23.tistory.com/100)
- [⭐⭐⭐ / Naver D2 - JVM Internal](https://d2.naver.com/helloworld/1230)
- [⭐⭐⭐ / [JAVA] JVM 동작원리 및 기본개념](https://steady-snail.tistory.com/67)
- [⭐⭐ / 자바의 메모리 구조 - 1.메소드 영역(Method Area)](https://blog.wanzargen.me/16)

### JAVA언어 관련
- [⭐⭐ / 위키백과 - 자바(프로그래밍 언어)](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4))
- [⭐ / A Quick Look at HotJava](http://www.scoug.com/os24u/2001/hotjava.html)
- [⭐ / Java 웹 아키이브 90년대](https://web.archive.org/web/19990225142530/http://www.java.sun.com/)
- [⭐ / Oak - History of the World Wide Web](https://ei.cs.vt.edu/book/chap1/java_hist.html)


