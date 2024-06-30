# 배열(array)

## 배열(array)이란?
![img](https://github.com/99MinSu/CS-Study/assets/89891488/244c79b0-2a85-4470-a4f6-cd79967c4503)

배열은 **같은 타입의 여러 변수들로 이루어 진 하나의 묶음**으로 다루는 선형 자료구조이다.

- 선형 자료 구조? **하나의 자료 뒤에 하나의 자료가 존재하는 형태의 자료 구조**

---

### 배열의 구조

- 인덱스(index) : 저장 공간에 연속적으로 번호를 부여, 배열에서의 위치를 의미하는 숫자.
    - 인덱스의 범위는 0부터 ‘배열의 길이 – 1’까지
    - 첫 요소의 인덱스가 0인 이유는 인덱스는 첫 번째 요소를 기준으로 **얼마만큼 떨어져 있는지 상대적인 값으로 표현**하기 때문이다
- 요소(element) : 배열을 구성하는 각각의 값을 의미

![1차원 배열](https://github.com/99MinSu/CS-Study/assets/89891488/266bece2-47b2-49ab-a6b3-0bbe431a1620)


배열은 각 저장 공간이 연속적으로 붙어있기 때문에 저장 공간에 일일히 이름을 부여할 필요 없이 **참조 변수의 이름과 인덱스 번호를 이용하여 배열의 저장 공간을 다룬다.**

- 첫번쨰 요소의 메모리 주소 값이 0x10이라면 두번쨰 요소의 메모리 주소는 0x14가 된다.(int 가 4byte이기 때문)
- 첫 번째 원소의 주소 + (자료형 크기)*i 한 주소에 접근한다.

---

# 다차원 배열이란?

배열에 배열 중첩 선언하여 메모리 구조가 2차원 이상의 형태를 보이는 배열을 다차원 배열이라고 한다.

- 2차원 배열은 요소로 1차원 배열을 가지는 배열, 3차원 배열은 요소로 2차원 배열을, 4차원 배열은 요소로 4차원 배열을 가지는 것 처럼 **기존 차원을 요소로 가지는 배열을 의미한다.**
- 1차원 배열이 논리적으로 직선 모양 이라면 2차원 배열은 사각형,  3차원 배열은 육면체와 같은 모양이다.

![논리적](https://github.com/99MinSu/CS-Study/assets/89891488/2016f360-b33c-4e6d-9672-ecec00b78c5c)

- 일반적으로 2차원을 초과하는 구조의 배열을 잘 이용하지 않는다.

## 2차원 배열의 구조

배열의 요소로 또 다른 1차원 배열을 가지는 배열을 의미한다.  

![2차원](https://github.com/99MinSu/CS-Study/assets/89891488/b8d6a172-b73b-4f1a-8f63-44b3ddfa4184)

위의 그림은 **길이가 3인 1차원 배열을 가지는 배열**을 의미 하며,  **2행 3열의 논리적인 구조**를 생각할 수 있다. 따라서 한 요소를 식별하려면 두 개의 인덱스가 필요하다.

- 2차원 배열은 1차원 배열과 달리 두 개의 인덱스(행과 열)을 가지는 테이블 형태라고 생각하면 된다.

하지만 컴퓨터의 메모리는 위와 같은 입체적 공간이 아닌 선형 공간이므로 논리적 구조와 달리 **1차원 배열과 마찬가지로  실제로는 다음 그림과 같이 저장된다.**

![2차원 배열](https://github.com/99MinSu/CS-Study/assets/89891488/67eea419-663b-4bec-b700-7f541ca48136)

---

## 배열의 특징

- **같은 타입**의 데이터를 나열한 **선형 자료구조**
- **연속적인 메모리 공간에 순차적**으로 데이터를 **저장한다.**
- 배열을 선언한 후에는 배열의 **크기는 고정된다.**

## 배열의 연산 및 시간 복잡도

| 연산 | 시간 복잡도 | 설명 |
| --- | --- | --- |
| 접근 | O(1) | 배열은 인덱스를 사용하여 요소에 직접 접근할 수 있습니다. |
| 탐색 | O(n) | 순차 접근 방식을 사용하기 때문에최악의 경우 배열의 모든 요소를 검사해야 한다. |
| 삽입 | O(n) | 배열의 첫 번째 위치에 삽입하려면 모든 요소를 이동해야 한다. |
| 삭제 | O(n) | 배열의 첫 번째 요소를 삭제하면 모든 요소를 이동해야 한다. |

| 마지막에 값 |  | i번째에 값 |  | 처음에 값 |
| --- | --- | --- | --- | --- |
| 삽입 | 삭제 | 삽입 | 삭제 | 삽입 |
| O(n) | O(1) | O(n) | O(n) | O(n) |
- **삽입(Insertion)**:

![삽입 예시](https://github.com/99MinSu/CS-Study/assets/89891488/876005b9-85e4-4355-85a8-63125130cadc)

마지막에 값 삽입, 현재보다 길이가 1 더 긴 배열을 선언하고 원래의 배열을 복사하고 마지막에 새로운 값을 삽입 하면 된다. 배열의 모든 원소를 복사해야 하므로 시간복잡도는 O(n)

![마지막값 삽입](https://github.com/99MinSu/CS-Study/assets/89891488/f2597692-d6b8-4d73-ae4c-d3ba6f7fadb6)

- **삭제(Deletion)**:

마지막에 값 삭제, 값을 없애고 자리를 비워두면 되므로  시간복잡도는 O(1)

![마지막 값 삭제](https://github.com/99MinSu/CS-Study/assets/89891488/23439f50-9f0a-4e8a-8560-d92f64484319)

## 배열의 장점

- 인덱스를 통해 모든 데이터에 직접 액세스하기 때문에 **액세스 속도가 빠르다.**
    - 리스트나 그래프와 같은 자료구조 형태와 달리 탐색없이 인덱스를 통해 직접 액세스 하기 때문에 액세스 속도가 빠르다.
    - 리스트의 경우 10,000번째 값을 액세스 하기 위해서는 첫번째 값부터 10,000번 탐색해야 하지만 배열의 경우 해당 인덱스 위치의 주소값을 얻는 단 한번의 연산만으로 액세스가 가능하다. 자료구조의 크기가 크면 클수록 이 차이는 더욱 커진다.
- 포인터 등 부가적인 정보가 없어 **기록 밀도가 1이다.**
    - 리스트, 그래프 등은 데이터 외에 포인터 등 부가정보를 가지기 때문에 기록밀도가 1이 되지 않지만, 배열은 부가정보 없이 데이터만 저장하기 때문에 기록밀도가 1이다.
    - 리스트나 그래프는 메모리에 분산시켜 데이터를 저장하고 포인터로 연결시킨 형태라 데이터외 부가 정보를 가지게 된다. 반대로 배열은 메모리의 연속된 공간에 데이터를 저장하고 인덱스를 이용한 연산을 통해 액세스 하기 때문에 부가정보가 필요 없다.
- 가장 간단하며 사용하기 쉽다

## 배열의 단점

- **삽입과 삭제가 어렵고 오래 걸린다.**
    - 원소를 삽입하거나 삭제할 경우, 해당 원소 이후의 모든 원소들을 한칸씩 밀거나 당겨야 한다. (연속된 메모리 공간에 저장되기 때문)
- 배열의 **크기를 바꿀 수 없다**.
    - 배열은 처음 생성할 때 크기를 설정함.
    - 크기를 변경하기 위해서는 원하는 크기의 새로운 배열을 선언한 뒤 값을 복사해야 함.
- 연속된 메모리라서 **공간 낭비**가 발생
    - 중간에 데이터가 삭제되면 공간 낭비가 발생할 수 있음. 또, 처음에 배열 크기를 100으로 생성했는데 10정도 밖에 쓰지 않으면 나머지 공간은 빈 공간으로 낭비가 발생함.
 

## Arrays 클래스
Arrays 클래스에는 배열을 다루기 위한 다양한 메소드가 포함되어 있다.
| 메소드 | 설명 |
| --- | --- |
| static <T> List<T> asList(T... a) | 전달받은 배열을 고정 크기의 리스트(list)로 변환하여 반환함. |
| static int binarySearch(Object[] a, Object key) | 전달받은 배열에서 특정 객체를 이진 검색 알고리즘을 사용하여 검색한 후, 그 위치를 반환함. |
| static <T> T[] copyOf(T[] original, int newLength) | 전달받은 배열을 특정 길이의 새로운 배열로 복사하여 반환함. |
| static <T> T[] copyOfRange(T[] original, int from, int to) | 전달받은 배열의 특정 범위에 해당하는 요소만을 새로운 배열로 복사하여 반환함. |
| static boolean equals(Object[] a, Object[] a2) | 전달받은 두 배열이 같은지를 확인함. |
| static void fill(Object[] a, Object val) | 전달받은 배열의 모든 요소를 특정 값으로 초기화함. |
| static void sort(Object[] a) | 전달받은 배열의 모든 요소를 오름차순으로 정렬함. |

### 2차원 배열의 비교
2차원 배열을 비교하기 위해 자바는 Arrays.deepEquals() 메소드를 제공한다.
```
int[][] arr = 	{
				{1, 2},
				{3, 4, 5}
				};
int[][] arr1 = 	{
				{1, 2},
				{3, 4, 6}
				};

System.out.println(Arrays.deepEquals(arr, arr1)); //다르기 때문에 false가 출력된다.
```

### 2차원 배열의 출력
2차원 배열의 실제 값을 출력하려면 1차원 배열과 마찬가지로 for문을 이용해 각 요소들을 하나씩 출력해 주거나 Arrays.deeptoString()메서드를 사용하여 배열을 문자열 형식으로 만들어 출력해야 한다.
```
int[][] arr = { 
				{1, 2, 3},
				{4, 5, 6, 8}
				};
                
for(int i = 0; i < arr.length; i++) { 행의 요소들 전체
	for(int j = 0; j < arr[i].length; j++) {각 행의 요소(열)을 하나씩 출력
		System.out.print(arr[i][j]);
	}
	System.out.println();
}
//123
//4568


// Arrays.deepToString() 메서드를 사용하여 문자열 형식으로 출력
// [[1, 2, 3], [4, 5, 6, 8]]
System.out.println(Arrays.toString(arr));
```
### Reference
https://cheris8.github.io/python/DS-Array/
[Array](https://www.notion.so/Array-29794fcc77784f43b90ac677167b5260?pvs=21) 
https://www.tcpschool.com/c/c_array_twoDimensional
https://jjoonleo.tistory.com/8