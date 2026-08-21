---
layout:  post
category:  algorithm
title:  No66、机器人的运动范围
tagline:  by 阿秀
tags:
    - 原创
    - 剑指offer
    - 数据结构与算法
    - 算法
    - 社招
    - 校招
    - 阿秀
excerpt: No66、机器人的运动范围
comment: false
---

<h1 align="center">带你快速刷完67道剑指offer</h1>

<div style="border-color: #24C6DC;
            background-color: #e9f9f3;         
            margin: 1rem 0;
        padding: .25rem 1rem;
        border-left-width: .3rem;
        border-left-style: solid;
        border-radius: .5rem;
        color: inherit;">
  <p>这是六则或许对你有些许帮助的信息:</p>
<p>⭐️1、阿秀与朋友合作开发了一个<span style="font-weight:bold;color:red">编程资源网站</span>，目前已经收录了很多不错的学习资源和黑科技（附带下载地址），如过你想要寻求合适的编程资源，<a href="https://tools.interviewguide.cn/home" style="text-decoration: underline" target="_blank">欢迎体验</a>以及推荐自己认为不错的资源，众人拾柴火焰高，我为人人，人人为我🔥！</p>  <p>2、👉23年5月份阿秀从<a style="text-decoration: underline" href="https://mp.weixin.qq.com/s?__biz=Mzk0ODU4MzEzMw==&mid=2247512170&idx=1&sn=c4a04a383d2dfdece676b75f17224e78" target="_blank">字节跳动离职跳槽到某外企</a>期间，为<span style="font-weight:bold">方便自己找工作，增加上岸几率</span>，跟朋友一起从0开发了一个<span style="font-weight:bold;color:red">互联网中大厂面试真题解析网站</span>，包括两个前端和一个后端。能够定向查看互联网公司的笔试真题，比如我想查一下字节跳动近一年的笔试真题有哪些？都是可以做到的。欢迎体验~
<div align="center">
</div>网站地址：<a style="text-decoration: underline" href="https://niumacode.com/home?ref=F6O2625K" target="_blank">大厂面试算法真题网站</a>。
    </p>3、😊
    分享一个阿秀自己私藏的<span style="font-weight:bold;color:red">黑科技网站</span>，<a style="text-decoration: underline" href="https://hkjtz.cn/" target="_blank">点此直达</a>，主要是各类小众实用APP、网站等，除此外也包括高清影视、音乐、电视剧、AI、纪录片、英语四六级考试、考研考公、副业等资源。
  </p>
  <p>4、😍免费分享阿秀个人学习计算机以来收集到的免费学习资源，<a style="text-decoration: underline" href="/notes/07-resources/01-free/01-introduce.html" target="_blank">点此白嫖</a>；也记录一下自己以前买过的<a style="text-decoration: underline" href="/notes/07-resources/02-precious.html" target="_blank">不错的计算机书籍、网络专栏和垃圾付费专栏</a>；也记录一下自己以前买过的<a style="text-decoration: underline" href="/notes/07-resources/02-precious.html" target="_blank">不错的计算机书籍、网络专栏和垃圾付费专栏</a>
  </p>
  <p>5、🚀如果你想在校招中顺利拿到更好的offer，阿秀建议你多看看前人<a style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/npg1k81zeq4wfpyz" target="_blank">踩过的坑</a>和<a style="text-decoration: underline"  target="_blank" href="https://www.yuque.com/tuobaaxiu/httmmc/gge9ppd0mbu2d3dp">留下的经验</a>，事实上你现在遇到的大多数问题你的学长学姐师兄师姐基本都已经遇到过了。
  </p>
  <p>6、🔥 欢迎准备计算机校招的小伙伴加入我的<a  style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/xg0otqvc17wfx4u9" target="_blank">学习圈子</a>，一个人踽踽独行不如一群人报团取暖，圈子里沉淀了很多过去21/22/23/24/25届学长学姐的<a  style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/gge9ppd0mbu2d3dp" target="_blank">经验和总结</a>，好好跟着走下去的，最后基本都可以拿到不错的offer！</a>如果你需要《阿秀的学习笔记》网站中📚︎校招八股文相关知识点的PDF版本的话，可以<a style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/qs0yn66apvkzw0ps" target="_blank">点此下载</a> 。</p>   </div>

## **No66、机器人的运动范围**

