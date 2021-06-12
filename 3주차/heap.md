# 알고리즘 3주차 - 힙
> https://programmers.co.kr/learn/courses/30/parts/12117

## 힙이란?
- 가장 높은 값(혹은 낮은 값)을 지속적으로 빠르게 뺄 수 있도록 자료의 삽입과 삭제가 이뤄질 수 있게 고안해낸 자료구조


- 노드 삽입과 삭제(pop)시 O(nlogn)이 소요. 보통 리스트의 경우 가장 높은 값을 탐색하는데 걸리는 시간은 O(n)


## 힙의 특징
- 완전 이진 트리
- 느슨한 정렬 (최대힙의 경우 부모 노드의 키 > 자식 노드의 키)
- 삭제시 최대 값을 리턴하는지 최소 값을 리턴하는지에 따라 Max Heap, Min Heap으로 구분

## 힙의 구현
1. 배열로 트리 구현하기
2. 삽입 연산
3. 삭제 연산

### 1. 배열로 트리 구현하기
- 최상위 부모 인덱스 : 0
- 왼쪽 자식 인덱스: (부모 인덱스) * 2 + 1
- 오른쪽 자식 인덱스: (부모 인덱스) * 2 + 2


``` java
class MinHeap {
  private ArrayList<Integer> heap;

  public MinHeap() {
    heap = new ArrayList<>();
  }
}
```

![힙구현-1](./Heap.png)

### 2. 삽입 연산

![힙구현-2](./heap-insert.png)

``` java
private void insert(int data) {
  heap.add(data);
  int position = heap.size() - 1;

  while( position > 1 
  && heap.get(position / 2) < heap.get(position)) {
    int temp = heap.get(position / 2);
    heap.set(position / 2, heap.get(position));
    heap.set(position, temp);

    position /= 2;
  }
}

```
