# JAVA ONLINE STUDY _ STUDYHALLE #7  
__과제 : 패키지__  
__목표 : 자바의 패키지에 대해 학습하기.__

---

## package 키워드  

`패키지 package`란 클래스의 묶음으로, 서로 관련된 클래스 또는 인터페이스를 그룹단위로 묶어놓음으로써 클래스를 효율적으로 관리할 수 있다.  

```java
package com.studyhalle;  // 반드시 소스파일의 첫 번째 문장으로 작성되어야 하며, 소스파일에서 한 번만 선언가능하다.

...
```

- 클래스의 이름은 패키지명을 포함한다. `예) java.lang.String, java.util.Date`  

- 클래스가 물리적으로 하나의 클래스파일 (.class) 인것과 같이 패키지는 물리적으로 하나의 디렉토리이며, 어떤 패키지에 속한 클래스는 해당 디렉토리에 존재하는 클래스파일이어야 한다.  

- 모든 클래스는 반드시 하나의 패키지에 속해야 한다. 자신이 속할 패키지가 지정되지않은 클래스는 자동적으로 `이름없는 패키지 unnamed package`에 속하게 된다.  

- 점(.)을 구분자로 하여 계층구조로 구성할 수 있다.

- 대소문자를 모두 허용하지만, 클래스명과 구분하기 위해 소문자로 하는 것을 원칙으로 하고 있다.  


## import 키워드  

- 클래스 코드 작성 전 사용하고자 하는 클래스의 패키지를 미리 명시하는데 사용되며, import문을 이용해 명시된 클래스는 소스코드 작성 시 패키지명을 생략할 수 있다.

- 컴파일러에게 소스파일에 사용된 클래스의 패키지에 대한 정보를 제공하는 역할을 한다.  
  컴파일 시 컴파일러는 import문을 통해 소스파일에 사용된 클래스들의 패키지를 알아 낸 다음, 모든 클래스 이름 앞에 패키지명을 붙여준다.  

- import문은 package문 다음, 클래스 선언문 이전에 위치하며, 한 소스파일에 여러번 선언할 수 있다.  

```java
package com.studyhalle;     // 1. package문  

import java.lang.String;    // 2. import문
import java.util.*;         // 같은 패키지 내 복수의 클래스가 사용될 때, *로 대체가능하다.  

public class Car {        // 3. 클래스선언  
...
}
```

그러나, * 는 하위패키지까지 포함하지는 않는다. 그러므로

```java
import java.util.*;  
import java.text.*;  
```
를
```java
import java.*;
```
로 대체할 수는 없다.  


### static import  

static 멤버를 호출할 때 클래스 이름을 생략할 수 있다. 특정 클래스의 static 멤버를 자주 사용할 경우 편리하다.  

```
import static java.lang.Integer.*;    // Integer클래스의 모든 static 메서드  
import static java.lang.Math.random;  // Math.random()만  
import static java.lang.System.out;   // System.out을 out으로 참조 가능.  
```

위와 같이 선언된 경우, 
 `System.out.println(Math.random());` 를 `out.println(random());` 로 쓸 수 있다.
<br>


## 클래스패스 classpath  
컴파일러나 JVM등이 클래스파일의 위치를 찾는데 기준이 되는 파일 경로를 의미한다.   
자바프로그램 실행 시, 컴파일러에 의해 소스코드 `.java` 는 바이트코드 `.class` 로 변환된다. 이 `.class` 파일을 찾는데 `classpath` 에 지정된 경로가 사용된다. `classpath` 는 클래스파일이 포함된 디렉토리와 파일을 콜론으로 구분한 목록으로, 지정된 경로를 모두 검색하여 클래스파일을 찾는다. (첫 번째로 찾은 파일을 사용)  

기본적으로 패키지에 포함되지 않은 소스 파일을 컴파일할 때 `classpath` 를 설정하게 되는데, 이 `classpath` 를 지정할 수 있는 방법으로 __환경 변수 CLASSPATH__ 를 설정하는 방법과, __-classpath__ 옵션을 사용하는 두 가지 방법이 있다.  


### 1. CLASSPATH 환경변수  
환경변수는 운영체제에 지정하는 변수로, 자바는 `CLASSPATH` 라는 환경변수의 값을 참고해서 동작한다. 
이 값을 미리 설정하면 실행할 때마다 -classpath 옵션을 사용하지 않아도 된다.

<img src="7_1.JPG" width=60%>  


### 2. -classpath 옵션  
컴파일, 혹은 실행 시 `-classpath` (단축어 `-cp`)옵션으로 직접 디렉토리를 지정할 수 있다.  

