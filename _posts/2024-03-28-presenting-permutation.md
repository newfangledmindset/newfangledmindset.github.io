---
title: "[BOJ 30021] 순열 선물하기"
excerpt: "순열을 선물하자"
categories:
    - ps
tags:
    - ps
    - 알고리즘
---

![[BOJ 30021]](/assets/images/2024-03-28-1.png)

[문제 링크](https://www.acmicpc.net/problem/30021)

알고리즘 스터디 한 거 리마인드 할 겸 작성해본다.

1. $$1+2+ \cdots + N = \frac{N(N + 1)}{2}$$ 이므로 총합이 소수가 되는 경우는 $N = 2$일때 밖에 없다.

2. 짝수는 절대 소수가 될 수 없다. 당연히 짝수의 합도 소수가 될 수 없다.

3. 홀수의 합은 $$n^2$$ 이므로 $$1 \cdots N$$까지 홀수만 선물하면 소수가 되는 경우가 없다.

이제 위 3개의 사실을 조합해 문제를 해결해 보자.

- 먼저 $$1 \cdots N$$ 내의 모든 홀수를 더한다. 홀수의 총합이 홀수라면 마지막으로 더했던 홀수를 빼서 잠시 다른 변수에 저장한다.
- 그리고 모든 짝수를 더한다. 여기까지 날짜별 합은 $$n^2$$, 또는 짝수이기 때문에 문제의 조건을 만족한다.
- 마지막으로 다른 변수에 저장해놨던 홀수 하나를 더한다. 1.에 의해 $$N = 2$$가 아니라면 총합은 소수가 될 수 없다!

아래는 나의 솔루션이다.

```cpp
int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    bool is_delayed = false;
    int n, acc = 0, d = 0;
    cin >> n;
    
    if (n == 2) {
        cout << "NO";
        return 0;
    }

    cout << "YES" << '\n';

    for (int i = 1; i <= n; i += 2) {
        if (i < n - 1) cout << i << ' ';
        is_delayed = !is_delayed;
        acc += i;
        d = i;
    }

    if (!is_delayed) cout << d << ' ';

    for (int i = 2; i <= n; i += 2) cout << i << ' ';

    if (is_delayed) cout << d << ' ';
}
```