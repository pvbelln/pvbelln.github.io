## UVA11614

### 思路

由初中（小学？）等差数列知识，可得数列 $\{ 1,2,3,\dots,n\}$ 的前 $n$ 项和为

$$\sum _{i=1} ^n a_i = \dfrac{n(n+1)}{2}$$

也就是说，我们知道了士兵数 $k$，也就是知道了该数列的某个前缀和。当然，这里说前缀和不太准确，因为最后一项可以是“不完整”的，即可以是 $1+2+3+4+5+3$。

我们可以设一共要站 $x$ 行，接下来要做的就是求解方程

$$\dfrac{x(x+1)}{2}=k$$

化简得

$$x^2+x-2k=0$$

由求根公式，得

$$x=\dfrac{-1+\sqrt{1+8k}}{2}$$

负的根舍掉了。

如果 $x$ 不为整数，则向下取整即可。

### 代码

```cpp
// Problem: Etruscan Warriors Never Play Chess
// Contest: Luogu
// URL: https://www.luogu.com.cn/problem/UVA11614
// Create Time: 2024-10-29 22:39:38

#include<iostream>
#include<cstring>
#include<cstdio>
#include<stack>
#include<queue>
#include<algorithm>
#include<cmath>
#include<vector>
//#include<unordered_map>
#define int long long
using namespace std;
/*================*/

inline int read() {
	char c=getchar();int x=0,f=1;
	for(;!isdigit(c);c=getchar())if(c=='-')f=-1;
	for(;isdigit(c);c=getchar())x=x*10+c-48;
	return x*f;
}

#define r(a) (a)=read()

int T,k;

signed main() {
	r(T);
	while (T--) {
		r(k);
		printf("%.0f\n",floor((-1.0+sqrt(1+8*k))/2.0));  //核心只有一行
	}
	return 0;
}
```