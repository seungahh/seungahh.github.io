---
layout: post
title:  "[JAVA]codeUp코드업 기초100제 자바로 풀기"
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

<hr/>

### No.1078
#### [기초-종합] 짝수 합 구하기(설명)
정수(1 ~ 100) 1개를 입력받아 1부터 그 수까지 짝수의 합을 구해보자.

```java

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		// 정수 1개가 입력된다.(0 ~ 100)
		
		Scanner sc = new Scanner(System.in);
		
		int sum = 0;
		int num = sc.nextInt();
		
		for(int i = 1; i <= num ; i++) {
			
			if(i%2==0) {
				sum += i;
			}
		}
		
		System.out.println(sum);

	}

}


```

<hr/>

### No.1079
#### [기초-종합] 원하는 문자가 입력될 때까지 반복 출력하기
'q'가 입력될 때까지 입력한 문자를 계속 출력하는 프로그램을 작성해보자.

**입력 예시: x b k d l q g a c**

**출력 예시 : <br> x<br> b<br> k<br> d<br> l<br> q**
```java

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		// 'q'가 입력될 때까지 입력한 문자를 계속 출력하는 프로그램을 작성해보자.
		
		Scanner sc = new Scanner(System.in);
	
		while(true) {
			
			char letter = sc.next().charAt(0);
			
			if(letter == 'q') {
				System.out.println(letter);
				break;
			}
			
			System.out.println(letter);
			
		}

	}

}

```

### Solution
- while(true) : 무한루프 사용
- 'q'가 나오기 전에 다 출력 해주고, 'q'가 나올때 마지막에 q까지 출력

<hr/>

### No.1080
#### [기초-종합] 언제까지 더해야 할까?
1, 2, 3 ... 을 계속 더해 나갈 때,
그 합이 입력한 정수(0 ~ 1000)보다 같거나 작을 때까지
계속 더하는 프로그램을 작성해보자.

즉, 1부터 n까지 정수를 계속 더한다고 할 때,
어디까지 더해야 입력한 수보다 같거나 커지는지 알아보고자 하는 문제이다.

**입력: 정수 1개가 입력된다 ex ) 55**

**출력: 1, 2, 3, 4, 5 ... 를 순서대로 계속 더해 합을 만들어가다가, 입력된 정수와 같거나 커졌을 때, 마지막에 더한 정수를 출력한다. ex ) 10**
```java

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
	
		int num = sc.nextInt();
		
		int count = 0;
		int sum = 0;
		if(num>=0 && num<=1000) {
			while(num>sum) {
				count++;
				sum+=count;
			}
		}
		
		System.out.println(count);
	
	}

}


```

### Solution
- while문에 조건 넣어주고
- count 변수 사용

<hr/>

### No.1085
#### [기초-종합] 소리 파일 저장용량 계산하기
소리가 컴퓨터에 저장될 때에는 디지털 데이터화 되어 저장된다.

마이크를 통해 1초에 적게는 수십 번, 많게는 수만 번 소리의 강약을 체크해
그 값을 정수값으로 바꾸고, 그 값을 저장해 소리를 파일로 저장할 수 있다.

값을 저장할 때에는 비트를 사용하는 정도에 따라 세세한 녹음 정도를 결정할 수 있고,
좌우(스테레오) 채널로 저장하면 2배… 5.1채널이면 6배의 저장공간이 필요하고,
녹음 시간이 길면 그 만큼 더 많은 저장공간이 필요하다.

1초 동안 마이크로 소리강약을 체크하는 수를 h
**(헤르쯔, Hz 는 1초에 몇 번? 체크하는가를 의미한다.)**

한 번 체크한 결과를 저장하는 비트 b
**(2비트를 사용하면 0 또는 1 두 가지, 16비트를 사용하면 65536가지..)**

좌우 등 소리를 저장할 트랙 개수인 채널 c
**(모노는 1개, 스테레오는 2개의 트랙으로 저장함을 의미한다.)**

녹음할 시간 s가 주어질 때,

