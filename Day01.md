#### 메모리 영역

- code : 실행할 프로그램 코드
- data : 전역, 정적
  - 잘못되면 Memory leak 발생.
- heap : 사용자 동적할당 (런 타임에 크기가 결정)
  - Garbege Collecter에 의해서 자동으로 할당.
- stack : 지역, 매개 (컴파일 타임에 의해 크기가 결정)



####  Byte order

- Endianness(엔디언) 

  - Big-endian 

    - 소프트웨어의 디버그를 편하게 해 주는 경향

  - Little-endian

    - 메모리에 저장된 값의 하위 바이트들만 사용할 때 별도의 계산이 필요 없다는 장점

      

- 비트 순서

  - MSB (최상위 비트)
  - LSB (최하위 비트)

  

  ####  Stack 

  ````java
  public class Stack {
  
  	int top;
  	int[] stack;
  	int size;
  	
  	public Stack(int size) {
  
  		this.size = size;
  		stack = new int[size];
  		top = -1;
  	}
  	private void push(int item) {
  
  		stack[++top] = item;
  		System.out.println(stack[top] + " push");
  	}
  	private void peek() {
  		System.out.println(stack[top] + " peek");
  	}
  	private void pop() {
  		System.out.println(stack[top] + " pop");
  		stack[top--] = 0;
  	}
  	private int search(int item) {
  		for (int i = 0; i <= top; i++) {
  			if (stack[i] == item)
  				return (top - i) + 1;
  		}
  		return -1;
  	}
  	private boolean empty() {
  		return size == 0;
  	}
  	
  	public static void main(String[] args) {
  		
  		Stack stk = new Stack(5);
  		stk.push(1);
  		stk.push(5);
  		stk.push(6);
  		stk.pop();
  		stk.pop();
  		stk.peek();
  		
  	}
  }
  ````

  

  

  ####  Linked List

  ````java
  package Day1;
  
  /*
   * @ TITLE Linked List (연결 리스트)
   */
  // List를 구성하는 Node 클래스
  class ListNode{
      private String data;    // 데이터 저장 변수
      public ListNode link;    // 다른 노드를 참조할 링크 노드
      
      public ListNode() {
          this.data = null;
          this.link = null;
      }
      
      public ListNode(String data) {
          this.data = data;
          this.link = null;
      }
      
      public ListNode(String data, ListNode link) {
          this.data = data;
          this.link = link;
      }
      
      public String getData() {
          return this.data;
      }
  }
  public class LinkedList {
      
      private ListNode head;    // ListNode 타입의 head 노드 인스턴스 변수
      
      // LinkedList 생성자
      public LinkedList() {
          head = null;    // head 노드 초기화
      }
      
      // Node 삽입 (중간에 삽입)
      public void insertNode(ListNode preNode, String data) {       
          ListNode newNode = new ListNode(data);    // 새로운 노드 생성
          
          // preNode.link는 preNode의 다음 노드이므로,
          // newNode.link = preNode.link는 새로운 노드의 link가 preNode의 다음 노드를 참조하도록 함. 
          newNode.link = preNode.link;
          
          // preNode의 link가 새로운 노드를 참조하도록 함.
          // 최종적으로 'preNode -> newNode -> 기존 preNode의 다음 노드 '이렇게 구성됨.
          preNode.link = newNode;
      }
      
      // Node 삽입 (마지막에 삽입)
      public void insertNode(String data) {
          ListNode newNode = new ListNode(data);    // 새로운 노드 생성
          if(head == null) {
              // head 노드가 null인 경우 새로운 노드를 참조하도록 함
              this.head = newNode;
          } else {
              // head 노드가 null이 아닌 경우 temp 노드가 head를 참조.
              // tempNode는 마지막 노드를 찾아서 참조하기 위해 사용.
              ListNode tempNode = head;
              
              // temp 노드의 link가 null이 아닐 때까지 다음 노드를 참조.
              // tempNode.link는 다음 노드를 참조하고 있으므로,
              // tempNode = tempNode.link는 tempNode에 다음 노드를 참조하도록 하는 것.
              // while문이 모두 실행되면 tempNode는 가장 마지막 노드를 참조하게 됨.
              while(tempNode.link != null) {
                  tempNode = tempNode.link;    // 다음 노드를 참조
              }
              
              // tempNode(마지막 노드)의 link가 다음 노드를 참조하도록 함. 
              tempNode.link = newNode;
          }
      }
      
      // Node 삭제(중간 노드 삭제)
      public void deleteNode(String data) {
          // preNode는 head가 가리키는 노드를 할당
          ListNode preNode = head;
          // tempNode는 head가 가리키는 노드의 다음 노드. 즉, preNode의 다음 노드를 할당
          ListNode tempNode = head.link; 
          
          // 주어진 데이터가 preNode의 데이터와 일치하는 경우
          // 즉, 첫번째 노드의 데이터와 일치하는 경우
          if(data.equals( preNode.getData() )) {
              // head는 preNode의 다음 노드를 참조하도록 함.
              head = preNode.link;
              // preNode의 link는 null을 할당하여 연결을 끊음.
              preNode.link = null;
          } else {
              // tempNode가 null일 때까지 반복하여 탐색
              while(tempNode != null) {
                  // 주어진 데이터와 temp 노드의 데이터가 일치할 경우.
                  if(data.equals( tempNode.getData() )) {
                      // tempNode가 마지막 노드인 경우
                      if(tempNode.link == null) {
                          preNode.link = null;
                      } else {
                          // tempNode가 마지막 노드가 아닌 경우
                          // preNode의 link는 tempNode의 다음 노드를 참조.
                          // tempNode의 link는 null을 할당하여 다음 노드로의 연결을 끊음.
                          preNode.link = tempNode.link;
                          tempNode.link = null;
                      }
                      break;
                  } else {
                      // 데이터가 일치하지 않을 경우 
                      // preNode에 tempNode를 할당하고, tempNode에 다음 노드 할당.
                      preNode = tempNode;
                      tempNode = tempNode.link;
                  }
              }
          }
      }
      
      // Node 삭제(마지막 노드 삭제)
      public void deleteNode() {
          ListNode preNode;
          ListNode tempNode;
          
          // head 노드가 null인 경우 모든 노드가 삭제되었으므로 return
          if(head == null) {
              return;
          }
          
          // head 노드의 link가 null인 경우
          // 노드가 1개 남았을 경우
          if(head.link == null) {
              // head에 null을 할당하여 남은 노드와의 연결을 끊음.
              head = null;
          } else {
              // preNode는 head가 가리키는 노드를 할당
              preNode = head;
              // tempNode는 head가 가리키는 노드의 다음 노드. 즉, preNode의 다음 노드를 할당
              tempNode = head.link;     
              
              // tempNode의 link가 null이 아닐 때까지 한 노드씩 다음 노드로 이동.
              // preNode는 tempNode를 할당하고
              // tempNode는 tempNode의 다음 노드를 할당.
              // 이렇게 하면 preNode는 마지막 노드의 이전 노드가 되고, tempNode는 마지막 노드가 됨.
              while(tempNode.link != null) {
                  preNode = tempNode;
                  tempNode = tempNode.link;
              }
              
              // preNode의 link를 null로 만들어서 가장 마지막 노드를 삭제
              // 즉, preNode의 다음 노드인 tempNode로의 연결을 끊음.
              preNode.link = null;
          }
      }
      
      // Node 탐색
      public ListNode searchNode(String data) {
          ListNode tempNode = this.head;    // temp 노드에 head가 가리키는 첫 번째 할당.
          
          // temp 노드가 null이 아닐 때까지 반복하여 탐색
          while(tempNode != null) {
              // 주어진 데이터와 temp 노드의 데이터가 일치할 경우 해당 temp 노드를 return
              if(data.equals(tempNode.getData())) {
                  return tempNode;
              } else {
                  // 데이터가 일치하지 않을 경우 temp 노드에 다음 노드 할당.
                  tempNode = tempNode.link;
              }
          }
          
          return tempNode;
      }
      
      // 리스트의 노드를 역순으로 구성
      public void reverseList() {
          ListNode nextNode = head;    // head가 참조하는 첫번째 노드를 할당.
          ListNode currentNode = null;
          ListNode preNode = null;
          
          // nextNode가 순차적으로 이동하며 currentNode의 link가 preNode를 참조하도록 함.
          // 1) preNode를 currentNode 위치로 이동
          // 2) currentNode는 nextNode 위치로 이동
          // 3) nextNode는 다음 노드 위치로 이동
          // 4) currentNode의 link는 preNode를 참조하도록 함
          while(nextNode != null) {
              preNode = currentNode;    // preNode는 currentNode 위치로 이동
              currentNode = nextNode;    // currentNode는 nextNode 위치로 이동
              nextNode = nextNode.link;    // nextNode는 다음 노드 위치로 이동
              currentNode.link = preNode;    // currentNode의 link에 preNode를 할당하여 역순으로 설정
          }
          
          head = currentNode;    // currentNode가 마지막 노드를 가리킬 때, head는 currentNode를 참조하도록 함.
      }
      
      // 연결 리스트에 저장된 모든 데이터를 출력
      public void printList() {
          ListNode tempNode = this.head;    // tempNode에 head가 가리키는 첫번째 노드를 할당
          
          // tempNode가 null이 아닐 때까지 반복하여 출력
          while(tempNode != null) {
              System.out.print(tempNode.getData() + " ");
              tempNode = tempNode.link;    // temp 노드에 다음 노드(tempNode.link) 할당.
          }
          System.out.println();
      }
   
      public static void main(String args[]) {
          LinkedList linkedList = new LinkedList();    // 연결 리스트 생성
          String str = "wed";
          
          linkedList.insertNode("sun");
          linkedList.insertNode("mon");
          linkedList.insertNode("tue");
          linkedList.insertNode("wed");
          linkedList.insertNode("thu");
          linkedList.insertNode("fri");
          linkedList.insertNode("sat");
          linkedList.printList();
          
          System.out.println(linkedList.searchNode(str).getData());
          
          linkedList.deleteNode(linkedList.searchNode(str).getData());
          linkedList.printList();
          
          str = "sun";
          
          linkedList.deleteNode(linkedList.searchNode(str).getData());
          linkedList.printList();
          
          linkedList.reverseList();
          linkedList.printList();
      }
      
  }
  
  
  
  ````

  

  

  ​	

  