<font style="font-weight:normal; color:#4169E1;text-decoration:underline;" target="_blank">[牛客网原题链接](https://www.nowcoder.com/practice/6e5207314b5241fb83f2329e89fdecc8?tpId=13&&tqId=11219&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)</font>

### **题目描述**

地上有一个m行和n列的方格。一个机器人从坐标0,0的格子开始移动，
每一次只能向左，右，上，下四个方向移动一格，但是不能进入行坐标和列坐标的数位之和大于k的格子。 
例如，当k为18时，机器人能够进入方格（35,37），因为3+5+3+7 = 18。
但是，它不能进入方格（35,38），因为3+5+3+8 = 19。请问该机器人能够达到多少个格子？

### **示例1**

**输入**

~~~
5,10,10
~~~
**返回值**

~~~
21
~~~



### **1、借助标记法，看的解释，其实很好理解和明白**

~~~cpp
bool canReach(int threshold, int x, int y) {
	int sum = 0;
	while (x > 0) {
		sum += x % 10;
		x /= 10;
	}
	while (y > 0) {
		sum += y % 10;
		y /= 10;
	}
	return sum <= threshold;
}

int movingCountCore(int threshold, int i, int rows,int j ,int cols, vector<vector<bool>>&visit) {
	if (i < 0 || i >= rows || j < 0 || j >= cols || !canReach(threshold, i, j) || visit[i][j] == true) return 0;
	//边界值不满足，不能到达或者已经走过了，也到达不了，返回0
	visit[i][j] = true; // 当前已经走过了，并且满足要求，所有后续return 要加上1

	return movingCountCore(threshold, i - 1, rows, j, cols, visit) + //分别是上下左右各个方向判断一下
		movingCountCore(threshold, i + 1, rows, j, cols, visit) +
		movingCountCore(threshold, i , rows, j-1, cols, visit) +
		movingCountCore(threshold, i, rows, j+1, cols, visit) + 1;

}
int movingCount(int threshold, int rows, int cols)
{
	vector<vector<bool>> visit(rows,vector<bool>(cols,false));
	return movingCountCore(threshold, 0,  rows, 0, cols, visit);
	
}
~~~



### **2、标注借助法的简化版**

递归只要俩行就够了，helper(threshold, rows, cols, flags, i + 1, j) +  helper(threshold, rows, cols, flags, i, j + 1) + 1，不需要往回走，然后前面的判断i，j也不会小于零了  

因为是从（0 0 ），开始走的，所以只需要判断向上和向右的情况即可

~~~cpp
bool canReach(int threshold, int x, int y) {
	int sum = 0;
	while (x > 0) {
		sum += x % 10;
		x /= 10;
	}
	while (y > 0) {
		sum += y % 10;
		y /= 10;
	}
	return sum <= threshold;
}

int movingCountCore(int threshold, int i, int rows,int j ,int cols, vector<vector<bool>>&visit) {
	if (i >= rows || j >= cols || !canReach(threshold, i, j) || visit[i][j] == true) return 0;
	//边界值不满足，不能到达或者已经走过了，也到达不了，返回0
	visit[i][j] = true; // 当前已经走过了，并且满足要求，所有后续return 要加上1

	return  movingCountCore(threshold, i + 1, rows, j, cols, visit) +
		movingCountCore(threshold, i, rows, j+1, cols, visit) + 1;

}
int movingCount(int threshold, int rows, int cols)
{
	vector<vector<bool>> visit(rows,vector<bool>(cols,false));
	return movingCountCore(threshold, 0,  rows, 0, cols, visit);
	
}
~~~



### **3、BFS**

~~~cpp
bool canReach(int threshold, int x, int y) {
	int sum = 0;
	while (x > 0) {
		sum += x % 10;
		x /= 10;
	}
	while (y > 0) {
		sum += y % 10;
		y /= 10;
	}
	return sum <= threshold;
}

int movingCount(int threshold, int rows, int cols)
{
	vector<vector<bool>> grid(rows,vector<bool>(cols,false));
	queue<pair<int, int>> que;
	if (canReach(threshold, 0, 0)) {
		que.push(make_pair(0, 0));
		grid[0][0] = true;
	}
	int cnt = 0;
	while (!que.empty()) {
		++cnt;
		int x, y;
		tie(x, y) = que.front();
		que.pop();
		if (x + 1 < rows && !grid[x + 1][y] && canReach(threshold, x + 1, y)) {
			grid[x + 1][y] = true;
			que.push(make_pair(x + 1, y));
		}
		if (y + 1 < cols && !grid[x][y + 1] && canReach(threshold, x, y + 1)) {
			grid[x][y + 1] = true;
			que.push(make_pair(x, y + 1));
		}
	}
	return cnt;
	
}
~~~



### **二刷：**

### **1、还是比较经典的方法**

运行时间：4ms  占用内存：504k

~~~cpp
int getValue(int row, int col) {
	int sum = 0;
	while (row != 0)
	{
		sum += row % 10;
		row = row / 10;
	}

	while (col != 0)
	{
		sum += col % 10;
		col = col / 10;
	}
	return sum;
}

void movingCountCore(int threshold, int rows, int cols, vector<vector<bool>>& visit, int row, int col, int &count) {
	if (row < 0 || col < 0 || row >= rows || col >= cols || visit[row][col] == true) return;
	if (getValue(row, col) > threshold) {
		visit[row][col] = true;
		return;
	}
	visit[row][col] = true;
	count++;

	movingCountCore(threshold, rows, cols, visit, row + 1, col, count);
	movingCountCore(threshold, rows, cols, visit, row - 1, col, count);
	movingCountCore(threshold, rows, cols, visit, row, col + 1, count);
	movingCountCore(threshold, rows, cols, visit, row, col - 1, count);

}


int movingCount(int threshold, int rows, int cols)
{
	if (rows < 0 || cols < 0) return 0;
	vector<vector<bool>> visit(rows, vector<bool>(cols, false));
	int count = 0;
	movingCountCore(threshold, rows, cols, visit, 0, 0, count);
	return count;

}
~~~


<p id = "机器人的运动范围"></p>

