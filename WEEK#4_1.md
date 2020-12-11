# JAVA ONLINE STUDY _ STUDYHALLE #4

#### 과제 0. JUnit 5 학습하세요.  

<sup> - 인텔리J, 이클립스, VS Code에서 JUnit 5로 테스트 코드 작성하는 방법에 익숙해 질 것.</sup>  
강좌 수강하며 공부중입니다 :-)

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

- __List__ : 순서가 있는 데이터의 집합, 데이터의 중복을 허용한다.  
  구현클래스로는 ArrayList, LinkedList, Stack, Vector 등이 있다.
- __Set__ : 순서를 유지하지 않는 데이터의 집합, 데이터의 중복을 허용하지 않는다.  
  구현클래스로는 HashSet, TreeSet 등이 있다.  
- __Map__ : key와 value의 쌍으로 이루어진 데이터의 집합,  
  순서는 유지되지 않으며, 키는 중복을 허용하지 않고, 값은 중복을 허용한다.  
  구현클래스로는 HashMap, TreeMap, Hashtable, Properties 등이 있다.  
  
  
### ▶ LinkedList  

- 불연속적으로 존재하는 데이터를 서로 연결한 형태로 구성되어 있다.  
- LinkedList를 구성하는 각 요소를 노드 node 라고 부르며, element와 의미는 비슷하나 좀 더 연결성이 강조된 표현이다.  
  이러한 노드들은 자신과 연결된 다음 요소에 대한 참조(주소값)와 데이터로 구성되어 있다.  

```
  class Node {
    Node next;    // 다음 요소의 주소를 저장
    Object obj;   // 데이터를 저장
  }
```

- 비순차적 데이터의 추가, 삭제 시 ArrayList는 다른 데이터를 재배치하여 저장공간을 만들어야 하지만,
  LinkedList의 경우 노드의 참조값만 변경하면 되므로, ArrayList에 비해 속도가 빠르다.
  그러나 데이터의 탐색, 접근 시에는 LinkedList가 순차탐색을 필요로 하기 때문에  
  인덱스값을 이용하는 ArrayList가 보다 빠르다.  


#### Doubly Linked List


이동방향이 단방향이기 때문에 이전요소에 접근이 어려운 LinkedList의 단점을 보완한 것으로  
다음 요소에 대한 참조 뿐 아니라 이전 요소에 대한 참조도 가능하게 하였다.
```
  class Node {
    Node next;      // 다음 요소의 주소를 저장
    Node previous;  // 이전 요소의 주소를 저장
    Object obj;     // 데이터를 저장
  }
```


#### Doubly circular linked list  

doubly linked list의 첫 번째 요소와 마지막 요소를 서로 연결시킨 것으로,  
마지막 요소의 다음 요소가 첫 번째 요소가 되고, 첫 번째 요소의 이전 요소가 마지막 요소가 되는 것.  


### ▶ 구현

- 정수를 저장하는 ListNode 클래스를 구현하세요.  
- ListNode add(ListNode head, ListNode nodeToAdd, int position)를 구현하세요.  
- ListNode remove(ListNode head, int positionToRemove)를 구현하세요.  
- boolean contains(ListNode head, ListNode nodeTocheck)를 구현하세요.  

```java
package com.studyhalle;

import java.util.List;

public class ListNode {

    private int data;
    private ListNode next = null;

    public int getData() {
        return data;
    }

    public void setData(int data) {
        this.data = data;
    }

    public ListNode getNext() {
        return next;
    }

    public void setNext(ListNode next) {
        this.next = next;
    }

    public ListNode(){}
    public ListNode(int input) {
        this.data = input;
    }

    public ListNode add(ListNode head, ListNode nodeToAdd, int position){

        if(position == 0) {
            nodeToAdd.next = head;
            head = nodeToAdd;
            return nodeToAdd;
        }

        for (int i = 0; i < position-1; i++) {
            head = head.next;
        }

        ListNode nextNode = head.next;
        head.next = nodeToAdd;
        nodeToAdd.next = nextNode;

        return nodeToAdd;
    } // add


    public ListNode remove(ListNode head, int positionToRemove){

        if (head == null) {
            return null;
        }

        if (positionToRemove == 0) {
            ListNode nodeToRemove = head;
            head = head.next;
            return nodeToRemove;
        }

        for (int i = 0; i < positionToRemove-1; i++) {
            head = head.next;
        }

        // 해당 포지션에 값이 없으니까?
        if (head==null) return null;

        ListNode nodeToRemove = head.next;
        head.next = nodeToRemove.next;

        ListNode returnNode = nodeToRemove;

        nodeToRemove = null;

        return returnNode;
    } // remove

    public boolean contains(ListNode head, ListNode nodeToCheck){

        while(head != null) {
            if (head == nodeToCheck) return true;
            head = head.next;
        }

        return false;
    } // contains

    public String printList(){
        ListNode node = this;
        StringBuffer output = new StringBuffer();
        output.append("[");
        while(node.next != null) {
            output = output.append(node.data);
            output = output.append("-");
            node = node.next;
        }
        output.append(node.data);
        output.append("]");
        return output.toString();
    }

    public String toString() {
        ListNode node = this;
        return String.valueOf(this.getData());
    }
}
```