필요한 저장 용량을 계산하는 프로그램을 작성해보자.

**입력 예시: h, b, c, s 가 공백을 두고 입력된다. h는 48,000이하, b는 32이하(단, 8의배수), c는 5이하, s는 6,000이하의 자연수이다. ex ) 44100 16 2 10**

**출력 예시: 필요한 저장 공간을 MB 단위로 바꾸어 출력한다.
단, 소수점 둘째 자리에서 반올림해 첫째 자리까지 출력하고 MB를 공백을 두고 출력한다. ex ) 1.7 MB**

```java

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {

		 Scanner sc = new Scanner(System.in);
	        
	        long h = sc.nextInt();
	        long b = sc.nextInt();
	        long c = sc.nextInt();
	        long s = sc.nextInt();
	        long total = 0;
	        
	        if(h>0 && h<=48000 && 
	            b>0 && b<=32 && b%8==0 && 
	            c>0 && c<=5 &&
	            s>0 &&s<=6000) {
	            total = h*b*c*s;
	        }
	        
	        //Math.pow(밑,지수) 2의 10승
	        // ? = (h*b*c*s)/8
	        // ? / 1024byte == kB
	        // MB로 출력하기위에 1024로 한번더 나눠준다.
	        double result = ((total/8)/Math.pow(2, 10))/Math.pow(2, 10);
	        System.out.printf("%.1f MB",result);

	}
	
}


```

### Solution
- 숫자가 길어질 수 있어서 long 타입으로함 
- h * b * c * s를 다 곱해주고 8bit=1Byte 8로 나누기  
- MB로 변환해주기 위해 KB->MB->GB->TB 1024bit=1KB 1024 두번 곱해주기
- 이때, Math.pow() 함수로 자바 거듭 제곱 구함 

<hr/>

### No.1090
#### [기초-종합] 수 나열하기2
어떤 규칙에 따라 수를 순서대로 나열한 것을 수열이라고 한다.

예를 들어
2 6 18 54 162 486 ... 은
2부터 시작해 이전에 만든 수에 3을 곱해 다음 수를 만든 수열이다.

이러한 것을 수학에서는 앞뒤 수들의 비율이 같다고 하여
등비(비율이 같다의 한문 말) 수열이라고 한다.


등비 수열을 알게된 영일이는 갑자기 궁금해졌다.

"그럼.... 13번째 나오는 수는 뭘까?"

영일이는 프로그램을 만들어 더 큰 수도 자동으로 계산하고 싶어졌다.


시작 값(a), 등비(r), 몇 번째인지를 나타내는 정수(n)가 입력될 때
n번째 수를 출력하는 프로그램을 만들어보자.

**입력 예시: 시작 값(a), 등비의 값(r), 몇 번째 인지를 나타내는 정수(n)가 공백을 두고 입력된다.(모두 0 ~ 10) ex ) 2 3 7**

**출력 예시: n번째 수를 출력한다. ex) 1458**

```java

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {

		 Scanner sc = new Scanner(System.in);
		 
		 long a = sc.nextInt();
		 long r = sc.nextInt();
		 long n = sc.nextInt();
		 
		 long result = 0;
		 
		 if(a <= 10 && a >= 0 && r <= 10 && r >= 0 && n <= 10 && n >= 0) {
			 result = (long) (a * Math.pow(r, (n-1)));
		 }
		 
		 System.out.println(result);
	

	}
	
}

```

### Solution
- Math.pow() 함수를 사용해서 등비 값의 (n번째 수 - 1)승

<hr/>

### No.1092
#### [기초-종합] 함께 문제 푸는 날
온라인 채점시스템에는 초등학생, 중고등학생, 대학생, 대학원생,
일반인, 군인, 프로그래머, 탑코더 등 아주 많은 사람들이 들어와 문제를 풀고 있는데,

실시간 채점 정보는 메뉴의 채점기록(Judge Status)을 통해 살펴볼 수 있다.

