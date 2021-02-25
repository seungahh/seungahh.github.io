---
layout: post
title:  "[JAVA]codeUp코드업 기초100제 자바로 풀기(1001~1014)"
date:   2021-02-25 21:03:36 +0530
categories: Java
---
### No.1014
#### [기초-입출력] 문자 2개 입력받아 순서 바꿔 출력하기
2개의 문자(ASCII CODE)를 입력받아서 순서를 바꿔 출력해보자.

```java

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
	//2개의 문자(ASCII CODE)를 입력받아서 순서를 바꿔 출력해보자.
	Scanner sc = new Scanner(System.in);
        
        String chars = sc.nextLine();
        //toCharArray() 문자배열로 변환해주는 메소드
        char[] chararr = chars.toCharArray();
        
        System.out.println(chararr[2]+" "+chararr[0]);

	}

}

```

### Solution
- toCharArray() : 문자열을 문자배열로 변환

<hr/>

### No.1020
#### [기초-입출력] 주민번호 입력받아 형태 바꿔 출력하기
주민번호는 다음과 같이 구성된다. XXXXXX-XXXXXXX 앞의 6자리는 생년월일(yymmdd)이고 뒤 7자리는 성별, 지역, 오류검출코드이다.
주민번호를 입력받아 형태를 바꿔 출력해보자.

```java

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
	
		Scanner sc = new Scanner(System.in);
		
		String num = sc.nextLine();
		
		String [] tokens = num.split("-");
		
		for(int i = 0; i < tokens.length; i++) {
			System.out.print(tokens[i]);
		}

	}

}

```

### Solution
- split() : split() 함수로 문자열 자르기