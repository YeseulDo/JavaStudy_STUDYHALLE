# JAVA ONLINE STUDY _ STUDYHALLE #9  
__과제 : 예외 처리__  
__목표 : 자바의 예외 처리에 대해 학습하기.__

---

## Exception과 Error의 차이는?  

### 프로그램 오류  

프로그램이 실행 중 어떤 원인에 의해 오작동하거나 비정상종료되는 경우, 이러한 결과를 초래하는 원인을 프로그램 에러, 오류라고 한다.  
발생시점에 따라 compile-time error 와 runtime error로 나눌 수 있다.  

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




## 커스텀한 예외 만드는 방법


https://velog.io/@codepark_kr/%EC%9E%90%EB%B0%94-%EC%9D%B4%EB%A1%A0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC
