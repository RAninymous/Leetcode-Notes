# 动态规划

## 经典模板

### 爬楼梯

**题干：**n级台阶，一次爬1或2，几种方式爬到顶。

链接：[70. 爬楼梯](https://leetcode.cn/problems/climbing-stairs/description/)

递归
```
class Solution:
    def climbStairs(self, n: int) -> int:
        @cache
        def dp(i: int) -> int:
            if i <= 1: return 1
            return dp(i-1) + dp(i-2)
        return dp(n)
```

递推：f[n]代表n级台阶的结果，f[0]相当于0级台阶。
```
class Solution:
    def climbStairs(self, n: int) -> int:
        f = [0] * (n+1)
        f[0], f[1] = 1, 1
        for i in range(2, n+1):
            f[i] = f[i-1] + f[i-2]
        return f[n]
```
> 不难看出，相当于斐波那契数列

空间优化：
```
class Solution:
    def climbStairs(self, n: int) -> int:
        a = b = 1
        for i in range(n-1):
            a, b = b, a+b
        return b
```

引申：
- [746. 使用最小花费爬楼梯](https://leetcode.cn/problems/min-cost-climbing-stairs/)：爬楼梯+cost
- [377. 组合总和 Ⅳ](https://leetcode.cn/problems/combination-sum-iv/)：自定义步幅的爬楼梯
