# Codeforces Round 780 Div3 Summary

## Problem A
This is the problem is similar to the one in mathmatical induction. But the given is 1 and 2. Then these two must can construct consecutive number. Then we only need to check whether we have a. If we have a then we can directly calculate the answer.

```cpp
#include<cstdio>
#include<cmath>
#include <iomanip>
#define eps 1e-7
using namespace std;
int n;
int main(){
//    freopen("a.in","r",stdin);
    scanf("%d",&n);
    for (int i=0;i<n;++i){
        int a,b;
        scanf("%d%d",&a,&b);
        if (!a) {printf("1\n");continue;}
        printf("%d\n",a+b*2+1);
    }
    return 0;
}
```

## Problem B
Give different kinds of candies, and then give the number of each. Ask whether you can finish all the candies at the end if you want to change the flavor each time.

In fact, we only focus on the two largest ones, because all the others can be rounded up and eliminated with the largest constructs. Only the two largest piles of candies must be one away from each other to output "YES".
```cpp
#include<bits/stdc++.h>
using namespace std;
int T,n,a[220000];
int main(){
//    freopen("b.in","r",stdin);
    scanf("%d",&T);
    while(T--){
        scanf("%d",&n);
        for (int i=0;i<n;++i) scanf("%d",&a[i]);
        sort(a,a+n);
        if (a[n-1]-a[n-2]>1) puts("NO");
        else puts("YES");
    }
    return 0;
}

```
