# 알고리즘 5주차 - 완전탐색 ( Brute Force )

> https://programmers.co.kr/learn/courses/30/parts/12230

## 완전 탐색 ( Brute Force ) 란?
- 모든 경우의 수를 다 계산해보는 방법론
- 모든 문제는 먼저 완전 탐색으로 풀이 가능해야한다.
- 기본적으로 DFS 혹은 BFS가 사용된다.


## 소수 구하기 ( 에라토스테네스의 체 )
- 문제 풀이중 계속해서 소수판별이 필요할 경우 미리 일정 범위내의 소수를 다 구하는 알고리즘.
- 체에 거르듯, 소수의 배수를 소거하는 방법

``` java 

private int limit = 10000001;
private boolean isPrimeNumber[] = new boolean[limit];

private void findAllPrimeNumber() {
        Arrays.fill(isPrimeNumber, true);
        isPrimeNumber[0] = false;
        isPrimeNumber[1] = false;
        for (int i = 2; i < limit; i++) {
            if(isPrimeNumber[i]) {
                for (int j = i + i; j < limit; j += i) {
                    isPrimeNumber[j] = false;
                }
            }
        }
    }
```

( 추가 - 구하고자 하는 범위의 루트 개만 돌아도 된다. )


## 순환 ( Permutation )
- 배열내 모든 순서 쌍을 찾는 문제

``` java 
 private void permutate(String str, String ans) {
        for (int i = 0; i < str.length(); i++) {
            char ch = str.charAt(i);
            String ros = str.substring(0, i) + str.substring(i + 1);

            System.out.println(ans+ch);

            permutate(ros, ans+ch);
        }
    }
```


