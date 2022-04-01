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
