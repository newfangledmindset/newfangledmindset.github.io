---
title: "[BOJ 28324] 스케이트 연습"
excerpt: "뒤집어서 생각해보기"
categories:
    - ps
tags:
    - ps
    - 알고리즘
---

![[BOJ 28324]](/assets/images/2024-03-28-2.png)

[문제 링크](https://www.acmicpc.net/problem/28324)

알고리즘 스터디 한 거 리마인드 할 겸 작성해본다.

텍스트가 고봉밥이라 어질어질한데, 사실 이 문제는 **거꾸로**, **뒤집어서** 생각하면 쉽게 풀린다. 근데 그런 생각까지 가는 게 쉽냐고...

이거 말고는 진짜 할 말이 없다.

아래는 나의 솔루션이다.

```cpp
int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    int n, sp, t;
    ll acc = 0;
    cin >> n;
    vector<int> v1;

    for (int i = 0; i < n; i++) {
        cin >> t;
        v1.push_back(t);
    }

    sp = 0;
    for (int i = n - 1; i >= 0; i--) {
        if (v1[i] <= sp) sp = v1[i];
        else sp++;

        acc += sp;
    }

    cout << acc;
}
```