```
java -classpath ".;..;directory" class
```

`;`  구분자  
`.`  현재경로  
`..` 상위경로



#### EX 1) 아래 내용과 같은 소스코드 ClasspathTest.java를 작성 후 컴파일 및 실행
```java
class Cpt {
    public void print(){
        System.out.println("Hello world:)");  
    }
}
 
class ClasspathTest {
    public static void main(String[] args){
        Cpt cpt = new Cpt();
        cpt.print();
    }
}
```
<img src="7_2.jpg">  


#### EX 2) Cpt.java 파일을 lib 아래로 이동 후 실행 - ClassNotFoundException 발생
<img src="7_3.jpg">  


#### EX 3) -classpath 옵션으로 현재디렉토리 및 하위 lib 디렉토리 설정 후 실행
<img src="7_4.jpg">  


## 접근제어자 access modifier  

접근제어자는 멤버, 클래스에 사용되어 해당하는 멤버 또는 클래스를 외부에서 접근하지 못하도록 제한하는 역할을 한다.  
클래스, 멤버변수, 메서드, 생성자 등에 접근제어자가 지정되어있지 않다면 기본값은 default 이다.  

| 제어자 | 같은클래스 | 같은패키지 | 자손클래스 | 전 체 | 설 명 |
|:-----:|:-----:|:-----:|:-----:|:-----:|-----|
| public | O | O | O | O | 접근 제한이 전혀 없음 |
| protected | O | O | O | X | 같은 패키지 내 + 상속관계에 있는 자손클래스에서 접근 가능 |
| default | O | O | X | X | 같은 패키지 내의 클래스에서만 접근 가능 |
| private | O | X | X | X | 같은 클래스 내에서만 접근 가능 |
<br>


__● 캡슐화 encapsulation__  

접근제어자를 사용하는 이유는 클래스 내부에 선언된 데이터의 보호, 객체지향개념의 `캡슐화 encapsulation`와 큰 관계가 있다.  
데이터가 유효한 값을 유지하고, 외부에서 함부로 변경할 수 없도록 하기 위해 외부로부터의 접근을 제어하는 것이다.  
또한 클래스 내부 작업에서만 사용되는 임시 변수나, 부분작업을 처리하기 위한 메서드 등 외부에서 접근할 필요가 없는 멤버들을 클래스 내부에 감추기 위해서 접근제어자를 사용하기도 한다.  
클래스 작성 시, 멤버변수를 `private`나 `protected`로 제한하고, 멤버변수의 값을 읽고 변경할 수 있는 `public` 메서드(getter, setter)를 제공하여 간접적으로 멤버변수의 값을 다룰 수 있도록 하는 방법이 바람직하다.


### 생성자의 접근제어자  

생성자에 접근제어자를 사용하여 인스턴스의 생성을 제한할 수도 있다.  
일반적으로 접근제어자는 클래스의 접근제어자와 같지만, 다르게 지정할 수도 있다. 생성자의 접근제어자가 `private`인 경우, 외부에서 생성자에 접근할 수 없으므로 클래스 내부에서 밖에 인스턴스를 생성할 수 없다. 때문에 생성자가 `private`인 클래스는 다른 클래스의 조상이 될 수 없다. 이러한 경우 클래스 앞에 `final`을 추가하여 상속할 수 없는 클래스라는 것을 알리는 것이 좋다.  
Math 클래스 같은 경우, 몇 개의 상수와 `static` 메서드만으로 구성되어 있기 때문에 인스턴스를 생성할 필요가 없으므로 외부의 불필요한 접근을 막기 위해 생성자의 접근제어자가 `private`으로 설정되어있다.  

<img src="/WEEK6/6_1.JPG" width=90%>  

```java
  public final class Math { // 생성자가 private으로 정의되어 있기 때문에, 클래스에 final 을 사용하고 있다.
    private Math() {}
    ...
  }
```

생성자가 `private`인 클래스의 인스턴스를 사용할 수 있게 하기 위해서는 대신 인스턴스를 생성해서 반환해 주는 `public` 메서드를 제공하는 방법이 있다. 다만 이 메서드는 `public static` 메서드이어야 한다.  



---  
#### REFERENCE  
남궁성, 「자바의 정석」, 도우출판, 2016  
https://effectivesquid.tistory.com/entry/%EC%9E%90%EB%B0%94-%ED%81%B4%EB%9E%98%EC%8A%A4%ED%8C%A8%EC%8A%A4classpath%EB%9E%80
https://opentutorials.org/course/1223/5527
