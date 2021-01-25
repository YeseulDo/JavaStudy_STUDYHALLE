# JAVA ONLINE STUDY _ STUDYHALLE #9  
__과제 : 예외 처리__  
__목표 : 자바의 예외 처리에 대해 학습하기.__

---

## Exception과 Error의 차이는?  

### 프로그램 오류  

프로그램이 실행 중 어떤 원인에 의해 오작동 비정상종료되는 경우, 이러한 결과를 초래하는 원인을 프로그램 에러, 오류라고 한다. 발생시점에 따라 compile-time error 와 runtime error로 나눌 수 있다.  

```
compime-time error : 컴파일 시 발생하는 에러  
runtime error : 실행 시 발생하는 에러  
logical error : 컴파일, 실행에는 문제가 없지만 프로그램이 원래 의도와 다르게 동작하는 에러  
```

자바에서는 실행시 (런타임) 발생할 수 있는 프로그램 오류를 `에러 Error` 와 `예외 Exception` 두 가지로 구분하였다.  
- __에러 Error__  메모리부족이나 스택오버플로우 등 일단 발생하면 프로그램 코드에 의해서 수습될 수 없는 심각한 오류로, 주로 JVM에서 발생시키며 프로그램이 비정상종료된다.  
- __예외 Exception__  프로그램 코드에 의해서 수습될 수 있는 오류로, 미리 예외상황을 예측하고 핸들링가능한 적절한 코드를 작성해놓음으로써 비정상종료를 막을 수 있다.  


## 자바가 제공하는 예외 계층 구조    

자바에서는 런타임시 발생하는 `Error` 및 `Exception` 을 클래스로 정의하고 있다.  

<img>

`Exception` 클래스와 `Error` 클래스도 `Object` 클래스의 자손들이며, 모든 예외의 최고 조상은 `Exception`클래스이다.  


## RuntimeException과 RE가 아닌 것의 차이는?  

Exception 클래스는 일반적으로 아래의 두 그룹으로 나뉜다.  

```
1. RuntimeException 클래스와 그를 상속하는 서브클래스  
2. Exception 클래스와 그를 상속하는 서브클래스  
```

RuntimeException 클래스도 Exception 클래스를 상속하는 서브클래스이긴 하지만, 예외의 성격에 따라 따로 분류한다.  


RuntimeException 및 서브클래스에 속하는 클래스들은 주로 프로그래머의 실수에 의해서 발생될 수 있는 예외들로,  
자바의 프로그래밍 요소와 관계가 깊다. 

예)  
`ArrayIndexOutOfBoundsException` 배열의 범위를 벗어남  
`NullPointerException` 값이 null인 참조변수의 멤버를 호출  
`ClassCastException` 클래스간의 형변환 실수  
`ArithmeticException` 정수를 0으로 나눔  
<br>


반면에 Exception 및 서브클래스에 속하는 클래스들은 주로 외부의 영향에 의해 발생하는 예외로서,  
사용자들의 동작에 의해 발생하는 경우가 많다.  

예)  
`FileNotFoundException` 존재하지 않는 파일의 이름 입력  
`ClassNotFound` 존재하지 않는 클래스의 이름 입력   
`DataFormatException` 잘못된 데이터 형식의 입력  


## 자바에서 예외 처리 방법 (try, catch, throw, throws, finally)  

`예외처리 exception handling` 란 프로그램 실행 시 발생할 수 있는 예기치 못한 예외의 발생에 대비한 코드를 작성하는것으로,  
예외처리의 목적은 예외의 발생으로 인한 실행중인 프로그램의 갑작스러운 비정상종료를 막고, 정상적인 실행상태를 유지할 수 있도록 하는 것이다. 발생된 예외를 처리하지 못하면 프로그램은 비정상종료되며, 처리되지 못한 예외는 JVM의 예외처리기(UncaughtExceptionHandler)가 받아 예외의 원인을 화면에 출력한다.  


### try-catch  

예외처리를 위해 `try-catch` 문을 사용한다.  
하나의 `try` 블럭 다음에는 여러 종류의 예외를 처리할 수 있도록 하나 이상의 `catch` 블럭이 올 수 있다.  

