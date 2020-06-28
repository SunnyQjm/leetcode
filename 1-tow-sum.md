# Leetcode 1 两数之和（Two sum）

> [两数之和](https://leetcode-cn.com/problems/two-sum/)

## 题目

给定一个整数数组 `nums` 和一个目标值 `target`，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

示例:

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

## 解答

- ### 解法1：

  - 思路：

    - 对每个值`tmp`，判断 `target - tmp` 是否在其右边的剩余数组当中；
    - 如果找到对应的匹配值，则返回两者的位置。

  - 代码：

    ```python
    def twoSum(self, nums, target):
        """
        (Knowledge)
        1. 对每个值tmp，判断 target - tmp 是否在其右边的剩余数组当中
        2. 如果找到对应的匹配值，则返回两者的位置
        """
        for i in range(len(nums)):
            tmp = nums[i]
            remain = nums[i + 1:]
            if target - tmp in remain:
                return [i, remain.index(target - tmp) + i + 1]
    ```

- ### 解法2：

  - 思路：

    - 用一个字典记录已经访问过的值及其下标；
    - 如果访问到某个值`num[i]`是，发现其匹配值 `target - nums[i]` 出现在 `dict` 里面，表示其左边有一个是可以与 `nums[i]` 想加得 `target` ，此时返回 `[dict[nums[i]], i]` 即为结果

  - 代码：

    ```python
    def twoSum2(self, nums, target):
        """
        (Knowledge)
        1. 用一个字典记录已经访问过的值及其下标
        2. 如果访问到某个值num[i]是，发现其匹配值target - nums[i] 出现在dict里面，表示其左边有一个是可以与nums[i]想加得target，
           此时返回[dict[nums[i]], i]即为结果
        """
        dict = {}
        for i in range(len(nums)):
            if target - nums[i] not in dict:
                dict[nums[i]] = i
            else:
                return [dict[target - nums[i]], i]
    ```

## 测试验证：

```python
class Solution:

    ################################################
    #### 解法一
    ################################################
    def twoSum(self, nums, target):
        """
        (Knowledge)
        1. 对每个值tmp，判断 target - tmp 是否在其右边的剩余数组当中
        2. 如果找到对应的匹配值，则返回两者的位置
        """
        for i in range(len(nums)):
            tmp = nums[i]
            remain = nums[i + 1:]
            if target - tmp in remain:
                return [i, remain.index(target - tmp) + i + 1]


    ################################################
    #### 解法2
    ################################################
    def twoSum2(self, nums, target):
        """
        (Knowledge)
        1. 用一个字典记录已经访问过的值及其下标
        2. 如果访问到某个值num[i]是，发现其匹配值target - nums[i] 出现在dict里面，表示其左边有一个是可以与nums[i]想加得target，
           此时返回[dict[nums[i]], i]即为结果
        """
        dict = {}
        for i in range(len(nums)):
            if target - nums[i] not in dict:
                dict[nums[i]] = i
            else:
                return [dict[target - nums[i]], i]

if __name__ == '__main__':
    solution = Solution()
    print(solution.twoSum([2, 7, 11, 15], 9))
    print(solution.twoSum2([2, 7, 11, 15], 9))
```



​	