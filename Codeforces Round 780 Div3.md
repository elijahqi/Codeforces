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

## Problem C
We are asked to remove the least number of characters from the string and get a string with an even number of digits, and we need to ensure that the odd and even digits are the same.
set dp[i] = for location i what is the max string that satisfy the requirement.
Final answer is equal to total length - max dp.
```cpp
#include<bits/stdc++.h>
using namespace std;
const int N=220000;
int n,dp[N];
int mp[300],lst[N];
int main(){
//    freopen("c.in","r",stdin);
    ios::sync_with_stdio(false);
    cin>>n;
    while(n--){
        string s;cin >> s;
        int sz=s.size();memset(mp,0,sizeof(mp));
        for (int i=1;i<=sz;++i){
            lst[i]=mp[s[i-1]];
            mp[s[i-1]]=i;
        }
        for (int i=1;i<=sz;++i){
            dp[i]=dp[i-1];
            if (lst[i]){
                dp[i]=max(dp[i],dp[lst[i]-1]+2);
            }
        }
        cout << sz-dp[sz]<<endl;
    }
    return 0;
}
```
## Problem D
We are asked to find the maximum product of the sequence. The sequence we can only pop from the left or right. And the element in this list are ranged from -2 to 2.

Then we can use two pointer method to do this problem.
In my solution ,we set the pointer l . Loop it from 0 to n-1. If a[l]==0 we must skip this. Since we know that if one of the element is 0. Then the whole product will be zero. Then we use r from l to try to extend to the most right non-zero one. And we use this non-zero segment to extend from left or from right to calculate the max product. Then we will get the answer.

```cpp
#include<bits/stdc++.h>
using namespace std;
const int N=220000;
int n,a[N],pre[N],two[N],T;
int l,r,mx,retl,retr;
int main(){
//    freopen("d.in","r",stdin);
    ios::sync_with_stdio(false);
    cin >> T;
    while(T--){
        cin >> n;
        for (int i=0;i<n;++i) cin >> a[i];
        int best=0,x=n,y=0,l=0;
        while(l<n){
            while(l<n&&(!a[l])) ++l;
            if (l==n) break;
            int r=l;bool neg=0;int two=0;
            while(r<n&&a[r]) ++r;
            for (int j=l;j<r;++j){
                if(a[j]<0) neg=!neg;
                if (abs(a[j])==2) ++two;
                if (!neg&&two>best){
                    best=two;x=l;y=n-j-1;
                }
            }
            neg=0;two=0;
            for (int j=r-1;j>=l;--j){
                if (a[j]<0) neg=!neg;
                if (abs(a[j])==2) ++two;
                if (!neg && two>best){
                    best=two;x=j;y=n-r;
                }
            }
            l=r+1;
        }
        cout << x << " " << y <<endl;
    }
    return 0;
}
```
