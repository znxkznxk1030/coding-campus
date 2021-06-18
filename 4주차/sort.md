

# 알고리즘 4주차 - 정렬 ( Sort )

> https://programmers.co.kr/learn/courses/30/parts/12198

## 정렬 ( Sort ) 이란?

- 데이터의 집합을 정해진 순서로 배치하여 자료를 의미있는 구조로 만드는 행위
- 비교의 기준이 되는 Key값의 대소관계로 오름차순 혹은 내림차순으로 정렬한다
- 정렬이 된 자료는 탐색 ( 이진 탐색 ) 에 유리한 구조를 갖게 된다.



## 평균 시간복잡도에 따른 구분

### O(N * N)

- 버블정렬
- 선택정렬
- 삽입정렬

### O(N * logN)

- 머지정렬
- 퀵정렬
- 힙정렬

### O(N + K)

- 버킷정렬



## 안정 정렬 (Stable Sort)

- 중복된 키값을 갖는 데이터들을 순서대로 정렬하는 알고리즘

#### Example

```json
[ 1, 5, 6, 5, 3, 9 ]
```

이같은 배열이 있다고 하자, 이때 key 가 5인 데이터는 2개가 있다.

이 두 데이터를 마킹해보자.

```json
[ 1, 5(1), 6, 5(2), 3, 9 ]
```

이 경우 정렬을 했을때, 두 데이터의 순서가 아래와 같이 변하는 경우가 존재한다면 불안정(Unstable) 정렬이다.


```json
[ 1, 3, 5(2), 5(1), 6, 9 ]
```

하지만 어떠한 경우에도, 같은 키를 같는 데이터들의 순서를 지켜준다면 안정(Stable) 정렬이라고 한다.

```json
[ 1, 3, 5(1), 5(2), 6, 9 ]
```



#### 안정 정렬

- 삽입소트
- 머지소트
- 버블소트



#### 불안정 정렬

- 선택소트
- 힙소트
- 퀵소트



## 제자리 정렬 (In-place Sort)

- 추가적인 메모리 공간이 더 필요하지 않는 정렬

#### 제자리 정렬

- 삽입정렬
- 선택정렬
- 버블정렬
- 힙정렬

#### 제자리 정렬이 아닌 정렬

- 머지소트

#### Controversy

- 퀵소트

>  [퀵 정렬](https://ko.wikipedia.org/wiki/퀵_정렬)은 제자리 알고리즘의 정의에 따라서 제자리 정렬로 분류할 수도 있고 아닐 수도 있다. 퀵 정렬은 재귀적으로 정의되기 때문에 [스택](https://ko.wikipedia.org/wiki/스택)을 사용하게 되는데, 이 스택의 깊이는 {\displaystyle n} ![n](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b)개의 원소에 대해 {\displaystyle \Omega \left(\log n\right)}![\Omega \left(\log n\right)](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c2452cebf9e8615fa9d35632416e9c470fb8051)에 비례하므로 전체 [공간 복잡도](https://ko.wikipedia.org/w/index.php?title=공간_복잡도&action=edit&redlink=1)는 상수가 아니다. 하지만 실용적인 의미에서 퀵 정렬은 상대적으로 작은 메모리만을 더 사용하기 때문에 흔히 제자리 정렬로 기술된다.

[출처 - 위키피디아](https://ko.wikipedia.org/wiki/%EC%A0%95%EB%A0%AC_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98#%EC%A0%9C%EC%9E%90%EB%A6%AC_%EC%A0%95%EB%A0%AC)

## 번외

#### 1. 퀵정렬은 언제나 최고의 정렬일까?

#### 2. 하스켈에서의 퀵정렬

```haskell
quicksort [] = []
quicksort (p:xs) = (quicksort lesser) ++ [p] ++ (quicksort greater)
    where
        lesser = filter (< p) xs
        greater = filter (>= p) xs
```



