---
layout: post
title:  "[Java] oop test review"
published : false
subtitle:   "oop test review"
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

 답 : toString 
 
TMI : 최상위 부모클래스 - java.lang의 Object class
 */

class Dog{
	String name;
	Dog(String name){this.name = name;}
	
	@Override
	public String toString() {
		return "Dog [name=" + name + "]";
	}
	
	
}

public class p01 {

	public static void main(String[] args) {
		String s = new String("싸피");
		System.out.println(s);
		Dog dog = new Dog("자바");
		System.out.println(dog);
	}
	
	
}



```

## 2  ❌

```java

/* 
  2. 다음 코드의 실행결과를 맞추시오
 
   	답 : 10,20,20,10

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

## 3 ❌

```java

/* 
 
 3. 다음 코드에 대한 설명으로 맞는 것을 고르시오. 

   1. 컴파일 오류 발생
   2. name = 
   3. name = null
   4. 실행시 오류 발생 
 
   답 : 1번
   The local variable name may not have been initialized
	
	해설 - 로컬변수는 자동 초기화가 되지 않는다. 
	      멤버변수는 힙에 할당되면서 자동 초기화 된다. 
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
 
 
 답 : Object  / java.lang / equals, toString
 */

```

## 5

```java

/* 
5. 다음코드의 실행결과를 골라라

 답 : Animal, B
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
 
 답 : class area(method area)
 */
```

## 7 ❌

```java
/*  
  
  7. Parent 클래스를 상속하는 클래스에 메서드 추가시 가능한 코드를 고르시오.
  
  
  내가 고른답 - private 
  
  정답 - 1, 3번 
  해설 - 메서드 시그니처는 이름과 파라미터 갯수, 타입 2가지
 */

// 보기 1번
class Parent{
	protected int method(int a, int b) {
		return 0;
	}
}

class s1 extends Parent{
	public int method(int a, int b) {
		return 0;
	}
}


// 보기 2번
//Cannot reduce the visibility of the inherited method from Parent
class s2 extends Parent{
	private int method(int a, int b) {
		return 0;
	}
}


// 보기 3번
class s3 extends Parent{
	int method(int a, long b) {
		return 0;
	}
}


// 보기 4번
//The return type is incompatible with Parent.method(int, int)
class s4 extends Parent{
	public byte method(int a, int b) {
		return 0;
	}
}

```

## 8 ❌

```java
/*
  
  8.다음 코드의 실행결과를 적으시오. 
  
  메인에서 이렇게 new로 할당하면, 0으로 초기화 된다. 쓰레기값이 안나옴.
  arr[0] = new int[1];
  
  
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
  
  정답 : public - protected - default - private
 
  
 */

```

## 10

```java
/*

다음 Test 클래스의 read를 호출하기 위해 다음과 같이 코드를 작성할 때 밑줄 친 곳에 올 수 없는 것은?

정답 : new Object();
The method read(Book) in the type p10 is not applicable for the arguments (Object)


		
*/ 

class Book extends Object{ }
class Magazine extends Book{ }
class ITNews extends Magazine{ }


public class p10 {
	public static void read(Book c) { }
	
	public static void main(String[] args) {
		read(new ITNews());
		read(new Book());
		read(new Magazine());
		//read(new Object());
		//The method read(Book) in the type p10 is not applicable for the arguments (Object)
		
	}
}

```

## 11 ❌

```java
/* 
 
 11. 다음 코드의 실행 결과를 고르시오.
 
 	1. 컴파일 오류 발생
 	2. Hello
 	3. nullHello
 	4. 실행시 오류 발생
 	
 	정답 :nullHello
 
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

 
 정답 : ABC
 
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
  
  답 : 1, 10
  
 
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
 14. 다음 코드의 실행결과를 고르시오.
 
 답 : SSAFY Student Hello 
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
 
 
 답 : ABD
 
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

## 16 ❌

```java
/*

 16. 다음 코드의 실행결과를 고르시오.

 답 :  java.lang.NullPointerException
	 런타임 에러 발생 
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
 	
 	정답 : 4번
 	The method print() from the type Parent_p17 is not visible

*/

class Parent_p17{
	private void print() {
		System.out.println("Parent");
	}
}


//The method print() from the type Parent_p17 is not visible
class Child_p17 extends Parent_p17{
	void childprint() {
		super.print();
	}
}


public class p17 {

}

```

## 18

```java
/*
 
 18. 다음 코드의 실행 결과를 고르시오. 
 
 답 : 1110
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

## 19 ❌

```java

/* 
 
 19. 다음 코드를 수행시 예상되는 결과를 적으시오. 
 
 정답 : Hi
 */
public class p19 {

	public static void main(String[] args) {
		String data = "Hi";
		data.replace(data.charAt( 1 ), 'e');
		System.out.println( data );
	}
}

