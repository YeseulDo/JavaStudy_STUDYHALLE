# JAVA ONLINE STUDY _ STUDYHALLE #7  
__과제 : 패키지__  
__목표 : 자바의 패키지에 대해 학습하기.__

---

## package 키워드  

패키지란, 클래스의 묶음이다.  
서로 관련된 클래스 또는 인터페이스를 그룹단위로 묶어놓음으로써 클래스를 효율적으로 관리할 수 있다.  
같은 이름의 클래스일지라도 서로 다른 패키지에 존재하는 것이 가능하다.  
클래스의 이름은 패키지명을 포함한다. java.lang.String  

클래스나 인터페이스의 소스파일(.java)에서 첫 번째 문장으로 `package 패키지명;` 을 추가한다.  


클래스가 물리적으로 하나의 클래스파일 (.class) 인것과 같이 패키지는 물리적으로 하나의 디렉토리이다.
어떤 패키지에 속한 클래스는 해당 디렉토리에 존재하는 클래스파일이어야 한다.  

하나의 소스파일에는 첫 번째 문장으로 한 번의 패키지선언만을 허용한다.

모든 클래스는 반드시 하나의 패키지에 속해야 한다.
자신이 속할 패키지가 지정되지않은 클래스는 자동적으로 `이름없는 패키지 unnamed package`에 속하게 된다.  

점(.)을 구분자로 하여 계층구조로 구성할 수 있다.

대소문자를 모두 허용하지만, 클래스명과 구분하기 위해 소문자로 하는 것을 원칙으로 하고 있다.  


## import 키워드  

클래스 코드 작성 전 사용하고자 하는 클래스의 패키지를 미리 명시하는데 사용되며, import문을 이용해 명시된 클래스는 소스코드 작성 시 패키지명을 생략가능하다.

컴파일러에게 소스파일에 사용된 클래스의 패키지에 대한 정보를 제공하는 역할로, 컴파일 시 컴파일러는 import문을 통해 소스파일에 사용된 클래스들의 패키지를 알아 낸 다음, 모든 클래스 이름 앞에 패키지명을 붙여준다.  

import문은 package문 다음, 클래스 선언문 이전에 위치하며, 한 소스파일에 여러번 선언할 수 있다.  

1. package  
2. import  
3. 클래스선언  

import 패키지명.클래스명;  
import 패키지명.*; // 같은 패키지에서 여러 개의 클래스가 사용될 때, import문을 여러번 작성 할 필요가 없다. 또한, 하위패키지의 클래스는 포함하지 않는다.  

import java.util.*;  
import java.text.*;  
import java.*; (x)  

### static import  

static 멤버를 호출할 때 클래스 이름을 생략할 수 있다. 특정 클래스의 static 멤버를 자주 사용할 경우 편리하다.  

import static java.lang.Integer.*;  // Integer클래스의 모든 static 메서드  
import static java.lang.Math.random; // Math.random()만  
import static java.lang.System.out; // System.out을 out으로 참조 가능.  

System.out.println(Math.random());  
out.println(random());


## 클래스패스  
컴파일러나 JVM등이 클래스의 위치를 찾는데 사용되는 경로.

## CLASSPATH 환경변수  
## -classpath 옵션  
## 접근지시자  
