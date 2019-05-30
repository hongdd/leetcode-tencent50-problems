#### Day5

##### 爬楼梯

<https://leetcode-cn.com/problems/climbing-stairs/>

> 假设你正在爬楼梯。需要 *n* 阶你才能到达楼顶。
>
> 每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？
>
> **注意：**给定 *n* 是一个正整数

```
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
```

```
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
```

状态方程：F(n) = F(n-1)+F(n-2) 与Fibonacci数列问题相似

**递归解法：超过时间限制,因为重复计算太多。**

例如：n=10，按照递归来，要计算F(8)+F(9)，之后F(9)=F(8)+F(7)

F(8) = F(7)+F(6)。。。。从这里可以发现，F(8)和F(7)被重复计算。

```c++
class Solution {
public:
    int climbStairs(int n) {
        if(n==1) return 1;
        if(n==2) return 2;
        return climbStairs(n-1)+climbStairs(n-2);   
    }
};
```

**非递归解法：用一个数组来记录之前的值**



```c++
class Solution {
public:
    int climbStairs(int n) {
        if(n==1) return 1;
        if(n==2) return 2;
        
        vector<int> f(n+1);
        f[0] = 0;
        f[1] = 1;
        f[2] = 2;
        for(int i=3;i<=n;i++)
        {
            f[i] = f[i-1]+f[i-2];
        }
        return f[n];
    
    }
};
```