```

## 20 ❌

```java
/*

 20. 다음 코드에 대한 설명으로 올바른 것을 고르시오.
 
 
 보기 
  1. Compile 오류가 발생한다.
  2. 실행 오류가 발생한다.
  3. 정상적으로 실행되고 Magazine이 출력된다.
  4. 정상적으로 실행되고 Novel이 출력된다. 
 
 
 답 : 1번 / The constructor p20() is undefined 
 
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
 
 다음 코드가 한줄씩 실행된다고 가정했을 때 주석이 달린 각줄에 대한 설명으로 올바르지 않은 것을 고르시오.
 
 1. 주석1은 Child의 show메서드가 실행된다.
 2. 주석2는 20이 출력된다.
 3. 주석3은 Parent_p21의 down 메서드가 실행된다.
 4. 주석4 컴파일 오류가 발생한다.
 
 정답 : 2
 
 1 : Child_p21의 show 실행 
 2 : 10 
 3 : Parent_p21의 down 실행 
 4 : 컴파일 오류 The method up(int) in the type Parent_p21 is not applicable for the arguments ()
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
		
		a.show();					// 1 : Child_p21의 show 실행 
		System.out.println(a.k);	// 2 : 10 
		a.down();					// 3 : Parent_p21의 down 실행 
		a.up();						// 4 : 컴파일 오류 The method up(int) in the type Parent_p21 is not applicable for the arguments ()
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
	
   정답 : 3번 
   
   해설 
   
   <overloading> 
   		1. 메서드의 이름이 같아야 한다.
		2. 메서드의 리턴타입이 다른 경우는 오버로딩이 성립되지 않는다.
		3. 매개변수의 개수 or 매개변수의 자료형이 달라야 한다. 
		
		예시
		void println ()
		void println (boolean x)
		void println (char x)
		void println (double x)
		void println (String x)
		
	<overwriting>
		1. 부모클래스의 메소드를 자식클래스에서 '재정의'하여 사용합니다.  
		2. 자식클래스에서 overwring시 조건
		  2.1 부모클래스의 메소드의 이름과 매개변수의 개수, 데이터타입, 순서와 리턴 타입이 같아야 한다.


 
 */
```

## 23 ❌

```java

/* 
  
  23. 배열의 생성코드가 잘못된 것을 고르시오.
  
  	1. int[] arr1 = new int[10];
  	2. char[] arr2 = {'H', 'e', 'l', 'l', 'o'};
  	3. int[] arr3 = new int[3] {4, 5, 6};
  	4. Object arr4 = new double[3];
  	
  	정답 : 3번 
  	Cannot define dimension expressions when an array initializer is provided
	해설 int[] arr5 = new int[]{4, 3, 2}; 가능함
		
  	
 */

public class p23 {
	public static void main(String[] args) {
		int[] arr1 = new int[10];
		char[] arr2 = {'H', 'e', 'l', 'l', 'o'};
		int[] arr3 = new int[3] {4, 5, 6};
		Object arr4 = new double[3];
	}
}

```
## 24

```java
/* 
 
  24. 자바 객체 생성시에 자식 클래스의 객체가 생성되면 부모 클래스 객체도 같이 생성된다. 
      현재 수행되는 객체에 대하여 부모 클래스 객체의 레퍼런스 값을 가지고 있는 것(keyword)은
      무엇인지 적으시오. 
      
  답 : super
  
  해설 : super 키워드는 부모 클래스로부터 상속받은 필드나 메소드를 자식 클래스에서 참조하는 데 사용하는 참조 변수입니다.
  
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


	정답 : 4번 
	해설 
		멤버변수 초기값 
		boolean 			- false
		char 				- '\u0000'  // 공백문자 
		byte, short, int	- 0
		long 				- 0
		float				- 0.0f
		double				- 0.0d or 0.0
		reference type		- null 
*/

public class p25 {
	
	static int a;
	static char b;
	static double c;
	static String d;
	
	static void print() {
		System.out.println("a : " + a);
		System.out.println("b : " + b);
		System.out.println("c : " + c);
		System.out.println("d : " + d);

	}
	
	public static void main(String[] args) {
		print();
	}

}

```
## 26

```java
/* 
 
 26. 클래스의 멤버변수에 대한 설명으로 잘못된 것을 고르시오.
 
 	1. 메서드나 생성자에 포함되지 않은 클래스에 선언된 변수이다.
 	2. 자동초기화가 발생한다.
 	3. 메모리 영역 중 Stack영역에 생성된다.
 	4. static이 붙지않은 instance변수는 객체 생성시 객체마다 메모리가 할당된다. 
 	
 
 
 	답 : 3 ?
 	
 	해설  -  https://whatisthenext.tistory.com/30
 		멤버변수 - 클래스 영역에 선언된 변수 (하늘색 변수)
 			1) 클래스 변수:  static이 붙은 변수 
 			2) 인스턴스변수
 			
 		지역변수 - method 영역 안에서 선언된 변수(노란색 변수)
 	
 
 */
