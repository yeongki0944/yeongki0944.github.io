---
layout: post
title:  "[Java] 강의 람다"
subtitle:   "람다"
categories: programming-language
tags: java
---

- A 인터페이스가 있음 
	- method가 하나만 있음
	- Functional Interface


## 개념
### `Funtinal Interface`
`Funtional Interface` 만들기

```java
package lamda;

@FunctionalInterface
public interface MyFuncIF {
	int calc(int i, int j);
	
}
```

`error` - Invalid '@FunctionalInterface' annotation; MyFuncIF is not a functional interface

```java
package lamda;

@FunctionalInterface
public interface MyFuncIF {
	int calc(int i, int j);
	
	int add(int i, int j);
}
```



## lamda를 사용안할 경우

### `interface`

```java
package lamda;

@FunctionalInterface
public interface MyFuncIF {
	int calc(int i, int j);
}
```

### `implements`


```java
package lamda;

public class MyFuncIFImpl implements MyFuncIF{
	@Override
	public int calc(int i, int j) {
		// TODO Auto-generated method stub
		return i + j;
	}
}
```

### `main`

#### 1. new로 impl한 클래스 생성
#### 2. anonymous class

```java
package lamda;

public class MyFuncIFTest {
	public static void main(String[] args) {
		int a = 10;
		int b = 20;
		
		{
			MyFuncIF obj = new MyFuncIFImpl();
			int result = obj.calc(a, b);
			System.out.println(result);
		}
		
		// anonymous class 객체 사용
		{
			MyFuncIF obj = new MyFuncIF(){

				@Override
				public int calc(int i, int j) {
					// TODO Auto-generated method stub
					return i + j;
				}		
			
			};
			int result = obj.calc(a, b);
			System.out.println(result);
		}
	}
}
```

## lamda 사용할 경우 

```java
package lamda;

public class MyFuncIFTest {
	public static void main(String[] args) {
		int a = 10;
		int b = 20;
		
		//lamda
		{
			MyFuncIF obj = (i, j) -> i + j;
			
			int result = obj.calc(a, b);
			System.out.println(result);
		}
	}
}
```

- 람다를 사용할 수 있는 이유 
	- 인터페이스에 method가 오직 하나있기 때문에 가능


## 파라미터가 Funtional Interface 인경우

- `파라미터로 lamda`를 넘길 수 있음.

```java
package lamda;

@FunctionalInterface
public interface MyFuncIF {
	int calc(int i, int j);
}
```

```java
package lamda;

public class MyFuncIFTest {
	public static void main(String[] args) {
		int a = 10;
		int b = 20;
		
		// lamda parameter
		{
			// 파라미터가 Funtinal Interface 이면 / lamda를 파라미터로 넘길 수 있다.
			MyFunc.m( (i,j) -> i+j);
			MyFunc.m( (i,j) -> i-j);
		}
	}
}


class MyFunc{
	static void m(MyFuncIF p) {
		System.out.println(p.calc(5, 7));
	}
}
```



## lamda 응용 - Collection과 함께 사용


### `Colections - Comparable 인터페이스`

### 1. `Interface Overriding`

```java
package lamda;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class Test {

	public static void main(String[] args) {

		List<Node> nodeList = new ArrayList<Node>();
		nodeList.add(new Node(1, 3));
		nodeList.add(new Node(5, 2));
		nodeList.add(new Node(2, 4));
		
		for (Node node : nodeList) {
			System.out.println(node.toString());
		}
		System.out.println();		

		Collections.sort(nodeList);
		
		for (Node node : nodeList) {
			System.out.println(node.toString());
		}

	}

}


class Node implements Comparable<Node>{
	int x;
	int y;
	
	Node(int y, int x){
		this.y = y;
		this.x = x;
	}
	@Override
	public String toString() {
		// TODO Auto-generated method stub
		return  "Node [y=" + y+" ,x="+x+"]";
	}
	
	
	@Override
	public int compareTo(Node o) {
		// TODO Auto-generated method stub
		// 
		return this.y - o.y;
	}
}
```

### 2. `anonymous class`


```java
package lamda;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class Test {

	public static void main(String[] args) {
		
		
		List<Node> nodeList = new ArrayList<Node>();
		nodeList.add(new Node(1, 3));
		nodeList.add(new Node(5, 2));
		nodeList.add(new Node(2, 4));
		
		for (Node node : nodeList) {
			System.out.println(node.toString());
		}
		System.out.println();

		// Comparator - Functional Interface 
		
		Collections.sort(nodeList, new Comparator<Node>() {
			@Override
			public int compare(Node o1, Node o2) {
				// TODO Auto-generated method stub
				return o1.y - o2.y;
			}
		});
		
		
		for (Node node : nodeList) {
			System.out.println(node.toString());
		}

	}

}


class Node {
	int x;
	int y;
	
	Node(int y, int x){
		this.y = y;
		this.x = x;
	}
	@Override
	public String toString() {
		// TODO Auto-generated method stub
		return  "Node [y=" + y+" ,x="+x+"]";
	}

}

```


### 3. `lamda`

```java
package lamda;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class Test {

	public static void main(String[] args) {
		
		
		List<Node> nodeList = new ArrayList<Node>();
		nodeList.add(new Node(1, 3));
		nodeList.add(new Node(5, 2));
		nodeList.add(new Node(2, 4));
		
		for (Node node : nodeList) {
			System.out.println(node.toString());
		}
		System.out.println();


		// 3. lamda 표현식
		Collections.sort(nodeList, (n1, n2) -> n1.x - n2.x);
		
		for (Node node : nodeList) {
			System.out.println(node.toString());
		}

	}

}


class Node {
	int x;
	int y;
	
	Node(int y, int x){
		this.y = y;
		this.x = x;
	}
	@Override
	public String toString() {
		// TODO Auto-generated method stub
		return  "Node [y=" + y+" ,x="+x+"]";
	}

}

```
