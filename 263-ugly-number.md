# Leetcode 263 丑数

> [丑数](https://leetcode-cn.com/problems/ugly-number/)

## 题目

编写一个程序判断给定的数是否为丑数。

丑数就是只包含质因数 `2, 3, 5` 的**正整数**。

- **示例1：**

  ```
  输入: 6
  输出: true
  解释: 6 = 2 × 3
  ```

- **示例2：**

  ```
  输入: 8
  输出: true
  解释: 8 = 2 × 2 × 2
  ```

- **示例3：**

  ```
  输入: 14
  输出: false 
  解释: 14 不是丑数，因为它包含了另外一个质因数 7。
  ```

**说明：**

1. `1` 是丑数。
2. 输入不会超过 32 位有符号整数的范围: $[−2^{31}, 2^{31} − 1]$。

## 解答

- 思路：

  - 依次判断能否用2, 3, 5整除，可以则将num处理对应质因子；
  - 判断最后结果是否为1。

- 代码：

  ```python
  def isUgly(self, num):
      """
      :type num: int
      :rtype bool
  
      (knowledge)
  
      思路：
      1. 依次判断能否用2, 3, 5整除，可以则将num处理对应质因子；
      2. 判断最后结果是否为1
      """
      if num == 0:
          return False
      while not num % 5:
          num /= 5
      while not num % 3:
          num /= 3
      while not num % 2:
          num /= 2
      return num == 1
  ```

## 测试验证

```python
class Solution:
    def isUgly(self, num):
        """
        :type num: int
        :rtype bool

        (knowledge)

        思路：
        1. 依次判断能否用2, 3, 5整除，可以则将num处理对应质因子；
        2. 判断最后结果是否为1
        """
        if num == 0:
            return False
        while not num % 5:
            num /= 5
        while not num % 3:
            num /= 3
        while not num % 2:
            num /= 2
        return num == 1


if __name__ == '__main__':
    solution = Solution()
    print(solution.isUgly(6), "= True")
    print(solution.isUgly(8), "= True")
    print(solution.isUgly(14), "= False")
```