---
title: tmp
tags: aaaa
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---

A Post with Header Image, See [Page layout](https://tianqi.name/jekyll-TeXt-theme/samples.html#page-layout) for more examples.

<!--more-->

## Problem

[Link](https://www.luogu.com.cn/problem/P2680)

题意：

给定一棵带边权的树，以及若干条树上的路径。我们可以使一条树边的边权变为 $0$ ，求变化后最长路径的最小值。

## Solution

将题目简化过后，从 “求最长路径的最小值” 可以大概猜到这道题需要用到二分。这道题中的完成时间很明显具有单调性：

*  若 $t$ 恰好满足题意，则 ${\forall} t_0 < t$ 都不满足，${\forall}t_1 > t$ 都满足。$\\$

所以这道题需要来二分答案。

接下来就要思考：对于一个完成时间 $t$ （最长路径的最小值），我们该如何判断是否可行呢？

我们可以先用 $\operatorname{LCA}$ 预处理出每条路径的长度。

对于长度小于 $t$ 的路径是一定满足的，所以我们只需要考虑长度大于 $t$ 的路径。

这时候贪心一下：使什么样的边边权为 $0$ 可以使所有长度大于 $t$ 的路径都最大程度的变小。

因为每条都需要变小，所以一定要选它们公共的边，而又要最大程度变小，所以一定要选这其中边权最大的边。

若有 $k$ 条路径的长度都大于 $t$ ，则我们想要选择改变的公共边一定被路径覆盖了 $k$ 次（毕竟是公共的）。对于维护覆盖次数，我们可以采用树上差分。

最后，如果所有长度大于 $t$ 的路径减去找到的路径长度（没找到的话显然不行）都小于了 $t$ 那就说明当前二分的 $t$ 是可行的的。

细节详见代码。。。

## Code
```cpp
#include <cstdio>
#include <vector>
#include <cstring>
#include <algorithm>

using namespace std;

const int Maxn = 3e5; 

int n, m, maxdis;
int vis[Maxn + 5], fa[Maxn + 5], dep[Maxn + 5], flag[Maxn + 5], f[Maxn + 5], cnt[Maxn + 5];

struct Node {
	int v, w;
} ; 

struct Plan {
	int u, v, dis, lca;
	friend bool operator < (Plan x, Plan y) {
		return x.dis < y.dis;
	}
} s[Maxn + 5];

vector < Node > ask[Maxn + 5];
vector < Node > edge[Maxn + 5];

int Max (int a, int b) {
	return a > b ? a : b;
}

void Make_Set () {
	for (int i = 1; i <= n; i ++) fa[i] = i;
}

int Find_Set (int u) {
	return u == fa[u] ? u : fa[u] = Find_Set (fa[u]);
}

void Tarjan (int u) {
	vis[u] = 1;
	for (auto x : edge[u]) {
		if (vis[x.v]) continue;
		f[x.v] = u;
		dep[x.v] = dep[u] + x.w;
		Tarjan (x.v);
		fa[x.v] = u;
	}
	for (auto x : ask[u]) {
		if (vis[x.v]) s[x.w].lca = Find_Set (x.v);
	}
}

void Dfs (int u, int tar, int dis) {
	cnt[u] = flag[u];
	for (auto x : edge[u]) {
		if (x.v == f[u]) continue;
		Dfs (x.v, tar, x.w);
		cnt[u] += cnt[x.v]; //将子树标记向上传 
	}
	if (cnt[u] == tar) {
		maxdis = Max (maxdis, dis); //cnt[u]==tar表示 u->fa[u]这条边被覆盖了 tar 次 
	}
}

bool Check (int mid) {
	int ct = 0;
	memset (cnt, 0, sizeof cnt);
	memset (flag, 0, sizeof flag);
	for (int i = 1; i <= m; i ++) {
		if (s[i].dis <= mid) {
			break;
		}
		ct ++;
		flag[s[i].u] ++;
		flag[s[i].v] ++;
		flag[s[i].lca] -= 2; //树上差分 
	}
	
	if (!ct) return true; 
	
	maxdis = 0;
	Dfs (s[1].lca, ct, 0); //找最大公共边，直接从最长路径的 LCA为根找公共边即可
	
	return s[1].dis - maxdis <= mid; //最长路径满足则所有都满足 
}

int main () {
	scanf ("%d %d", &n, &m);
	
	for (int i = 1; i < n; i ++) {
		int u, v, w;
		scanf ("%d %d %d", &u, &v, &w);
		edge[u].push_back ({v, w});
		edge[v].push_back ({u, w});
	}
	
	for (int i = 1; i <= m; i ++) {
		scanf ("%d %d", &s[i].u, &s[i].v);
		ask[s[i].u].push_back ({s[i].v, i});
		ask[s[i].v].push_back ({s[i].u, i});
	}
	
	Make_Set ();
	Tarjan (1); //Tarjan离线求LCA 
	
	for (int i = 1; i <= m; i ++) {
		s[i].dis = dep[s[i].u] + dep[s[i].v] - dep[s[i].lca] * 2; //LCA求路径长 
	}
	
	sort (s + 1, s + 1 + n);
	reverse (s + 1, s + 1 + n); //先从大到小排序 
	
	int l = 0, r = s[1].dis; 
	while (l < r) {
		int mid = l + r >> 1;
		if (Check (mid)) r = mid;
		else l = mid + 1;
	}
	
	printf ("%d", l);
	return 0;
}
```
