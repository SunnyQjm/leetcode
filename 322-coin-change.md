# Leetcode 322 零钱兑换

> [零钱兑换](https://leetcode-cn.com/problems/coin-change/)

## 题目

给定不同面额的硬币 coins 和一个总金额 amount。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回 `-1`。

- **示例1：**

  ```
  输入: coins = [1, 2, 5], amount = 11
  输出: 3 
  解释: 11 = 5 + 5 + 1
  ```

- **示例2：**

  ```
  输入: coins = [2], amount = 3
  输出: -1
  ```

## 解答

- 思路：

  - 使用动态规划；

  - 定义f(n)为状态转移方程，表示凑n元所需的最少硬币数：

    $f(n) = \begin{cases}-1, & n < 0 \\ 0, & n == 0 \\ min{f(n - c) + 1 | c \in coins}, & n > 0 \end{cases}$

- 代码：

  ```python
  def coinChange(self, coins, amount):
      """
      :type coins: List[int],
      :type amount: int
      :rtype int
  
      (knowledge)
  
      思路：
      1. 使用动态规划；
      2. 定义f(n)为状态转移方程，表示凑n元所需的最少硬币数：
          -1 n < 0
          0  n == 0
          min{f(n - c) + 1 | c ∈ coins}
      """
      
      dp = [amount + 1 for i in range(amount + 1)]
  
      dp[0] = 0
  
      for i in range(len(dp)):
          for coin in coins:
              if i - coin < 0:
                  continue
              dp[i] = min(dp[i], dp[i - coin] + 1)
      return dp[amount] if dp[amount] != amount + 1 else -1
  ```

## 测试验证

```python
class Solution:
    def coinChange(self, coins, amount):
        """
        :type coins: List[int],
        :type amount: int
        :rtype int

        (knowledge)

        思路：
        1. 使用动态规划；
        2. 定义f(n)为状态转移方程，表示凑n元所需的最少硬币数：
            -1 n < 0
            0  n == 0
            min{f(n - c) + 1 | c ∈ coins}
        """

        dp = [amount + 1 for i in range(amount + 1)]

        dp[0] = 0

        for i in range(len(dp)):
            for coin in coins:
                if i - coin < 0:
                    continue
                dp[i] = min(dp[i], dp[i - coin] + 1)
        return dp[amount] if dp[amount] != amount + 1 else -1


if __name__ == '__main__':
    solution = Solution()
    print(solution.coinChange([1, 2, 5], 11), "= 3")
    print(solution.coinChange([2], 3), "= -1")
```