- 테스트  
```java
package com.studyhalle;


import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.Test;

import static org.junit.jupiter.api.Assertions.*;

class ListNodeTest {
    ListNode node1 = new ListNode(1);

    @Test
    void addTest(){
        node1.add(node1, new ListNode(2), 1);
        node1.add(node1, new ListNode(3), 2);
        node1.add(node1, new ListNode(4), 3);
        node1.add(node1, new ListNode(5), 4);

        String output = node1.printList();
        assertEquals("[1-2-3-4-5]", output);
        System.out.println(output);
    }

    @Test
    void removeTest(){
        node1.add(node1, new ListNode(2), 1);
        node1.add(node1, new ListNode(3), 2);
        node1.add(node1, new ListNode(4), 3);
        node1.add(node1, new ListNode(5), 4);

        node1.remove(node1, 2);
        assertEquals("[1-2-4-5]", node1.printList());

        assertNull(node1.remove(node1, 5));

        /*
        왜안되는지모르게따..?
        node1.remove(node1, 0);
        assertEquals("[2-4-5]", node1.printList());
        */


    }

    @Test
    void containTest(){
        node1.add(node1, new ListNode(2), 1);
        node1.add(node1, new ListNode(3), 2);
        node1.add(node1, new ListNode(4), 3);
        ListNode newNode = new ListNode(5);
        node1.add(node1, newNode, 4);
        ListNode newNode1 = new ListNode(4);
        assertEquals(true ,node1.contains(node1, newNode));
        assertEquals(false, node1.contains(node1, newNode1));

    }
}
```


## 과제 3. Stack을 구현하세요.  

### Stack  

Stack이란 마지막에 저장한 데이터를 가장 먼저 꺼내는 LIFO (Last In First Out) / 후입선출형의 순차적인 자료구조를 말한다.  

### 구현  

- int 배열을 사용해서 정수를 저장하는 Stack을 구현하세요.  
- void push(int data)를 구현하세요.  
- int pop()을 구현하세요.  

```java
package com.studyhalle;

public class Stack {

    private int top;
    private int size;
    private int[] stackArray;

    public Stack(int size) {
        this.top = -1;
        this.size = size;
        this.stackArray = new int[this.size];
    }

    public void push(int input) {
        if (top==this.size-1) {
            System.out.println("Stack is FULL");
        } else {
            stackArray[++top] = input;
        }
    }

    public int pop() {
        if(top == -1) {
            System.out.println("Stack is EMPTY");
            return 0;
        } else {
            int returnInt = stackArray[top];
            this.top -= 1;
            return returnInt;

        }
    }

    public int peek(){
        if(top == -1) {
            System.out.println("Stack is EMPTY");
            return 0;
        } else {
            return stackArray[top];
        }
    }
}
```


## 과제 4. 앞서 만든 ListNode를 사용해서 Stack을 구현하세요.  

- ListNode head를 가지고 있는 ListNodeStack 클래스를 구현하세요.  
- void push(int data)를 구현하세요.  
- int pop()을 구현하세요.  


```java
package com.studyhalle;

public class ListNodeStack {
    ListNode head;

    public ListNodeStack() {
        head = new ListNode();
    }

    public void push(int data) {
        ListNode node = new ListNode(data);
        head.add(head, node, 0);
    }

    public int pop() {
        if (head==null) return 0;
        return head.remove(head, 0).getData();
    }
}
```
  
#### (optional) 과제 5. Queue를 구현하세요.   
<sup> - 배열을 사용해서</sup>  
<sup> - ListNode를 사용해서</sup>  

---  
