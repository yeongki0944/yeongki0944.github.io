---
layout: post
title:  "[Java] Java Interface"
subtitle:   "java interface"
categories: programming-language
tags: java
---
## Class Diagram
![](https://i.imgur.com/uCYnaal)


## Interface : IBookManager

```java
public interface IBookManager {
	/**
	 * 도서를 도서리스트에 추가한다.
	 * @param book : 추가할 도서
	 */
	void add(Book book);
	/**
	 * 고유번호로 해당 도서를 도서리스트에서 삭제한다.
	 * @param isbn : 삭제할 도서의 고유번호
	 */
	void remove(String isbn);
	/**
	 * 등록된 도서리스트를 반환한다.
	 * @return 등록된 전체 도서리스트
	 */
	Book[] getList();
	/**
	 * 고유번호로 해당 도서를 조회한다.
	 * @param isbn : 조회할 도서의 고유번호
	 * @return 고유번호에 해당하는 도서
	 */
	Book searchByIsbn(String isbn);
	/**
	 * 도서 제목을 포함하고 있는 도서리스트를 반환한다.
	 * @param title : 조회할 도서의 제목
	 * @return
	 */
	Book[] searchByTitle(String title);
	/**
	 * 잡지리스트를 반환한다.
	 * @return 잡지리스트
	 */
	Magazine[] getMagazines();
	/**
	 * 잡지가 아닌 도서리스트를 반환한다. 
	 * @return 잡지가 아닌 도서리스트
	 */
	Book[] getBooks();
	/**
	 * 도서리스트의 가격의 총합을 반환한다.
	 * @return 모든 도서 가격의 총합
	 */
	int getTotalPrice();
	/**
	 * 도서가격의 평균을 반환한다.
	 * @return 모든 도서 가격의 평균
	 */
	double getPriceAvg();
}
```

## Interface 구현(implements) - BookManagerImpl class

```java
import java.util.Arrays;

/**
 * 도서리스트를 배열로 유지하며 관리하는 클래스
 */
public class BookManagerImpl implements IBookManager {
	/**
	 * 관리할 최대 도서 수
	 */
	private static int MAX_SIZE = 100;
	/**
	 * 관리할 도서 리스트
	 */
	private Book[] books = new Book[MAX_SIZE];
	/**
	 * 현재 등록된 도서 수
	 */
	private int size;
	
	/**
	 * 싱글톤 디자인패턴 위해 유지하는 객체 참조값 
	 * 클래스 메로리에 로드시에 객체 1번 생성하여 참조값 유지
	 */
	
	//선언을 인터페이스로 했음. 
	// main, 외부에서 이것을 사용하는 관점에서 보면, BookManager에서 구현한 상세 내용은 관심이 없고 인터페이스에서 정의한 기능만 사용하고 싶기때문에
	// 인터페이스로 객체를 생성해서, 싱글톤 디자인을 한다.
	
	// 싱글톤으로 다중 인터페이스를 구현할때, getInstance부분을 복잡하게 구현해야 된다 -> 디자인패턴으로 확장 // 
	private static IBookManager instance = new BookManagerImpl();
	/**
	 * 기본 생성자
	 */
	private BookManagerImpl() { // 외부에서 객체 생성을 하지 못하도록 접근 제어자를  private으로 만든 생성자
	}
	/**
	 * 내부에서 생성한 객체의 참조값을 반환한다.
	 * @return 생성된 객체의 참조값
	 */
	public static IBookManager getInstance() {
		return instance;
	}

	/**
	 * 도서를 도서리스트에 추가한다.
	 * @param book : 추가할 도서
	 */
	@Override
	public void add(Book book) {
		if(size<MAX_SIZE) books[size++] = book;
	}
	/**
	 * 고유번호로 해당 도서를 도서리스트에서 삭제한다.
	 * @param isbn : 삭제할 도서의 고유번호
	 */
	@Override
	public void remove(String isbn) {
		for (int i = 0; i < size; ++i) {
			// 삭제할 도서를 찾았다면 해당 도서 위치에 배열의 제일 마지막 도서를 복사
			if (books[i].getIsbn().equals(isbn)) {
				books[i] = books[size-1];
				books[size-1]=null;			// 삭제된 도서 위치 null 처리
				--size;						// 등록된 도서 수 감소
				break;
			}
		}
	}
	/**
	 * 등록된 도서리스트를 반환한다.
	 * @return 등록된 전체 도서리스트
	 */
	@Override
	public Book[] getList() {
		return Arrays.copyOfRange(books, 0, size);
	}
	/**
	 * 고유번호로 해당 도서를 조회한다.
	 * @param isbn : 조회할 도서의 고유번호
	 * @return 고유번호에 해당하는 도서
	 */
	@Override
	public Book searchByIsbn(String isbn) {
		for (int i = 0; i < size; ++i) {
			if (books[i].getIsbn().equals(isbn)) return books[i]; 
		}
		return null;
	}
	/**
	 * 도서 제목을 포함하고 있는 도서리스트를 반환한다.
	 * @param title : 조회할 도서의 제목
	 * @return
	 */
	@Override
	public Book[] searchByTitle(String title) {
		int count = 0; 
		for (int i = 0; i < size; ++i) {
			if (books[i].getTitle().contains(title)) ++count;
		}
		
		Book[] result = new Book[count];
		int idx = 0;
		for (int i = 0; i < size; ++i) {
			if (books[i].getTitle().contains(title)) {
				result[idx++] = books[i];
			}
		}
		return result; 
	}
	/**
	 * 잡지리스트를 반환한다.
	 * @return 잡지리스트
	 */
	@Override
	public Magazine[] getMagazines() {
		int count = 0;
		for (int i = 0; i < size; ++i) {
			if (books[i] instanceof Magazine) ++count;
		}
		
		Magazine[] result = new Magazine[count];
		int idx = 0;
		for (int i = 0; i < size; ++i) {
			if (books[i] instanceof Magazine) {
				result[idx++] = (Magazine)books[i];
			}
		}
		return result;
	} 
	/**
	 * 잡지가 아닌 도서리스트를 반환한다. 
	 * @return 잡지가 아닌 도서리스트
	 */
	@Override
	public Book[] getBooks() {
		int count = 0; 
		for (int i = 0; i < size; ++i) {
			if (!(books[i] instanceof Magazine)) ++count;
		}
		
		Book[] result = new Book[count];
		int idx = 0;
		for (int i = 0; i < size; ++i) {
			if (!(books[i] instanceof Magazine)) {
				result[idx++] = books[i];
			}
		}
		return result;
	}	
	/**
	 * 도서리스트의 가격의 총합을 반환한다.
	 * @return 모든 도서 가격의 총합
	 */
	@Override
	public int getTotalPrice() {
		int total = 0;
		for (int i = 0; i < size; ++i) {
			total += books[i].getPrice();
		}
		return total;
	}
	/**
	 * 도서가격의 평균을 반환한다.
	 * @return 모든 도서 가격의 평균
	 */
	@Override
	public double getPriceAvg() {
		return (double)getTotalPrice()/ size;
	}
}
```

## Book Class

```java
public class Book {
	/** 고유 번호 */
	private String isbn;		
	/**	제목 */
	private String title;		
	/** 저자 */
	private String author;		
	/** 출판사 */
	private String publisher;	
	/** 가격 */
	private int price;			
	/**	설명 */
	private String desc;		

	/** 기본 생성자 */
	public Book() {
	}
	/** 도서 정보를 모두 받아 생성하는 생성자 */
	public Book(String isbn, String title, String author, String publisher, int price, String desc){
		// 받은 정보로 객체의 상태를 초기화한다.
		this.isbn = isbn;
		this.title = title;
		this.author = author;
		this.publisher = publisher;
		this.price = price;
		this.desc = desc;
	}
	/**
	 * 고유번호를 반환한다.
	 * @return 고유번호
	 */
	public String getIsbn() {
		return isbn;
	}
	/**
	 * 고유번호를 저장한다.
	 * @param isbn : 고유번호
	 */
	public void setIsbn(String isbn) {
		this.isbn = isbn;
	}
	/**
	 * 제목을 반환한다.
	 * @return 제목
	 */
	public String getTitle() {
		return title;
	}
	/**
	 * 제목을 저장한다.
	 * @param title : 제목
	 */
	public void setTitle(String title) {
		this.title = title;
	}
	/**
	 * 저자를 반환한다.
	 * @return 저자
	 */
	public String getAuthor() {
		return author;
	}
	/**
	 * 저자를 저장한다.
	 * @param author : 저자
	 */
	public void setAuthor(String author) {
		this.author = author;
	}
	/**
	 * 출판사를 반환한다.
	 * @return 출판사
	 */
	public String getPublisher() {
		return publisher;
	}
	/**
	 * 출판사를 저장한다.
	 * @param publisher : 출판사
	 */
	public void setPublisher(String publisher) {
		this.publisher = publisher;
	}
	/**
	 * 가격을 반환한다.
	 * @return 가격
	 */	
	public int getPrice() {
		return price;
	}
	/**
	 * 가격을 저장한다.
	 * @param price : 가격
	 */	
	public void setPrice(int price) {
		this.price = price;
	}
	/**
	 * 설명을 반환한다.
	 * @return 설명
	 */
	public String getDesc() {
		return desc;
	}
	/**
	 * 설명을 저장한다.
	 * @param desc : 설명
	 */		
	public void setDesc(String desc) {
		this.desc = desc;
	}
	/**
	 * 도서의 정보를 문자열로 반환한다
	 * @return 도서정보
	 */
	public String toString() {
		return isbn + '\t' + "| " + title + "  \t" + "| " + author + '\t' + "| " + publisher + '\t'
				+ "| " + price + '\t' + "| " + desc + '\t';
	}
}
```

## Magazine Class

```java
public class Magazine extends Book {
	/**
	 * 발행년도
	 */
	private int year;
	/**
	 * 발행월
	 */
	private int month;
	
	/** 기본 생성자 */
	public Magazine() {
	}
	/** 잡지 정보 모두를 받아 생성하는 생성자 */
	public Magazine(String isbn, String title, String author, String publisher, int price, String desc, int year, int month) {
		super(isbn, title, author, publisher, price, desc);
		this.year = year;
		this.month = month;
	}
	/**
	 * 발행년도를 반환한다.
	 * @return 발행년도
	 */
	public int getYear() {
		return year;
	}
	/**
	 * 발행년도를 저장한다.
	 * @param year : 발행년도
	 */
	public void setYear(int year) {
		this.year = year;
	}
	/**
	 * 발행월을 반환한다.
	 * @return 발행월
	 */
	public int getMonth() {
		return month;
	}
	/**
	 * 발행월을 저장한다.
	 * @param month : 발행월
	 */
	public void setMonth(int month) {
		this.month = month;
	}
	/**
	 * 잡지정보를 문자열로 반환하다.
	 * @return 잡지 정보
	 */
	public String toString() {
		// StringBuilder 와 덧셈이 차이
		// 1.StringBuilder 
		//		충분히 큰 배열을 만들어 그 배열에 append하는 식으로 동작
		//		Stringbuffer 도 있다.
		//		문자열을 자주 사용하고, 큰 문자열을 다룰경우 
		
		
		// 2. 덧셈으로 하면 결과를 heap에 새로운 객체로 덧셈 결과를 생성. -> 메모리가 낭비되는 것.
		// 		최근 컴파일러가 StringBuilder로 자동으로 바꿈 / 단 반복문같은 복잡한 코드는 컴파일러가 최적화하지 못함. 
		//		문자열이 작은 경우, new가 아닌  리터럴로 생성해서 사용 권장.
		
		
		StringBuilder builder = new StringBuilder();
		builder.append(super.toString());
		builder.append("|");
		builder.append(year + "\t| ");
		builder.append(month);
		return builder.toString();
	}
}
```


## Test main

```java
public class BookTest {

	public static void main(String[] args) {
		
		// 도서 리스트를 유지하고 관리하는 BookManagerImpl 객체의 참조값을 조회한다.(싱글톤 디자인패턴 적용했으므로 객체 생성 불가)
		IBookManager bookManager = BookManagerImpl.getInstance();
		// BookManager 객체를 이용해  도서정보를 추가한다.
		bookManager.add(new Book("21424", "Java Pro", "김하나", "jaen.kr", 15000, "Java 기본 문법"));
		bookManager.add(new Book("21425", "Java Pro2", "김하나", "jaen.kr", 25000, "Java 응용"));
		bookManager.add(new Book("35355", "분석설계", "소나무", "jaen.kr", 30000, "SW 모델링"));
		bookManager.add(new Magazine("45678", "월간 알고리즘", "홍길동", "jaen.kr", 10000, "1월 알고리즘", 2021, 1));

		System.out.println("**********************도서 전체 목록**********************");
		for (Book b : bookManager.getList()) {
			System.out.println(b);
		}
		System.out.println("**********************일반 도서 목록**********************");
		for (Book b : bookManager.getBooks()) {
			System.out.println(b);
		}
		System.out.println("**********************잡지 목록**********************");
		for (Magazine b : bookManager.getMagazines()) {
			System.out.println(b);
		}
		System.out.println("**********************도서 제목 포함검색**********************");
		for (Book b : bookManager.searchByTitle("Java")) {
			System.out.println(b);
		}
		System.out.println("도서 가격 총합 : "+bookManager.getTotalPrice());
		System.out.println("도서 가격 평균: "+bookManager.getPriceAvg());	
	}
}
```