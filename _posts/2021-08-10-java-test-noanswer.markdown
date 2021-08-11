---
layout: post
title:  "[Java] oop test"
published : false
subtitle:   "oop test"
categories: programming-language
tags: java
---

## 1

```java
/*
 1. 1. test 클래스를 실행시 화면에는 "싸피" 와 "Dog@12af82" 형태로 결과가 출력된다. 
 Dog 클래스의 출력결과를 "자바"로 객체가 가지고 있는 값으로 변경해서 출력하려고 한다. 
 Object에서 제공하는 메서드를 오버라이딩해서 객체를 대표하는 문자열을 출력하도록 변경해야 한다. 
 이 메서드가 무엇인지 적으시오.

 */




```

## 2  

```java

/* 
  2. 다음 코드의 실행결과를 맞추시오
 
 */

public class p02 {
	
	public static void swap(int i, int j, int[] a) {
		int temp = i;
		i = j;
		j = temp;
		
		temp = a[0];
		a[0] = a[1];
		a[1] = temp;
	}
	
	public static void main(String[] args) {
		int i = 10;
		int j = 20;
		int[] a = {i, j};
		swap(i, j, a);
		System.out.println(i + "," + j + "," + a[0] + "," + a[1]);
	}

}

```

## 3 

```java

/* 
 
 3. 다음 코드에 대한 설명으로 맞는 것을 고르시오. 

 */


public class p03 {
	public static void main(String[] args) {
		String name;
		System.out.println("name = " + name);
	}
}

```

## 4

```java
/*
 4. [서술형 이 클래스는 모든 자바 클래스들의 최상위 클래스로, 명시적으로 상속받지 않으면 자동으로 상속된다. 
 이 클래스는 무엇인지, 반드시 패키지명도 포함시켜 적고, 그 클래스가 가지고 있는 메소드 1개 이상 적고, 
 메소드가 가지고 있는 역할을 적으시오.
 
 */

```

## 5

```java

/* 

5. 다음코드의 실행결과를 골라라

 */

class Animal{
	String name = "Animal";
	public void eat() {
		System.out.println("A");
	}
}

class Cat extends Animal{
	String name = "Cat";
	public void eat() {
		System.out.println("B");
	}
}

public class p05 {

	public static void main(String[] args) {
		Animal a = new Cat();
		
		System.out.print(a.name + ", ");
		a.eat();
	}
	
	
}

```

## 6

```java
/*

6. 클래스의 객체를 생성하기 위해서는 클래스 자체의 정보를 메모리에 로딩해야 한다.
이러한 것을 클래스로딩이라고 부른다. 클래스 자체의 정보가 실행시에 로딩되는 메모리 영역을 고르시오.
 
 */
```

## 7 

```java
/*  
  
  7. Parent 클래스를 상속하는 클래스에 메서드 추가시 가능한 코드를 고르시오.
  
  	1. public int method(int a, int b)
	2. private int method(int a, int b)
	3. int method(int a, long b)
	4. public byte method(int a, int b)

 */


```

## 8 

```java
/*
  
  8.다음 코드의 실행결과를 적으시오. 
    
 */
public class p08 {
	public static void main(String[] args) {
		int[][] arr = new int[2][];
		arr[0] = new int[] { 1, 2, 3 };
		arr[1] = arr[0];
		arr[0] = new int[1];
		System.out.print(arr[0][0] + ", ");
		System.out.println(arr[1][1]);
	}
}

```

## 9

```java

/* 
 
  9. 접근제한자 범위가 넓은 것 부터 순서대로 적은 것  
  
 */

```

## 10

```java
/*

다음 Test 클래스의 read를 호출하기 위해 다음과 같이 코드를 작성할 때 밑줄 친 곳에 올 수 없는 것은?
		
*/ 

class Book extends Object{ }
class Magazine extends Book{ }
class ITNews extends Magazine{ }


public class p10 {
	public static void read(Book c) { }
	
	public static void main(String[] args) {
		read(new ITNews());			// 1
		read(new Book());			// 2
		read(new Magazine());		// 3
		read(new Object());			// 4
	}
}

```

## 11 

```java
/* 
 
 11. 다음 코드의 실행 결과를 고르시오.
 
 */
public class p11 {
	
	public static void main(String[] args) {
		String[ ] arr = new String[2];
		arr[1] = "Hello";
		System.out.println( arr[0] + arr[1] );
	}
	
}

```

## 12

```java
/* 

 12. 다음 코드의 실행결과를 작성하시오.
 
 */

class Parent_p12{
	public Parent_p12() {
		System.out.print("A");
	}
	
}

class Child_p12 extends Parent_p12{
	public Child_p12(){
		System.out.print("B");
	}
}


public class p12 {
	public static void main(String[] args) {
		Parent_p12 p  = new Child_p12();
		System.out.println("C");
	}
}

```

## 13

```java
/*  
 
  13. 다음 코드를 수행시 예상되는 결과를 고르시오.
 
 */
public class p13 {
	public static void main(String[] args) {
		int a = 0;
		int b = 1;
		
		if((a++ == 0)||(b++ == 1)) {
			b = 10;
		}
		System.out.println(a + ", " + b);
	}
	
}
```

## 14

```java
/*

 14. 다음 코드의 실행결과를 적으시오.
 
 */

class Parent_p14 {
	void play() {
		this.show();
		System.out.print("Hello ");
	}
	
	void show() {
		System.out.print("SSAFY ");
	}
}

class Child_p14 extends Parent_p14{
	void show() {
		super.show();
		System.out.print("Student ");
	}
}
public class p14 {
	public static void main(String[] args) {
		Parent_p14 c = new Child_p14();
		c.play();
	}
}

```

## 15

```java
/* 

 15. Animal 클래스를 상속받아 Cat 클래스가 구현되어 있을때, 다음 자바 프로그램의 수행결과를 적으시오.
 
 */
class Animal_p15{
	
}

class Cat_p15 extends Animal_p15{
	
}
public class p15 {

	public static void main(String[] args) {
		Animal_p15 a = new Animal_p15();
		Cat_p15 b = new Cat_p15();
		
		if ( a instanceof Animal_p15) System.out.print("A");
		if ( b instanceof Animal_p15) System.out.print("B");
		if ( a instanceof Cat_p15) System.out.print("C");
		if ( b instanceof Cat_p15) System.out.print("D");
	}
}

```

## 16 

```java
/*

 16. 다음 코드의 실행결과를 고르시오.

*/

class Board{
	int no;
	String title;
}

public class p16 {
	public static void main(String[] args) {
		Board[] arr = new Board[2];
		arr[0].no = 1;
		arr[0].title = "A";
		System.out.println(arr[0].no);
		System.out.println(arr[0].title);

	}
}

```

## 17

```java
/* 

 17. 클래스의 상속과 관련된 내용으로 틀린것을 고르시오.
 
 	1) 클래스 간의 상속은 단일상속을 지원한다.
 	2) 클래스 간의 상속시 extends 키워드를 사용한다.
 	3) 상속받은 메서드의 내용을 다시 정의할 수 있다.
 	4) 접근제한자와 상관없이 super 클래스의 모든 것을 이용할 수 있다.

*/

```

## 18

```java
/*
 
 18. 다음 코드의 실행 결과를 고르시오. 
 
 */

public class p18 {
	public static void main(String[] args) {
		int type = 2;
		int b = 0;
		switch(type) {
			case 1:
				b += 1;
			case 2:
				b += 10;
			case 3:
				b += 100;
			default:
				b += 1000;
		}
		
		System.out.println(b);
	}
}

```

## 19 

```java

/* 
 
 19. 다음 코드를 수행시 예상되는 결과를 적으시오. 
 
 */
public class p19 {

	public static void main(String[] args) {
		String data = "Hi";
		data.replace(data.charAt( 1 ), 'e');
		System.out.println( data );
	}
}

```

## 20 

```java
/*

 20. 다음 코드에 대한 설명으로 올바른 것을 고르시오.
 
 
 보기 
  1. Compile 오류가 발생한다.
  2. 실행 오류가 발생한다.
  3. 정상적으로 실행되고 Magazine이 출력된다.
  4. 정상적으로 실행되고 Novel이 출력된다. 
  
*/


class p20 {

	private String category="Magazine";
	public p20(String category) { this.category = category; }
	public void setCategory (String category) { this.category = category; }
	public String getCategory( ) { return category; }
	public static void main(String[] args) {
		p20 e = new p20 ( );
		e.setCategory("Novel");
		System.out.println( e.getCategory() );
	}
	

}

```

## 21

```java

/* 
 
 21. 다음 코드가 한줄씩 실행된다고 가정했을 때 주석이 달린 각줄에 대한 설명으로 올바르지 않은 것을 고르시오.
 
 1. 주석1은 Child의 show메서드가 실행된다.
 2. 주석2는 20이 출력된다.
 3. 주석3은 Parent_p21의 down 메서드가 실행된다.
 4. 주석4 컴파일 오류가 발생한다.

 */

class Parent_p21{
	int k = 10;
	void show() { System.out.println("P-show"); }
	void down() { System.out.println("P-down"); }
	void up( int k ) { System.out.println("P-up : "+k); }
}

class Child_p21 extends Parent_p21{
	int k = 20;
	void show() { System.out.println("C-show"); }
	void up() { System.out.println("C-up"); }
}

public class p21 {
	
	public static void main(String[] args) {
		Parent_p21 a = new Child_p21();
		
		a.show();					// 1
		System.out.println(a.k);	// 2
		a.down();					// 3
		a.up();						// 4 
	}

}

```

## 22

```java
/* 
 22. 다음 설명 중 올바른 것을 고르시오.
 
   1. 예외처리중 finally block을 사용하려면 반드시 catch block이 있어야 한다.
   
   2. method의 overloading은 같은 이름의 method를 여러개 정의하는 것이며 조건은 전달 인자의 타입와
      갯수가 같아야 한다.
      
   3. 클래스에서 클래스간의 상속은 단일 상속만 가능하며, 인터페이스는 다중 implements가 가능하다.
   
   4. 클래스 상속시 생성자도 상속된다.  
 */
```

## 23 

```java

/* 
  
  23. 배열의 생성코드가 잘못된 것을 고르시오.
  
  	1. int[] arr1 = new int[10];
  	2. char[] arr2 = {'H', 'e', 'l', 'l', 'o'};
  	3. int[] arr3 = new int[3] {4, 5, 6};
  	4. Object arr4 = new double[3];
  	  	
 */

```
## 24

```java
/* 
 
  24. 자바 객체 생성시에 자식 클래스의 객체가 생성되면 부모 클래스 객체도 같이 생성된다. 
      현재 수행되는 객체에 대하여 부모 클래스 객체의 레퍼런스 값을 가지고 있는 것(keyword)은
      무엇인지 적으시오. 
  
 */
```

## 25 ❌

```java
/* 
	25. Test 클래스 객체 생성시 멤버변수 초기화와 관련된 내용 중 잘못된 것을 고르시오.
	
		1. 변수 a는 0으로 초기화된다.
		2. 변수 b는 '\u0000' 공백문자로 초기화 된다.
		3. 변수 c는 0.0으로 초기화된다.
		4. 변수 d는 빈문자열로 초기화된다.
```
## 26

```java
/* 
 
 26. 클래스의 멤버변수에 대한 설명으로 잘못된 것을 고르시오.
 
 	1. 메서드나 생성자에 포함되지 않은 클래스에 선언된 변수이다.
 	2. 자동초기화가 발생한다.
 	3. 메모리 영역 중 Stack영역에 생성된다.
 	4. static이 붙지않은 instance변수는 객체 생성시 객체마다 메모리가 할당된다. 

```

## 27 

```java
/* 

  27. 다음 중 생성자(Constructor)에 대한 특징으로 틀린 것을 고르시오.
  
  	1. 생성자는 반환타입을 선언하면 안된다.
  	2. 디폴트 생성자는 상속한 super 클래스의 파리미터 없는 생성자를 호출한다.
  	3. 클래스내에 파라미터 없는 생성자가 정의되어 있지 않다면 컴파일러는 항상 디폴트 생성자를 만든다.
  	4. 생성자의 이름은 클래스의 이름과 같아야 한다. 

*/ 

```

## 28

```java
/* 
 
  28. Encapsulation(캡슐화)를 제공하기 위해 중요한 데이터나 복잡한 기능을 외부에 보여지지 않도록 숨기고자 한다.
      가장 관련깊은 접근 제한자를 고르시오
      
    1. public
    2. protected
    3. default
    4. private

 */
```

## 29

```java
/* 

  29. 다음 코드의 실행결과를 적으시오.

*/


class Foo{
	private int x; 
	public Foo(int x) { this.x=x; }
	public void setx(int x) { this.x = x; }
	public int getX() { return x; }
}

public class p29 {
	static Foo fooBar (Foo foo) {
		foo = new Foo(100); 
		return foo;
	}
	
	public static void main(String[] args) { 
		Foo foo = new Foo(300); 
		System.out.print(foo.getX() + "-"); 
		Foo fooFoo = fooBar (foo); 
		System.out.print(foo.getX() +"-"); 
		System.out.print (fooFoo.getX() + "-");
		
		foo = fooBar (fooFoo); 
		System.out.print(foo.getX() + "-");
		System.out.print (fooFoo.getX());

	}


}

```

## 30 

```java
/* 

  30. [서술형] abstract class와 interface에 대해서 서술하시오. 
  	(공통점과 차이점을 이용하여 서술, 100글자 이상 서술하세요.)
  	
*/
```

## 31

```java
/* 
 
  31. 다음 코드의 실행 결과를 작성하시오.
  
 */
public class p31 {
	public static void main(String[] args) {
		String str1 = new String("a");
		String str2 = new String("a");
		String str3 = "a";
		String str4 = "a";
		if (str1 == str2)		System.out.print("A");
		if (str1.equals(str2))	System.out.print("B");
		if (str3 == str4)		System.out.print("C");
		if (str1 == str3)		System.out.print("D");


	}
}

```

## 32

```java
/* 

  32. 다음 코드의 실행 결과는 무엇인지 적으시오.
 	
 */
public class p32 {
	public static void main(String[] args) {
		System.out.printf("%.1f", (double)(5 / 2));
	}
}

```
