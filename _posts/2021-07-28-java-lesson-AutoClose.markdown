---
layout: post
title:  "[Java] 강의 Exception Auto Closable"
subtitle:   "auto closable"
categories: programming-language
tags: java
---


## Auto Closable
- finally에서 close를 할때 
	- fianlly 안에서 또 다시 try-catch로 처리해줘야 된다.
		- 불편함.

## Auto Cloasble이 생긴 이유

### 1.MS에서 C#에 개발자의 불편함을 먼저 수용해 Auto Closable 구문을 사용하기 시작

### 2.Java도 C#을 따라 버전업을 할때 Auto Closable 구문 추가함

## Java API docs autoclosable사용 예시
[java.sql - 인터페이스 / connection](https://docs.oracle.com/javase/8/docs/api/java/sql/Connection.html)

## Auto Closable 예시
- jdbc 연결시 메인에 throws Exception을 통해 예외처리

```java
package day2.jdbc.autoclosable;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class JDBCClientDelete {
	public static void main(String[] args) throws Exception{

		Class.forName("com.mysql.cj.jdbc.Driver");  //driver loading
		Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/startcamp_db?useUniCode=yes&characterEncoding=UTF-8&serverTimezone=Asia/Seoul",
				"root", "password");
				
		Statement stmt = con.createStatement();
		
		String SqlDelete = "DELETE FROM person WHERE person_id=3";
		int cnt = stmt.executeUpdate(SqlDelete);
		System.out.println(cnt);
		
		
		System.out.println(cnt);
		
		stmt.close();
		con.close();
		
	}
}
```


- try-catch로만 예외처리

```java
package day2.jdbc.autoclosable;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

public class JDBCClientDelete2 {
	public static void main(String[] args) {
		Connection con = null;
		Statement stmt = null;
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");  //driver loading
			con = DriverManager.getConnection("jdbc:mysql://localhost:3306/startcamp_db?useUniCode=yes&characterEncoding=UTF-8&serverTimezone=Asia/Seoul",
					"root", "password");
			
			stmt = con.createStatement();
			
			String SqlDelete = "DELETE FROM person WHERE person_id=3";
			int cnt = stmt.executeUpdate(SqlDelete);
			System.out.println(cnt);
			
			
			System.out.println(cnt);
		}catch( ClassNotFoundException e) {
			e.printStackTrace();
		}catch(SQLException e){
			e.printStackTrace();
		}finally {
			
			try{
				stmt.close();
				con.close();
			}catch(SQLException e) {
				e.printStackTrace();
			}

		}
		
	}
}
```



## Auto closable 안에 String 선언시 에러 발생
- The resource type `String` does `not implement` `java.lang.AutoCloseable`


- 중첩해서 사용하면 된다. 

```java
package day2.jdbc.autoclosable;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class JDBCClientSelect {
	public static void main(String[] args) throws Exception{
	
		try( 
		Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/startcamp_db?useUniCode=yes&characterEncoding=UTF-8&serverTimezone=Asia/Seoul",
				"root", "password");		
		Statement stmt = con.createStatement();
		//String SqlSelect ="SELECT person_id, person_nm, person_age FROM person";
		//ResultSet rs = stmt.executeQuery(SqlSelect);		
		){
			Class.forName("com.mysql.cj.jdbc.Driver");  //driver loading
			String SqlSelect = "SELECT person_id, person_nm, person_age FROM person";
			try(
					ResultSet rs = stmt.executeQuery(SqlSelect);
			){
				while(rs.next()) {
					int person_id = rs.getInt("person_id");
					String person_nm = rs.getString("person_nm");
					int person_age = rs.getInt("person_age");
					System.out.println(person_id + "/" + person_nm + "/" + person_age);
				}
			}catch(SQLException e) {
				e.printStackTrace();
			}
			
		}catch(ClassNotFoundException | SQLException e) {
			e.printStackTrace();
		}
		
		
		
		
		
		rs.close();
		stmt.close();
		con.close();
		
	}
}
```





