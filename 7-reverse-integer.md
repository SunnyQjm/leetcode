# Leetcode 7 整数反转

> [整数反转](https://leetcode-cn.com/problems/reverse-integer/)

## 题目

给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

- **示例1：**

  ```
  输入: 123
  输出: 321
  ```

- **示例2：**

  ```
  输入: -123
  输出: -321
  ```

- **示例3：**

  ```
  输入: 120
  输出: 21
  ```

**注意:**

假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 $[−2^{31},  2^{31} − 1]$。请根据这个假设，如果反转后整数溢出那么就返回 0。

## 解答

- 思路：

  - 首先记录输入值的符号（是正数还是负数），然后取其绝对值|x|进行处理；
  - 接着用一个long型（Python里面的数字完全够大）存储结果；
  - 将|x|从个位开始向左遍历，依次叠加到结果里面；
  -  最后判断结果是否移出（与32位有符号整形的最大值和最小值进行比对）。

- 代码：

  ```python
  INT_MAX_VAL = 2147483647
  INT_MIN_VAL = -2147483648
  
  def reverse(self, x):
      """
      (Knowledge)
  
      思路：
      1. 首先记录输入值的符号（是正数还是负数），然后取其绝对值|x|进行处理
      2. 接着用一个long型（Python里面的数字完全够大）存储结果；
      3. 将|x|从个位开始向左遍历，依次叠加到结果里面；
      4. 最后判断结果是否溢出（与32位有符号整形的最大值和最小值进行比对）
      """
      isNegitive = -1 if x < 0 else 1
      result, x = 0, abs(x)
      while x > 0:
          result = result * 10 + x % 10
          x = x // 10
      result = isNegitive * result
  
      return 0 if result > INT_MAX_VAL or result < INT_MIN_VAL else result
  ```

## 测试验证

```python
INT_MAX_VAL = 2147483647
INT_MIN_VAL = -2147483648

class Solution:
    def reverse(self, x):
        """
        (Knowledge)

        思路：
        1. 首先记录输入值的符号（是正数还是负数），然后取其绝对值|x|进行处理
        2. 接着用一个long型（Python里面的数字完全够大）存储结果；
        3. 将|x|从个位开始向左遍历，依次叠加到结果里面；
        4. 最后判断结果是否溢出（与32位有符号整形的最大值和最小值进行比对）
        """
        isNegitive = -1 if x < 0 else 1
        result, x = 0, abs(x)
        while x > 0:
            result = result * 10 + x % 10
            x = x // 10
        result = isNegitive * result

        return 0 if result > INT_MAX_VAL or result < INT_MIN_VAL else result


if __name__ == '__main__':
    solution = Solution()
    print(solution.reverse(123), "= 321")
    print(solution.reverse(-123), "= -321")
    print(solution.reverse(120), "= 21")
```

