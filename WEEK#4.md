# JAVA ONLINE STUDY _ STUDYHALLE #4
__목표 : 자바가 제공하는 제어문 학습하기.__

---


## 제어문 control statement 이란?

- 코드의 실행흐름을 바꾸는 역할을 하는 문장  
- 위에서 아래로 순차적으로 진행되는 흐름 이외에, 조건에 따라 문장을 건너뛰고 때로는 같은 문장을 반복해서 수행할 수 있도록 한다.  
- 제어문에는 조건에 따라 다른 문장이 수행되도록 하는 조건문과, 특정문장들을 반복해서 수행하는 반복문이 있다.  

## 조건문 if, switch  

- 조건문은 조건식과 문장을 포함하는 블럭 {} 으로 구성되어 있으며, 조건식의 연산결과에 따라 실행할 문장이 달라진다.
- 조건문에는 if문, switch문이 있는데 if문이 주로 사용된다.
- 경우의 수가 많을 때는 switch문이 효율적이지만, if문보다 제약이 많다.

### ▶ if  

- 가장 기본적인 조건문으로, 조건식과 괄호로 이루어져 있다.
```
  if(조건식) {  
    // 조건식이 true일 때, 괄호 {} 안의 문장들이 수행된다.  
  }  
```

- 조건식은 일반적으로 비교연산자와 논리연산자로 구성된다.  
- 조건식의 결과는 반드시 true, false 중 하나일 필요가 있다.  
- 블럭 block {} 내에는 보통 여러 문장을 넣지만, 한 문장만 넣거나 아무런 문장도 넣지 않을 수 있다.  
  블럭 내의 문장이 한 문장일 경우, 괄호를 생략할 수 있다.  
```
  if (score > 60)  
    System.out.println("합격입니다.");  
```  

#### if-else  
- 조건식이 어느 한 쪽이 참이면 다른 한 쪽이 거짓인 상반된 관계에 있을 경우, if-else 문으로 작성할 수 있다.  
  이러한 경우 두 개의 if문으로 작성할 수도 있지만, if-else문이 하나의 조건식만 계산하면 되므로 더 효율적이고 간단하다.  
```
  if (조건식) {  
    // 조건식이 true 일 때 수행된다.  
  } else {  
    // 조건식이 false 일 때 수행된다.  
  }  
```  

#### if-else if  
- 처리해야 할 경우의 수가 셋 이상인 경우에 사용할 수 있다.  
```
  if (조건식 1) {  
    // 조건식 1이 true 일 때 수행된다.  
  } else if (조건식 2) {  
    // 조건식 2가 true 일 때 수행된다.  
  } else if (조건식 3) {  
    // 조건식 3이 true 일 때 수행된다.  
  } else { 
    // 마지막은 보통 else 블럭으로 끝나며, 생략가능하다.  
    // 위의 어느 조건식도 만족하지 않을 때 수행된다.  
  }
```

- 조건식 1 부터 순서대로 평가하여 결과가 참인 조건식을 만나면 해당 블럭만 수행 후 if문 전체를 벗어난다.
- 결과가 참인 조건식이 하나도 없을 경우 else블럭이 수행되는데, else블럭이 생략된 경우 어떠한 블럭도 수행되지 않는다.  


#### 중첩 if  
- if문 블럭 내에 또 다른 if문을 포함시키는 형태로, 횟수에는 거의 제한이 없다.
```
  if (조건식) {  
    // 조건식 1이 true 일 때 수행된다.  
    
    if (조건식 2) {  
      // 조건식 1, 2가 모두 true일 때 수행된다.  
    } else {  
      // 조건식 1은 true, 2는 false 일 때 수행된다.  
    }  
    
  } else {  
    // 조건식 1이 false 일 때 수행된다.  
  }  
``` 

---  
#### 과제 0. JUnit 5 학습하세요.  
<sup> - 인텔리J, 이클립스, VS Code에서 JUnit 5로 테스트 코드 작성하는 방법에 익숙해 질 것.</sup>
#### 과제 1. live-study 대시 보드를 만드는 코드를 작성하세요.  
<sup> - 깃헙 이슈 1번부터 18번까지 댓글을 순회하며 댓글을 남긴 사용자를 체크 할 것.</sup>  
<sup> - 참여율을 계산하세요. 총 18회에 중에 몇 %를 참여했는지 소숫점 두자리가지 보여줄 것.</sup>  
<sup> - Github 자바 라이브러리를 사용하면 편리합니다.</sup>  
<sup> - 깃헙 API를 익명으로 호출하는데 제한이 있기 때문에 본인의 깃헙 프로젝트에 이슈를 만들고 테스트를 하시면 더 자주 테스트할 수 있습니다.</sup>  
#### 과제 2. LinkedList를 구현하세요.</sup>  
<sup> - LinkedList에 대해 공부하세요.</sup>  
<sup> - 정수를 저장하는 ListNode 클래스를 구현하세요.</sup>  
<sup> - ListNode add(ListNode head, ListNode nodeToAdd, int position)를 구현하세요.</sup>  
<sup> - ListNode remove(ListNode head, int positionToRemove)를 구현하세요.</sup>  
<sup> - boolean contains(ListNode head, ListNode nodeTocheck)를 구현하세요.</sup>  
#### 과제 3. Stack을 구현하세요.  
<sup> - int 배열을 사용해서 정수를 저장하는 Stack을 구현하세요.</sup>  
<sup> - void push(int data)를 구현하세요.</sup>  
<sup> - int pop()을 구현하세요.</sup>  
#### 과제 4. 앞서 만든 ListNode를 사용해서 Stack을 구현하세요.  
<sup> - ListNode head를 가지고 있는 ListNodeStack 클래스를 구현하세요.</sup>  
<sup> - void push(int data)를 구현하세요.</sup>  
<sup> - int pop()을 구현하세요.</sup>  
#### (optional) 과제 5. Queue를 구현하세요.   
<sup> - 배열을 사용해서</sup>  
<sup> - ListNode를 사용해서</sup>  

---  