public class p26 {
	int instance_var_x;
	int instance_var_y;
	static int static_instance_var_z;
	
	void method() {
		int local_x;
		int local_y;
	}
}

```

## 27 ❌

```java
/* 

  27. 다음 중 생성자(Constructor)에 대한 특징으로 틀린 것을 고르시오.
  
  	1. 생성자는 반환타입을 선언하면 안된다.
  	2. 디폴트 생성자는 상속한 super 클래스의 파리미터 없는 생성자를 호출한다.
  	3. 클래스내에 파라미터 없는 생성자가 정의되어 있지 않다면 컴파일러는 항상 디폴트 생성자를 만든다.
  	4. 생성자의 이름은 클래스의 이름과 같아야 한다. 


	정답 : 3번
	해설 : 
*/ 

// 1번 - 경고 메시지 This method has a constructor name
// 생성자가 제대로 동작하지 않는다.
class P_p27_1{
	int num;
	void P_p27() {
		this.num = 10;
		return;
	}
}

class P_p27_2{
	public P_p27_2() {
		System.out.println("P_p27_2");
	}
}

class C_p27_2 extends P_p27_2{
	
	public C_p27_2() {
		// super(); 이게 자동으로 추가됨.
		System.out.println("C_p27_2");
	}
	
	
	public C_p27_2(int x) {
		//이것을 호출해도 super(); 이 자동으로 추가됨.
		System.out.println("C_p27_2, X : " + x);
	}
}


class P_p27_3{
	//public P_p27_3() {}
	
	public P_p27_3(int x) {
		System.out.println("P_p27_3, X : "+ x);
	}
}


class C_p27_3 extends P_p27_3{
	
	public C_p27_3() {
		// super(); 이게 자동으로 추가됨.
		System.out.println("C_p27_3");
	}
	
	
	public C_p27_3(int x) {
		//이것을 호출해도 super(); 이 자동으로 추가됨.
		System.out.println("C_p27_3, X : " + x);
	}
}


public class p27 {
	
	public static void main(String[] args) {
		P_p27_1 p1 = new P_p27_1();
		System.out.println(p1.num);
		
		C_p27_2 c2 = new C_p27_2(); 
		C_p27_2 c2_1 = new C_p27_2(10); 
	}
}

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
    
    정답 : 4번 
   
 
 
 */
```

## 29

```java
/* 
  29. 다음 코드의 실행결과를 적으시오.
  
  답 : 300-300-100-100-100
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

## 30 ❌

```java
/* 
  30. [서술형] abstract class와 interface에 대해서 서술하시오. 
  	(공통점과 차이점을 이용하여 서술, 100글자 이상 서술하세요.)
  	
  	
  	나의 답변
  		공통점 
  		1) Java에서 다형성을 지원하기 위해 사용하는 개념이다.
  		2) abstract나 interface를 받아 사용하는 하위클래스는 abstract와 interface에서 정의된
  		   메소드를 반드시 정의해야 된다.
  		   
        차이점
        1) abstract는 상속관계에서 부모클래스에서 구현을 하지 않고, 자식클래스가 구현하도록하는 개념이다.
        2) interface는 대규모 프로젝트시 PM과 같은 최상위 관라자가 interface를 설계 후 실제 구현하는 프로그래머에게
           전달하면, 프로그래머는 정의된 interface를 implements한 후 interface에 맞춰 비즈니스 로직을 구현하는 것이다. 
           
  	
  	
  	구글 검색 
  	1. 공통점 
  		1) abstract class(추상 클래스)와 interface 는 선언만 있고 구현 내용이 없는 클래스이다.
 		2) 자기 자신이 new를 해서 객체를 생성할 수 없으며, 추상클래스를 extends 받거나,
 		   interface를 implements 한 자식만이 객체를 생성할 수 있다.
		3) abstract class는 extends로 상속받은 자식, interface는 implements하고 구현한 자식들만 
		   객체를 생성할 수 있다.
		   
	2. 차이점 
		1) 추상클래스는 단일 extends만 가능 / 인터페이스는 다중 implements가능 
		2) 추상클래스의 목적 - 상속 받아서 기능을 확장시키는 것(부모의 유전자를 물려받는 것)
		3) 인터페이스의 목적 - implements한 메서드를 반드시 구현하도록 강요하는 것 / 비즈니스 로직에 따라 결합하는 관계를 형성
	

출처: https://marobiana.tistory.com/58 [Take Action]
 */
```

## 31

```java
/* 
 
  31. 다음 코드의 실행 결과를 작성하시오.
  
 	답 : BC
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
 	
 	답 : 2.0
 */
public class p32 {
	public static void main(String[] args) {
		System.out.printf("%.1f", (double)(5 / 2));
	}
}

```
