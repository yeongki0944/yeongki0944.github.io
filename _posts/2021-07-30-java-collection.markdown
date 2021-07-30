---
layout: post
title:  "[Java] Collection"
subtitle:   "java collection"
categories: programming-language
tags: java
---

## Collection - ArrayList 순회 

### for

```java
package collections;

import java.util.ArrayList;
import java.util.Iterator;

public class TraverseTest {

	public static void main(String[] args) {
		ArrayList<String> arrayList = new ArrayList<String>();
		
		arrayList.add("손흥민");
		arrayList.add("이강민");
		arrayList.add("이강민");		// ArrayList는 중복 가능
		arrayList.add("이승우");
		
		
		// for
		for (int i = 0; i < arrayList.size(); i++) {
			String s = arrayList.get(i);
			System.out.println(s);
		}
		
		// forEach
		for (String string : arrayList) {
			System.out.println(string);
		}
		
	}
}
```

### Iterator

`Iterator<String> itr = arrayList.iterator();`

`itr.hasnext()` 	- 다음 값이 있으면 True / 없으면 False

`itr.next()` 		- 다음 값의 레퍼런스 값을 반환


```java
package collections;

import java.util.ArrayList;
import java.util.Iterator;

public class TraverseTest {

	public static void main(String[] args) {
		ArrayList<String> arrayList = new ArrayList<String>();
		
		arrayList.add("손흥민");
		arrayList.add("이강민");
		arrayList.add("이강민");		// ArrayList는 중복 가능
		arrayList.add("이승우");
		
		// Iterator 
		Iterator<String> itr = arrayList.iterator();
		
		while( itr.hasNext() ) {
			String s = itr.next();
			System.out.println(s);
		}
	}
}
```


### forEach() 

```java
package collections;

import java.util.ArrayList;
import java.util.Iterator;

public class TraverseTest {

	public static void main(String[] args) {
		ArrayList<String> arrayList = new ArrayList<String>();
		
		arrayList.add("손흥민");
		arrayList.add("이강민");
		arrayList.add("이강민");		// ArrayList는 중복 가능
		arrayList.add("이승우");
		
		
		// forEach
		arrayList.forEach( s -> System.out.println(s));
		
		
	}
}
```


### 메소드 레퍼런스 

`메소드 레퍼런스` - 람다 처럼 funtional interface에만 적용가능한 것. 

```java
package collections;

import java.util.ArrayList;
import java.util.Iterator;

public class TraverseTest {

	public static void main(String[] args) {
		ArrayList<String> arrayList = new ArrayList<String>();
		
		arrayList.add("손흥민");
		arrayList.add("이강민");
		arrayList.add("이강민");		// ArrayList는 중복 가능
		arrayList.add("이승우");
		
		
		// 메소드 레퍼런스 - 람다 처럼 funtional interface에만 적용가능한 것. 
		// 떠블 컬럼 오퍼레이터 
		arrayList.forEach( System.out::println );
		
	}
}
```
---

## Collection - ArrayList 삭제


### Arrays.asList

`immutable` 변경불가 

```java
package collections;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class TraverseRemoveTest {

	public static void main(String[] args) {
		// mutable - 변경가능
		ArrayList<String> arrayList = new ArrayList<String>();
		arrayList.add("손흥민");
		arrayList.add("이강민");
		arrayList.add("이강민");		// ArrayList는 중복 가능
		arrayList.add("이승우");
		
		
		// immutable - 변경불가
		List<String> list = Arrays.asList("손흥민", "이강민", "이승우", "이강민");

	}
}
```



### ArrayList - Remove By for

```java
package collections;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class TraverseRemoveTest {

	public static void main(String[] args) {
		// mutable - 변경가능 
		ArrayList<String> arrayList = new ArrayList<String>();
		arrayList.add("손흥민");
		arrayList.add("이승우");
		arrayList.add("이강인");		// ArrayList는 중복 가능
		arrayList.add("이강인");
		
		for (int i = 0; i < arrayList.size(); i++) {
			String s = arrayList.get(i);
			if( s.equals("이강인")) arrayList.remove(i);
		}
		
		for (String string : arrayList) {
			System.out.println(string);
		}
	}
}
```

`문제점` -  이강인이 모두 삭제 되지 않는다. 

`해결방법` - 뒤에서부터 삭제

```java
package collections;

import java.util.ArrayList;

public class TraverseRemoveTest {

	public static void main(String[] args) {
		// mutable - 변경가능 
		ArrayList<String> arrayList = new ArrayList<String>();
		arrayList.add("손흥민");
		arrayList.add("이승우");
		arrayList.add("이강인");		// ArrayList는 중복 가능
		arrayList.add("이강인");
		
		for (int i = arrayList.size()-1; i >= 0; i--) {
			String s = arrayList.get(i);
			if( s.equals("이강인")) arrayList.remove(i);
		}
		
		for (String string : arrayList) {
			System.out.println(string);
		}
	}
}
```

### ArrayList - Remove By forEach 

```java
package collections;

import java.util.ArrayList;

public class TraverseRemoveTest {

	public static void main(String[] args) {
		// mutable - 변경가능 
		ArrayList<String> arrayList = new ArrayList<String>();
		arrayList.add("손흥민");
		arrayList.add("이승우");
		arrayList.add("이강인");		
		
		for (String string : arrayList) {
			if( string.equals("이강인")) arrayList.remove(string);
		}
		
		for (String string : arrayList) {
			System.out.println(string);
		}
	}
}
```

`error` 발생 

```
Exception in thread "main" java.util.ConcurrentModificationException
	at java.util.ArrayList$Itr.checkForComodification(ArrayList.java:909)
	at java.util.ArrayList$Itr.next(ArrayList.java:859)
	at collections.TraverseRemoveTest.main(TraverseRemoveTest.java:14)

```

forEach문은 `ReadOnly` - forEach문으로 `삭제는 불가능`  /  `변경은 가능` 



### ArrayList - Remove By Iterator 

`iterator`는 `삭제 가능`

```java
package collections;

import java.util.ArrayList;
import java.util.Iterator;

public class TraverseRemoveTest {

	public static void main(String[] args) {
		// mutable - 변경가능 
		ArrayList<String> arrayList = new ArrayList<String>();
		arrayList.add("손흥민");
		arrayList.add("이승우");
		arrayList.add("이강인");		
		
		Iterator<String> itr = arrayList.iterator();
		
		while( itr.hasNext() ) {
			String s = itr.next();
			if(s.equals("이강인")) itr.remove();
		}
		
		System.out.println(arrayList);
	}
}
```

### ArrayList - Remove By removeIf() & lamda

`ArrayList`의 `removeIf()`에 `lamda`를 적용

```java
package collections;

import java.util.ArrayList;
import java.util.Iterator;

public class TraverseRemoveTest {

	public static void main(String[] args) {
		// mutable - 변경가능 
		ArrayList<String> arrayList = new ArrayList<String>();
		arrayList.add("손흥민");
		arrayList.add("이승우");
		arrayList.add("이강인");		
		
		arrayList.removeIf( s -> s.equals("이강인")); 
		
		System.out.println(arrayList);
		
		
	}
} 
```


