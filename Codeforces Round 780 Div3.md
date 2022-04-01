# Codeforces Round 780 Div3 Summary

## Problem A
This is the problem that

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
