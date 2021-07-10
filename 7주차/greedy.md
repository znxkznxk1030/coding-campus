# 알고리즘 7주차 - 탐욕법 ( Greedy )

> https://programmers.co.kr/learn/courses/30/parts/12244

## 탐욕법이란?

- 동적프로그래밍을 이용할 경우에도 불필요한 연산이 존재한다는 것에서 착안된 알고리즘 기법이다.
- 각 단계에 있을 때, 최선의 선택을 하는 것이 결과적으로도 최선의 선택일 경우에 적용되는 기법.
- 하지만, 많은 경우에 각 단계의 최선의 결과의 최선이 아니기 때문에 주의가 필요하다.



## 대표적인 문제 - 회의실 배정문제

https://www.acmicpc.net/problem/1931



### 문제

한 개의 회의실이 있는데 이를 사용하고자 하는 N개의 회의에 대하여 회의실 사용표를 만들려고 한다. 각 회의 I에 대해 시작시간과 끝나는 시간이 주어져 있고, 각 회의가 겹치지 않게 하면서 회의실을 사용할 수 있는 회의의 최대 개수를 찾아보자. 단, 회의는 한번 시작하면 중간에 중단될 수 없으며 한 회의가 끝나는 것과 동시에 다음 회의가 시작될 수 있다. 회의의 시작시간과 끝나는 시간이 같을 수도 있다. 이 경우에는 시작하자마자 끝나는 것으로 생각하면 된다.

### 입력

첫째 줄에 회의의 수 N(1 ≤ N ≤ 100,000)이 주어진다. 둘째 줄부터 N+1 줄까지 각 회의의 정보가 주어지는데 이것은 공백을 사이에 두고 회의의 시작시간과 끝나는 시간이 주어진다. 시작 시간과 끝나는 시간은 231-1보다 작거나 같은 자연수 또는 0이다.

### 출력

첫째 줄에 최대 사용할 수 있는 회의의 최대 개수를 출력한다.



### 예제 입력 1

```
11
1 4
3 5
0 6
5 7
3 8
5 9
6 10
8 11
8 12
2 13
12 14
```

### 예제 출력 1 

```
4
```



##  코드

``` c++
#include <iostream>
#include <cstdio>
#include <cstring>
#include <vector>
#include <queue>
#include <algorithm>
#include <math.h>
#include <string.h>
#include <functional>

#define ll long long int
#define pii pair<long long, long long>
#define si(a)   scanf("%d", &(a))
#define sc(a)   scanf("%c", &(a))
#define sll(a)  scanf("%lld", &(a))
#define ss(a)   scanf("%s", (a))
#define pi(a)   printf("%d", (a))
#define pll(a)  printf("%lld\n", (a))
#define MAX(a,b) (a)>(b)?(a):(b)
#define MIN(a,b) (a)<(b)?(a):(b)
#define FOR(a,b,c) for((a)=(b);(a)<=(c);(a)++)
#define _FOR(a,b,c) for((a)=(b);(a)<(c);(a)++)
#define INF 2e9
#define mod 1000000007

#define ALICE 0
#define COMPUTER 1

using namespace std;

ll N, sum = 0, t = 0;

int main(){
    sll(N);
    vector<pii> meating;
    
    int i;
    FOR(i,1,N)
    {
        ll a,b; sll(a); sll(b);
        meating.push_back(pii(b,a));
    }
    
    sort(meating.begin(), meating.end());
    
    _FOR(i,0,meating.size())
    {
        ll st = meating[i].second, ed = meating[i].first;
        if(st >= t)
        {
            t = ed;
            sum++;
        }
    }
    
    pll(sum);
    
    return 0;
}
```



