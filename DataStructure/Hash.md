해시(Hash)
==========
**해시(Hash)는 입력 데이터를 고정된 길이의 데이터로 변환된 값**을 말합니다. 
다른 말로는 '해시 값(Hash value), 해시 코드, 체크섬' 이라고도 합니다. 
이러한 해시는 뒤에서 알아볼 '해시 함수'에 의해서 얻게 됩니다. 
간단하게 말하자면, 데이터의 KEY 값이 해시 함수를 통해서 변환된 간단한 정수입니다. 
이렇게 정수로 변환된 해시는 배열의 인덱스, 위치, 데이터 값을 저장하거나 검색할 때 활용됩니다.

### 좋은 해시?
1. 계산 속도가 빨라야 한다.
2. 결괏값이 다양해야 한다. (특정값만 자주 나오지 ❌)

## 01. 자료구조의 특징
* 키(KEY)에 데이터(Value)를 매핑할 수 있는 데이터 구조
* 해시 함수를 통해 키의 데이터를 배열에 저장할 수 있는 주소(인덱스 번호)를 계산
* 키를 통해서 저장된 데이터를 빠르게 찾고, 저장 및 탐색 속도가 획기적으로 빨라짐

## 02. 알아둘 용어
### 👍 해시 함수(Hash Function)
> 임의의 데이터를 고정된 길이의 값으로 리턴해주는 함수
   
**해시 함수(Hash function)는 입력받은 데이터를 해시 값으로 출력시키는 알고리즘**을 말합니다.  
1. 어떤 입력 값에도 항상 고정된 길이의 해시값을 출력한다.
2. 입력 값의 아주 일부만 변경되어도 전혀 다른 결과 값을 출력한다.(눈사태 효과)
3. 출력된 결괏값을 통해 입력값을 유추할 수 없다.
 
이렇게 출력된 해시 값은 알고리즘에 따라 다양한 결과를 보입니다.   
그렇기 때문에 함수는 목적에 맞게 다양하게 설계되고 자료구조, 캐시, 검색, 에러 검출, 암호 등으로 유용하게 사용됩니다.   

## 💥 해시 충돌 (Hash Collision)   
아무리 해시 함수가 좋아도 세상의 모든 것을 고정된 크기로 바꿀 수 없을 것 같습니다.    
그래서 서로 다른 대상이 동일한 해시 값을 가지는 현상을 해시 충돌이라고 부릅니다.   
이 현상을 해결하는 방법은 두 가지가 존재합니다.   
해시 충돌이 적은 함수가 좋은 해시함수라고 불립니다.   