자! 여기서...잠깐..
같은 날 동시에 가입한 3명의 사람들이 온라인 채점시스템에 들어와 문제를 푸는 날짜가
매우 규칙적이라고 할 때, 다시 모두 함께 문제를 풀게 되는 그날은 언제일까?

예를 들어 3명이 같은 날 가입/등업하고, 각각 3일마다, 7일마다, 9일마다
한 번씩 들어온다면, 처음 가입하고 63일 만에 다시 3명이 함께 문제를 풀게 된다.

**입력 예시: 같은 날 동시에 가입한 인원 3명이 규칙적으로 방문하는,
방문 주기가 공백을 두고 입력된다. (단, 입력값은 100이하의 자연수이다.) ex ) 3 7 9**

**출력 예시: 3명이 다시 모두 함께 방문해 문제를 풀어보는 날(동시 가입/등업 후 며칠 후?)을 출력한다. ex) 63**

```java

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {

		 Scanner sc = new Scanner(System.in);
	     
		 int a = sc.nextInt();
		 int b = sc.nextInt();
		 int c = sc.nextInt();
		 
		 //a,b,c의 최소 공배수 찾기 : (세 수의 곱)/최대공약수
	     //a,b,c가 모두 만족하는 day가 되었을 때 반복문 종료하기
		 
		 int day=1;
		 while(day%a!=0 || day%b!=0 || day%c!=0) day++;

		 System.out.println(day);	

	}
	
}


```

### Solution
- 핵심 : a, b, c의 최소공배수 찾기 
- a, b, c로 d를 나눈 나머지가 0이 아니면 반복하는 반복문
- d를 a로 나눈 나머지가 0이 되어도 d를 b로 나눈 나머지가 0이 아니면 다시 반복함
- d를 b로 나눈 나머지가 0이 되어도 d를 c로 나눈 나머지가 0이 아니면 다시 반복함
- 조건식 3개 동시에 거짓이면 while을 탈출함

<hr/>

### No.1093
#### [기초-1차원배열] 이상한 출석 번호 부르기1
정보 선생님은 수업을 시작하기 전에 이상한 출석을 부른다.

선생님은 출석부를 보고 번호를 부르는데,
학생들의 얼굴과 이름을 빨리 익히기 위해 번호를 무작위(랜덤)으로 부른다.

그리고 얼굴과 이름이 잘 기억되지 않는 학생들은 번호를 여러 번 불러
이름과 얼굴을 빨리 익히려고 하는 것이다.

출석 번호를 n번 무작위로 불렀을 때, 각 번호(1 ~ 23)가 불린 횟수를 각각 출력해보자.

**입력 예시: 첫 번째 줄에 출석 번호를 부른 횟수인 정수 n이 입력된다. (1 ~ 10000)
두 번째 줄에는 무작위로 부른 n개의 번호(1 ~ 23)가 공백을 두고 순서대로 입력된다. ex ) 10
1 3 2 2 5 6 7 4 5 9**

**출력 예시: 1번부터 번호가 불린 횟수를 순서대로 공백으로 구분하여 한 줄로 출력한다. ex) 1 2 1 1 2 1 1 0 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0**

```java

import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		
		 Scanner sc = new Scanner(System.in);
		
		 int [] arr = new int[24];
		 
		 int num = sc.nextInt();
		 
		 // 10개의 무작위로 부른 번호가 들어간 배열 1 3 2 2 5 6 7 4 5 9
		 for(int i = 0; i < num; i++) {
			 int num2 = sc.nextInt();
   		 //arr[0]번에는 1번이 1번불려서 1이 저장된다.
                 //arr[1]번에는 2번이 2번불려서 2가 저장된다.
			 arr[num2] += 1;
		 }
		 
		 for(int i = 1; i <= 23; i++) {
			 System.out.print(arr[i] + " ");
		 }
		 
		 
	}
	
}



```

### Solution
- 10개의 무작위로 부른 번호가 들어간 배열 1 3 2 2 5 6 7 4 5 9
- arr[0]번에는 1번이 1번불려서 1이 저장된다.
- arr[1]번에는 2번이 2번불려서 2가 저장된다.