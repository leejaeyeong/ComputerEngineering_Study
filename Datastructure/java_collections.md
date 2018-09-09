
## Java Collection Framework (JCF)
Java에서 데이터를 저장하는 기본적인 자료구조를 모아 제공해 줌  
상속구조는 다음과 같다.   

 - `List : 순서가 있는 저장공간`
   - LinkedList  
   - Stack  
   - Vector  : 동기화 보장  ---> 상대적느림  
   - ArrayList  : 동기화 보장 X

 - `Set : 집합적인 저장 공간`
   - HashSet : Set 계열의 대표, 동기화 지원하지 않음   
   - SortedSet : 정렬을 위한 Set 계열 클래스
   - TreeSet

 - `Map : 키와 값으로 데이터 핸들`
   - Hashtabel : 동기화 보장 Map 계열 클래스 -->상대적느림  
   - HashMap  : 동기화 보장 하지 않음 Map 계열 클래스  
   - SortedMap : 정렬을 위한 Map 계열 클래스  
   - TreeMap


## 각 컬렉션의 특징은?
**List** - 순서가 있는 데이터의 집합임, 중복허용  
**Set** - 순서를 유지하지 않는 데이터의 집합, 중복을 허용하지 않음  
**Map** - key와 value의 쌍으로 이루어진 데이터의 집합 순서는 유지되지 않고, 키는 중복을 허용하지 않으며 값의 중복은 허용한다  
내부적으로 SoredMap을 구성하고 있기 때문에 key 값에 대해 정렬이 이루어진다. --> 이로인해 값을 추가할 때 상대적으로 시간이 오래걸

## 동기화(Synchronization)  
동기화는 작업들 사이의 수행 시기를 맞추는 것을 말함
List, Set, Map은 동기화를 지원하는 것도 있지만 그렇지 않은 것도 있음. 동기화가 제공된다고 무조건 좋은 것은 아니고 **성능차를 고려할 필요가 있기 때문에 상황에 따라서 적절하게 사용할 줄 알아야함.**  

Vector는 동기화를 보장하고 ArrayList는 동기화를 보장하지 않는다. 하지만 동기화를 보장하지 않는다고 하더라도 **synchronizedList**라는 키워드로 동기화하도록 구현할 수 있음.   
(동기화를 제공하지 않는 Set에서도 적용됨)

동기화를 지원하지 않은 Map도 위와 같이 **synchronizedMap**이라는 키워드로 동기화를 지원할 수 있지만 **ConcurrentHashMap**의 성능이 더 좋기 때문에 **ConcurrentHashMap**을 사용하는 것이 더 좋다.    

**그 이유는?**   
**ConcurrentHashMap**는 동기화를 진행할 때 블록 전체를 고정시키지 않고 Map을 여러 조각으로 나누어 부분적으로 고정(Lock)하는 형태로 구현되어 있다. 이것은 다중 스레드 환경에 더 효율성을 보이기 때문이다.   
--> cpu 스레드가 많아져서 분할적으로 처리할 수 있는 환경이  효율적이라는 의미

## 정리
### `List : 순서가 있고 중복 허용`

   - **ArrayList** - 상대적으로 빠름, 순차적 접근 가능  
   - **Vector** - ArrayList의 이전 버전임, 모든 메소드가 동기화 됨   
   -  **LinkedList** - 순서가 변경 될 경우 노드 링크를 변경하면 되므로 삽입 또는 삭제를 많이 사용하는 경우 빠른 속도를 보임

### `Set : 순서의 의미가 없고 중복을 허용하지 않음`  
   - **HashSet** - 빠른 접근 속도, 순서를 예측할 수 없다  
   - **LinkedHashSet** - 추가된 순서대로 접근 가능  
   - **TreeSet** - 정렬 방법을 지정할 수 있음  

### `Map : 순서는 유지되지 안고 키 중복은 허용하나 값은 허용하지 않음 `  
   - **HashMap** - 중복 X, 순서를 보장 X, null 값 허용  
   - **Hashtable** - HashMap 보다 느리지만 동기화 가능 null 허용  
   - **TreeMap** - Key, Value로 빠른 검색, 내부 정렬로 인해 느림   
   - **LinkedHashMap** - HashMap과 동일 but 입력 순서대로 접근 가능
*************

## 예

 <pre><code>
import java.util.HashMap //HashMap을 사용하기 위해  
import java.util.Iterator //반복자라는 의미로 데이터를 검색할 때 쓰임(모든 자료구조형에 사용가능)
public class MainClass {  
public static void main(String[] args) {  
HashMap< Integer, String> hashMap = new HashMap< Integer,String>();  // hashMap 객체 생성 key,value를 입력 받음
hashMap.put(0,"str0");  //key와 value를 put 함수로 저장(다른 Collection의 경우에는 add를 쓰기도함)  
hashMap.put(1,"str1");   
hashMap.put(2,"str2");   
hashMap.put(3,"str3");   
System.out.println(hashMap.toSring()); //hashMap에 저장된 key 0~3에 대응하는 value를 출력
hashMap.remove(2); //key 2에 해당하는 데이터 삭제
System.out.println(hashMap.toSring());  // key 0,1,3에 대한 value 출력
hashMap.clear();  //컬렌션에 모든 key와 value 삭제
System.out.println(hashMap.toSring());  // 출력결과 {}
hashMap.put(0,"str0");  
hashMap.put(1,"str1");   
hashMap.put(2,"str2");   
hashMap.put(3,"str3");     
System.out.println(hashMap.toSring());  //key 0~3에 대응하는 value를 출력  
</code></pre>  

hashMap의 특징으로 key에 대한 vlaue를 찾기 때문에 처리속도가 빠르지만 key를 추가할 경우 정렬 과정을 거치기 때문에 상대적으로 속도가 걸림.  

## 어떤 경우에 사용하는가?
### List

- Vector, ArrayList, LinkedList  
 일반적인 경우에 ArrayList를 가장 많이 사용함. 처리 속도가 제일 빠름 Vector 같은 경우 synchronized 라는 동기화 코드가 있어서 메소드를 호출 할때 마다 동기화를 진행해 비교적 처리속도가 느림.LinkedList 같은 경우 중간 중간에 있는 데이터를 수정하는 빈도가 높으면  좋음  

### Set  
- HashSet, LinkedHashSet,TreeSet  
HashSet은 TreeSet에 비해 처리속도가 매우 빨라서 일반적으로 사용되는것은 HashSet, LinkedHashSet은 HashSet과 동일 하지만 순차적접근이 가능하기 때문에 그런 경우에 사용함. TreeSet은 객체의 순서를 유지해야할 때 사용.

### Map
- HashMap, Hashtable, LinkedHashMap,TreeMap  
Hashtable은 동기화 코드가 있어서 동기화가 필요한 부분에서 사용하고 HashMap은 동기화 처리가 없기 때문에 빠른 처리속도를 요구할 때 사용한다. TreeMap은 정렬 때문에 가장 느리고 데이터 정렬을 필요로 하는 경우에 사용한다. LinkedHashMap은 Hashmap과 거의 동일 순차적으로 자료에 대해 순차적 접근이 필요한 경우 사용함.
