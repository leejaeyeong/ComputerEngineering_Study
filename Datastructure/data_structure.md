## Data_structure
### 1. 만들어진 이유

-  CPU : 중앙정보처리장치, 레지스터, 데이터를 연산/ 처리하는 가장 중요한 부분

- Memory : RAM(Random Access Memory), CPU에서 직접 접근이 가능, 사용자가 자유롭게 내용을 일고 쓰고 지울 수 있다. 휘발성 기억장치, 빠르다

- Storage : HDD, SSD, 비휘발성 기억장치, 용량이 아주 크지만 느리다.

- **위와 같은 이유로 데이터는 기본적으로 스토리지에 저장된다. 하지만 스토리지는 매우느리기 때문에 CPU와 함께 일하기에는 속도면에서 부족하므로 어떠한 프로그램을 실행하면 해당 프로그램과 데이터는 메모리즉 RAM으로 옮겨진다. 고로 CPU는 메모리에 로드된 데이터를 이용해서 여러 가지 일을 하므로 실행속도를 결정하는 것은 대체로 메모리이고 자료구조를 사용하고 만들어진 이유는 메모리의 효율적인 사용이라고 할 수 있다.**  

### 2. C언어의 메모리 구조

- 데이터(DATA), 스택(STACK) , 힙(HEAP)

- 데이터(DATA) 영역

 · 전역 변수와 정적(static) 변수가 할당되는 영역
 · 프로그램을 시작하면 할당하고, 프로그램을 종료하면 메모리에서 해제함  

- 스택(STACK) 영역

 · 함수 호출 시 생성되는 지역 변수와 매개변수가 저장되는 영역
 · 함수 호출이 완료되면 사라짐

- 힙(HEAP) 영역

 · 필요에 따라 동적으로 메모리를 할당
  (힙 영역은 할당해야 할 메모리 영역의 크기를 프로그램이 실행되는 동안 (run time) 결정해야 하는 경우에 사용한다.)


### 3. Stack

- LIFO, Last In First Out

- Stack에 Data를 넣을 경우 => PUSH

- Stack에서 Data를 꺼낼 경우 => POP

- 꼭대기 => Top 밑바닥 => BOTTOM

### 4. Queue

- FIFO , First In First Out

- Queue에서 Data를 넣는 작업 => Enqueue

- Queue에서 Data를 꺼내는 작업 => Deque

- 배열 Queue를 구현시  Dequeue시 시간 복잡도 O(n) 하지만 Ring Buffer로 구현시 O(1)

### 5. Dequeue

- **Double-ended Queue의 약자로 양쪽 끝에서 삽입과 삭제가 모두 가능한 자료구조이다. 큐와 스택을 합친 형태로 생각할 수 있다.**

- 앞과 뒤에서 insert와 delete가 좋다.

- 스케줄링이 복잡해질수록 큐와 스택보다 덱이 효율이 잘나오는 경우가 있으며 우선순위를 조절하게 될 때 큐나 스택보다는 덱의 사용이 더 유용하다.

### 6. List

- List는 데이터를 순서대로 나열한(줄지어 늘어놓은)자료구조이다.

- Array로 만든 선형 리스트

 - Data를 insert시 이후의 모든 elements를 하나씩 뒤로 옮긴다.

 - Data를 Delete시 모든 elements를 하나씩 앞으로 땡긴다.

 - 단점 : 쌓인 Data의 크기를 미리 알아야 하며 Data의 insert, delete시 data를 모두 옮겨야 하므로 효율이 좋지 않음

- Pointer로 만든 LinkedList

 - Linked list에 데이터를 삽입할 때 노드용 객체를 만들고, 삭제할 때 노드용 객체를 없애면 배열로 만든 선형 리스트에서의 밀고 당기는 문제를 해결 가능하다.

- Doubly Circular Linked List

 - Circular List : Linear list의 tail node 가 head node의 node를 가리키면 Circular list라고 한다.

 - Doubly linked list : Linear LinkedList의 가장 큰 단점인 다음 node를 찾기 쉽지만 앞쪽의 node를 찾을 수 없다는 것을 개선

### 7. Tree

- Breadth-first Search : low level 부터 왼쪽에서 오른쪽 방향으로 검색

-  Depth-first Search : leaf까지 내려가면서 검색하는 것을 우선순위로 탐색

- Preorder

 - Searching Order : Visit Node => Left Child => Right Child

- Incorder

 - Searching Order : Left Child => Visit Node => Right Child

- Postorder

 - Searching Order : Left Child => Right Child => Visit Node

### 8. Graph

- Undirected Graph : 두 정점을 연결하는 간선의 방향이 없는 Graph

- Directed graph : 간선이 있는 그래프

- Complete graph : 각 정점에서 모든 정점을 연결하여 가능한 최대의 간선 수를 가진 graph.

- Weight graph : 정점을 연결하는 간선에 가중치(weight)를 할당한 Graph