### ⛓️ 분리 연결법 (Separate Chaining)   
분리 연결법은 충돌이 발생하면 연결된 새로운 공간을 사용하는 방법 입니다. (Linked List)   
![img](https://github.com/99MinSu/CS-Study/assets/89891084/19444222-6d8c-4c80-8969-6759ba24ce2e)    
분리 연결법은 데이터가 아파트처럼 모여있다고 생각하시면 좋습니다.   
위의 예시에서 apple은 1층 1호, dragon은 1층 2호라고 볼 수 있을 것 같습니다.

### 😋 장단점
연결 리스트라는 자료 구조를 사용하기 때문에 보다 유연하게 사용할 수 있습니다.   
또한, 해시 값을 그대로 사용할 수 있습니다.   

하지만 연결 리스트를 사용한다는 것은 추가적인 공간이 필요하다는 의미입니다.   
연속된 데이터가 아니기 때문에 캐시의 도움을 받기 어렵습니다.   

특히, 연결 리스트는 검색 시 O(n)만큼의 시간이 소요됩니다.   
어떤 해시 값을 가진 데이터가 많아진다면 해시의 원래 목적을 달성하기 어렵습니다.   
정리하자면, 연결 리스트가 장점이자 단점 입니다.   

### 📭 개방 주소법 (Open Addressing)   
개방 주소법은 충돌이 발생하면 다른 해시 코드(버킷)를 사용하는 방법입니다.   
고정된 크기의 배열을 사용합니다.   
![img (2)](https://github.com/99MinSu/CS-Study/assets/89891084/a31c81bf-3fd5-4dd0-8a22-e1b33f92eea9)   
새로운 공간을 할당하는 대표적인 방법들입니다.이 외에도 다양한 방법들이 존재합니다  
1. 선형 탐색(Linear Probing) : 충돌 시 다음 버킷, 혹은 몇 개를 건너뛰어 데이터를 삽입한다.
2. 제곱 탐색(Quadratic Probing) : 충돌 시 제곱만큼 건너뛴 버킷에 데이터를 삽입(1,4,9,16..)
3. 이중 해시(Double Hashing) : 충돌 시 다른 해시함수를 한 번 더 적용한 결과를 이용함.

### 😋 장단점
개방 주소법은 고정된 크기의 배열을 사용하기 때문에 추가적인 공간을 필요로 하지 않습니다.   
데이터가 적을 때는 분리 연결법보다 좋은 성능을 보입니다.   
연속된 공간을 사용하기 때문에 CPU가 빠르게 찾을 수 있기 때문입니다. (좋은 캐시 성능)   

하지만 데이터가 많아지면 캐시에서 찾는 값을 꺼내올 확률이 줄어들어 좋은 캐시의 성능을 기대할 수 없습니다.    
충돌이 발생했을 때 다음 빈 공간을 찾기 어려워지고, 값이 자주 추가되고 삭제된다면 성능이 떨어집니다.   
그리고 해시 값 그대로 가지지 않을 확률이 높습니다.

정리하자면, 적은 데이터에서는 성능이 좋지만 많아지면 성능이 떨어집니다.   

## 📦 다양한 Hash Collection
자바는 다양한 해시 기반의 자료 구조를 제공하고 있습니다.   
대표적인 친구들을 알아보고 비교해 보겠습니다.   

### 🗺️ HashMap
Key의 중복을 피하기 위해서 해시를 사용하는 Map 자료 구조입니다.   
자바의 HashMap은 해시 충돌을 분리 연결법으로 대응합니다.   

앞서 분리 연결법은 “연결 리스트를 사용하기 때문에 본래 목적을 잃을 수 있다” 라고 설명했습니다.   
자바에서 어떻게 이 문제를 해결하는지 살펴보겠습니다.   

### 👻 보조 해시 함수
어떤 해시 값이 너무 자주 등장한다면 특정 연결 리스트에 값이 너무 많아질 수 있습니다.   
보조 해시 함수는 해시 값이 더 균등하게 나올 수 있게 도와주는 함수 입니다.   

HashMap 내부에 구현되어 있는 보조 해시 함수입니다.   
```java
static final int hash(Object key) {
    int h;
    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
}
```
여기서 유심히 봐야 할 것은 자바에서 해시 값은 int 라는 점입니다.   
int는 4byte 크기를 표현할 수 있습니다. 그리고 이전에 해시 값은 목차를 의미한다고 했습니다.   
따라서, 자바는 목차가 대략 4byte(2 ^ 32) 개만큼 존재할 수 있다는 뜻입니다. (실제는 2 ^ 30 😎)   

### 🌳 Tree 자료 구조
연결 리스트(Linked List)라는 자료 구조는 검색 시 O(n)의 시간을 소요합니다.   
이 문제를 해결하기 위해서 자바는 Tree라는 자료 구조를 활용합니다.   
![img (1)](https://github.com/99MinSu/CS-Study/assets/89891084/909a98e4-0d59-4278-bdff-2adf75e4ef61)   

특히, Red-Black Tree라는 검색에 최적화된 트리 구조를 사용합니다.   
그 결과 O(n)만큼 걸리던 시간을 O(logn) 로 줄였습니다.   

다만, 항상 트리 구조가 좋은 것은 아니기 때문에 연결 리스트와 같이 사용 합니다.   
사용 중인 공간(버킷)의 개수에 따라서 둘 중에 선택을 합니다.   
내부를 확인해 보면 다음과 같이 트리 구조로 변경하는 기준이 제공되어 있습니다.     
2만큼 차이가 나는 이유는 빈번하게 구조가 변경되는 것을 막기 위해서입니다.    
```java  
static final int TREEIFY_THRESHOLD = 8;
static final int UNTREEIFY_THRESHOLD = 6;
```
트리 구조에서 크고 작음을 해시 값으로 비교하는데 모든 것을 비교할 수는 없습니다.   
따라서, 내부적으로 적당히 대소 관계를 형성해 줌으로 이 현상을 해결합니다.   
```java   
static int tieBreakOrder(Object a, Object b) {
    int d;
    if (a == null || b == null ||
        (d = a.getClass().getName().
         compareTo(b.getClass().getName())) == 0)
        d = (System.identityHashCode(a) <= System.identityHashCode(b) ?
             -1 : 1); // 임의로 대소 관계를 만들어준다.
    return d;
}
```   
### 👀 동적으로 크기 변경하기
트리 구조가 충돌 이후의 문제를 해결했다면, 크기 변경은 충돌 자체를 해결하는 것 입니다.   
크기를 변경하는 임계값은 다음과 같습니다.   
> Load Factor * 공간의 수 (Capacity)
여기서 Load Factor는 공간이 얼마나 차있는지를 나타내는 비율입니다.   
기본적으로 자바는 Load Factor는 0.75를, 기본 크기(Capacity)는 16으로 제공합니다.   
```java
static final int DEFAULT_INITIAL_CAPACITY = 1 << 4; // aka 16
static final float DEFAULT_LOAD_FACTOR = 0.75f;
```     
임계값에 도달한다면 내부적으로 구현된 resize()메서드로 크기를 2배씩 늘립니다.   

### 🔴⚫️ Red-Black Tree
Red-Black Tree는 이진 탐색 트리입니다.   
자바는 최악의 경우에도 좋은 검색 성능을 가지는 특징 때문에 선택했습니다.   
### Red-Black Tree 참고 링크   
https://code-lab1.tistory.com/62#google_vignette

### 🎫 HashTable
HashMap과 거의 유사한 자료 구조입니다. 하지만 몇 가지 차이가 존재합니다.   

Table은 Map과 다르게 동기화를 지원합니다. 하지만 성능이 좋다고는 할 수 없습니다.   
Map에서는 key와 value 모두 null을 사용할 수 있지만 Table에서는 사용할 수 없습니다.   

이런 문제를 해결하기 위해서 자바 1.5 이후부터 ConcurrentHashMap을 지원합니다.   
특히, 내부적으로 크기를 조정할 때 발생하는 Table의 부족한 성능을 해결하였습니다.   

정리하면, HashTable은 Thread-Safe 하지만 성능이 부족하므로,   
ConcurrentHashMap을 을 사용해서 쓰레드 안정성을 챙기면 됩니다.   
### ConcurrentHashMap 참고 링크   
https://m.blog.naver.com/manggo_ya_/223449763877

### 👥 HashSet
HashSet은 내부적으로 HashMap을 사용합니다.   
Map 자료 구조의 key가 중복이 될 수 없다는 점을 이용해 Set이라는 자료 구조의 특징을 살렸습니다.   

key로는 저장할 데이터를, value 값은 내부적으로 생성되어 있는 dummy를 사용합니다.   
```java
private static final Object PRESENT = new Object(); // dummy
```   
정리하자면, HashSet은 HashMap과 거의 동일하다 고 볼 수 있습니다.

## 😋 정리
* 해시는 임의의 크기를 고정된 크기로 바꾸는 알고리즘이다.
* 해시 충돌이란 서로 다른 대상이 같은 해시 값을 가지는 현상이다.
* 자바의 해시 컬렉션은 분리 연결법을 사용한다.
* 해시 테이블과 해시 맵은 거의 유사하다. 해시 테이블을 개선한 게 ConcurrentHashMap이다.
* 해시 셋은 해시 맵과 거의 유사하다. 값에 더미 값을 넣어서 사용한다.

### Reference   
https://codinghejow.tistory.com/408
