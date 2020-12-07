# JAVA ONLINE STUDY _ STUDYHALLE #4

#### 과제 0. JUnit 5 학습하세요.  
<sup> - 인텔리J, 이클립스, VS Code에서 JUnit 5로 테스트 코드 작성하는 방법에 익숙해 질 것.</sup>
#### 과제 1. live-study 대시 보드를 만드는 코드를 작성하세요.  
<sup> - 깃헙 이슈 1번부터 18번까지 댓글을 순회하며 댓글을 남긴 사용자를 체크 할 것.</sup>  
<sup> - 참여율을 계산하세요. 총 18회에 중에 몇 %를 참여했는지 소숫점 두자리가지 보여줄 것.</sup>  
<sup> - Github 자바 라이브러리를 사용하면 편리합니다.</sup>  
<sup> - 깃헙 API를 익명으로 호출하는데 제한이 있기 때문에 본인의 깃헙 프로젝트에 이슈를 만들고 테스트를 하시면 더 자주 테스트할 수 있습니다.</sup>  


## 과제 2. LinkedList를 구현하세요.  

### ▶ Collections Framework  

- __Collection__ : 다수의 데이터, 데이터 그룹  
  __Framework__ : 표준화 된 프로그래밍 방식  
  컬렉션 프레임웍이란, 데이터군을 저장하는 클래스들을 표준화 한 설계  
- 컬렉션 프레임웍은 다수의 데이터를 다루는 데 필요한 다양한 클래스를 제공하며,  
  인터페이스와 다형성을 이용한 객체지향적 설계를 통해 표준화 되어 있다.  
  따라서 사용법을 익히기에도 편리하며, 재사용서이 높은 코드를 작성할 수 있다.  

#### 핵심 인터페이스  

컬렉션 프레임웍에는 컬렉션 데이터 그룹을 크게 크게 3가지 타입으로 정의하고 있으며,  
각 컬렉션을 다루는데 필요한 기능을 가진 3개의 인터페이스를 정의하였다.  
또한 List와 Set의 공통적인 부분을 다시 뽑아서 새로운 인터페이스 Collection을 추가로 정의하였다.  

// 상속계층도

- __List__ : 순서가 있는 데이터의 집합, 데이터의 중복을 허용한다.  
  구현클래스로는 ArrayList, LinkedList, Stack, Vector 등이 있다.
- __Set__ : 순서를 유지하지 않는 데이터의 집합, 데이터의 중복을 허용하지 않는다.  
  구현클래스로는 HashSet, TreeSet 등이 있다.  
- __Map__ : key와 value의 쌍으로 이루어진 데이터의 집합,  
  순서는 유지되지 않으며, 키는 중복을 허용하지 않고, 값은 중복을 허용한다.  
  구현클래스로는 HashMap, TreeMap, Hashtable, Properties 등이 있다.  
  
  
### ▶ LinkedList  


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
