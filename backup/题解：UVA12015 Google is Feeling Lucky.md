## UVA 12015

### 题目大意

多组数据，每组数据给出 $10$ 个网址以及它们各自的相关度，输出相关度最高的网址。若有多个满足要求，请按照原顺序依次输出，一行一个。

### 解题思路

可以使用 `std::vector` 把输入的网址按照相关度存起来，同时又保持原有顺序。

设置一个变量 $maxx$，记录最大相关度，可以免去排序的过程。

注意多测清空。

### 代码


```cpp
// Problem: Google is Feeling Lucky
// Contest: Luogu
// URL: https://www.luogu.com.cn/problem/UVA12015
// Create Time: 2024-09-18 20:27:39

#include<iostream>
#include<cstring>
#include<cstdio>
#include<stack>
#include<queue>
#include<algorithm>
#include<cmath>
#include<vector>
//#include<unordered_map>
//#define map unordered_map
using namespace std;
/*================*/

inline int read() {
	char c=getchar();int x=0,f=1;
	for(;!isdigit(c);c=getchar())if(c=='-')f=-1;
	for(;isdigit(c);c=getchar())x=x*10+c-48;
	return x*f;
}

#define r(a) (a)=read()

int n,rev,maxx,C; //rev 表示每个网址的相关度
string s;
vector<string> v[105];

signed main() {
	cin>>n;
	while (n--) {
		//初始化
		maxx=-1;
		for (int i=0;i<=100;i++) v[i].clear();
		for (int i=1;i<=10;i++) {
			cin>>s>>rev;
			maxx=max(maxx,rev);
			v[rev].push_back(s);
		}
		printf("Case #%d:\n",++C);
		for (auto c:v[maxx]) cout<<c<<"\n";
	}
	return 0;
}
```