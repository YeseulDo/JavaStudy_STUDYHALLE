# JAVA ONLINE STUDY _ STUDYHALLE #4  
__목표 : 자바의 Class에 대해 학습하기.__

---

## 클래스 정의하는 방법


클래스는 객체를 정의해 놓은 것으로 객체를 생성하는 데 사용된다. 클래스와 객체는 제품 설계도와 제품의 관계와 같다고 할 수 있으며, 한 번 설계도를 잘 정의 해 놓으면 반복해서 제품을 만드는 일이 쉬워 지는 것과 같다. Java는 프로그래밍을 위한 많은 유용한 클래스를 제공하고 있으며, 이러한 클래스를 이용해 원하는 기능의 프로그램을 보다 쉽게 작성할 수 있다.  


__1. 데이터와 함수의 결합__  

- 클래스란, 데이터와 함수의 결합으로 서로 관련된 변수들을 정의하고, 이들에 대한 작업을 수행하는 함수들을 함께 정의 한 것.  
  자바와 같은 객체지향언어에서는, 변수(데이터)와 함수를 하나의 클래스에 정의하여 서로 관계가 깊은 변수와 함수를 함께 다룰 수 있다.  

- C언어에서는 문자열을 문자의 배열로 다루지만, 자바에서는 String이라는 클래스로 다룬다.  
  String 클래스에는 문자형 배열이 선언되어 있고, 이러한 문자열을 다루는데 필요한 함수를 함께 정의해 놓았다.  
  이렇게 하나의 클래스 안에 작업대상이 되는 변수와 함수를 함께 정의 해 놓음으로써, 변수와 함수가 유기적으로 연결되어 작업이 간단하고 명료해진다.  


__2. 사용자정의 타입 (user-defined type)__  

- 서로 관련된 변수들을 하나로 묶어서 하나의 타입으로 새로 추가하는 것으로, 자바에서는 클래스가 곧 사용자 정의 타입이 된다.  
  
  
```Java
public class Time {
  private int hour;
  private int minute;
  private float second;
  
  public int getHour() { return hour; }
  public int getMinute() { return minute; }
  public int getSecond() { return second; }
  
  public void setHour(int h) {
    if (h < 0 || h > 23) return;
    hour = h;
  }
  
  public void setMinute(int m) {
    if (m < 0 || h > 59) return;
    minute = m;
  }
  
  public void setSecond(float s) {
    if (s < 0.0f || s > 59.99f) return;
    second = s;
  }

}
```

- 하나의 시간을 구성하는 시, 분, 초를 하나로 묶기 위해, 세 변수를 멤버변수로 갖는 Time클래스를 정의하였다.  
또한, 이 데이터에 주어지는 제약조건들을 설정하기 위해 지정된 값의 유효성을 조건문으로 점검한 후 유효한 값일 경우에 변경할 수 있게 하였다.  


## 객체 만드는 방법 (new 키워드 이해하기)  


### 객체와 인스턴스  

- 객체 : 실제로 존재하는 것, 사물과 같은 유형의 객체 또는 개념과 같은 무형의 객체.  
- 프로그래밍에서의 객체는 클래스에 정의된 내용대로 메모리에 생성된 것.  

- 클래스로부터 객체를 만드는 과정을 __클래스의 인스턴스화__ 라고 하며,  
  어떠한 클래스로부터 만들어진 객체를 그 클래스의 __인스턴스 instance__ 라고 한다.  
- 객체와 인스턴스는 같은 의미이지만, 객체는 인스턴스를 대표하는 포괄적인 의미를 가지며  
  인스턴스는 특정 클래스로부터 만들어진 객체라는 보다 구체적인 의미를 가진다.  

### 객체의 구성요소  

- 객체는 다수의 속성과 다수의 기능으로 이루어진 속성과 기능의 집합이라고 할 수 있으며,  
  객체가 가진 속성과 기능을 그 객체의 __멤버 member__ 라 한다.  

- 속성 property : member variable, attribute, field, state
- 기능 function : method, function, behavior  

- 클래스는 객체를 정의한 것이므로 클래스에는 객체의 모든 속성과 기능이 정의되어 있다.  
  클래스로부터 객체를 생성하면, 클래스에 정의된 속성과 기능을 가진 객체가 만들어지는 것.  
  
  
### 인스턴스의 생성과 사용  

```
  클래스명 변수명;           // 클래스의 객체를 참조하기 위한 참조변수를 선언
  변수명 = new 클래스명();   // 클래스의 객체를 생성 후, 객체의 주소를 참조변수에 저장
```

- new : 클래스타입의 인스턴스를 생성해주는 역할을 한다.  
        Heap 영역에 데이터를 저장할 공간을 할당받고, 객체를 초기화 할 생성자를 호출하며, 그 공간의 참조값(해시코드)을 객체에게 반환한다.

```
package com.studyhalle;

public class TvTest {
    public static void main(String[] args) {
        Tv t;
        t = new Tv();
        t.channel = 7;
        t.channelDown();        
    }
}

class Tv {
    String color;
    boolean power;
    int channel;
    
    void power() { power = !power; }
    void channelUp() { ++channel; }
    void channelDown() { --channel; }
}
```

- 인스턴스는 참조변수를 통해서만 다룰 수 있으며, 참조변수의 타입은 인스턴스의 타입과 일치해야 한다.  


## 메소드 정의하는 방법  



## 생성자 정의하는 방법  
## this 키워드 이해하기  


## 과제 (Optional)  

- int 값을 가지고 있는 이진 트리를 나타내는 Node 라는 클래스를 정의하세요.  
- int value, Node left, right를 가지고 있어야 합니다.  
- BinrayTree라는 클래스를 정의하고 주어진 노드를 기준으로 출력하는 bfs(Node node)와 dfs(Node node) 메소드를 구현하세요.  
- DFS는 왼쪽, 루트, 오른쪽 순으로 순회하세요.  