```Java
try {
  // 예외가 발생할 가능성이 있는 코드
} catch (Exception1 e1) { // 처리하고자 하는 예외와 같은 타입의 참조변수를 선언한다.
  // Exception1이 발생했을 경우 이를 처리하기 위한 코드를 작성한다.
} catch (Exception2 e2) { 
  // Exception2가 발생했을 경우 이를 처리하기 위한 코드를 작성한다.
} ...
```


* 흐름

`try` 블럭 내에서 예외가 발생하면, 발생한 예외에 해당하는 클래스의 인스턴스가 만들어진다.  
생성된 예외클래스의 인스턴스와 `catch` 블럭의 괄호 () 에 선언된 참조변수가 `instanceof` 연산자를 이용해 비교되는데,  
여러 개의 `catch` 블럭이 작성된 경우, 가장 위에 작성된 `catch` 블럭부터 순서대로 연산이 이루어진다.  
`instanceof` 연산의 결과가 true 인-발생한 예외의 종류와 일치하는- `catch` 블럭을 찾으면, 내부에 작성된 문장이 수행된다.  

```Java

public class ExceptionEx {
    public static void main(String[] args) {

        int number = 100;
        int result = 0;

        for (int i = 0; i < 10; i++) {
            try {
                result = number / (int) (Math.random() * 10);   // ArithmeticException의 발생가능성이 있는 코드
                System.out.println(result);
                
            } catch (ArithmeticException e) { // ArithmeticException 이 발생한 경우 0을 출력
                System.out.println(0); 
                
            } catch (Exception e) { // ArithmeticException 이외의 예외가 발생한 경우 해당 예외의 정보와 메시지 등을 출력
                e.printStackTrace();
                System.out.println("error message : "+e.getMessage());
            }

        }
    }
}

```

작성된 `catch` 블럭 중 발생한 예외타입의 종류와 일치하는 블럭이 없으면 예외는 처리되지 않는다.  
`try-catch` 문의 마지막에 `Exception` 클래스 타입의 참조변수를 선언한 `catch` 블럭을 작성하면,  
어떤 종류의 예외가 발생하더라도 이 `catch` 블럭에 의해 처리되도록 할 수 있다.  


예외발생시 생성되는 인스턴스는 `catch` 블럭의 괄호()에 선언된 참조변수를 통해 접근할 수 있다.  
이 인스턴스에는 발생한 예외에 대한 정보가 담겨져 있으며, `printStackTrace()`, `getMessage()` 를 통해  
이 정보들을 얻어 예외의 발생원인을 알 수 있다.  

```
  printStackTrace()   예외발생당시 호출스택에 있던 메서드의 정보와 예외메시지를 화면에 출력  
  getMessage()        발생한 예외클래스의 인스턴스에 저장된 메시지를 출력
```

예외가 발생하지 않는 경우에는 `catch` 블럭을 거치지 않고 `try-catch` 문 자체를 빠져나간다.  
  
<sup>* try-catch 문은 괄호 {} 를 생략할 수 없다.</sup>  


#### multi catch  

여러 개의 `catch` 블럭을 `|` 기호를 사용하여 하나의 블럭으로 합칠 수 있다.  
중복된 코드를 줄일 수 있으며, 개수에는 특별히 제한은 없다.  
그러나 멀티 catch 블럭에 연결된 예외클래스가 상속관계에 있다면 컴파일에러가 발생한다. 굳이 적을 필요가...  

```
try {
  ...
} catch (ExceptionA | ExceptionB | ExceptionC e) {
  ...
}
```

`멀티 catch` 는 하나의 블럭으로 여러 예외를 처리하는 것이기 때문에, 발생한 예외가 실제로 어떤 것인지는 알 수 없다.  
때문에, `멀티 catch` 블럭에 사용되는 예외클래스들의 공통분모가 되는 조상 예외 클래스에 선언된 멤버만 사용할 수 있다.  


### throw  
### throws  
### finally  



## 커스텀한 예외 만드는 방법


https://velog.io/@codepark_kr/%EC%9E%90%EB%B0%94-%EC%9D%B4%EB%A1%A0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC
