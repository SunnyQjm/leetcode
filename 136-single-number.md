# Leetcode 136 只出现一次的数字

> [只出现一次的数字](https://leetcode-cn.com/problems/single-number/)

## 题目

给定一个**非空**整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

**说明：**

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

- **示例1：**

  ```
  输入: [2,2,1]
  输出: 1
  ```

- **示例2：**

  ```
  输入: [4,1,2,1,2]
  输出: 4
  ```

## 解答

- 思路：

  - 异或(^)操作 => 是一种位操作，两个数字进行异或，对应位相同则为0,不同则为1（即相同的数字异或得0，0和任意数字异或都得原数字）；
  - 由于题中nums数组除了目标值以外，所有的数字都出现了两次，所以把数组中所有的数字都进行异或之后，得到的结果即为目标值；

- 代码：

  ```python
  def singleNumber(self, nums):
      """
      :type: nums: List[int]
      :rtype: int
  
      (Knowledge)
  
      思路：
      1. 异或(^)操作 => 是一种位操作，两个数字进行异或，对应位相同则为0,不同则为1（即相同的数字异或得0，0和任意数字异或都得原数字）
      2. 由于题中nums数组除了目标值以外，所有的数字都出现了两次，所以把数组中所有的数字都进行异或之后，得到的结果即为目标值
      """
      for i in range(1, len(nums)):
          nums[0] = nums[0] ^ nums[i]
      return nums[0]
  ```

## 测试验证

```python
class Solution:
    def singleNumber(self, nums):
        """
        :type: nums: List[int]
        :rtype: int

        (Knowledge)

        思路：
        1. 异或(^)操作 => 是一种位操作，两个数字进行异或，对应位相同则为0,不同则为1（即相同的数字异或得0，0和任意数字异或都得原数字）
        2. 由于题中nums数组除了目标值以外，所有的数字都出现了两次，所以把数组中所有的数字都进行异或之后，得到的结果即为目标值
        """
        for i in range(1, len(nums)):
            nums[0] = nums[0] ^ nums[i]
        return nums[0]


if __name__ == '__main__':
    solution = Solution()
    print(solution.singleNumber([2, 2, 1]), "= 1")
    print(solution.singleNumber([4, 1, 2, 1, 2]), "= 4")
```