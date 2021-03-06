# Leetcode 14 最长公共前缀

> [最长公共前缀](https://leetcode-cn.com/problems/longest-common-prefix/)

## 题目

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 `""`。

- **示例1：**

  ```
  输入: ["flower","flow","flight"]
  输出: "fl"
  ```

- **示例2：**

  ```
  输入: ["dog","racecar","car"]
  输出: ""
  解释: 输入不存在公共前缀。
  ```

## 解答

- ### 解法1：

  - 思路：

    - 将两个字符串转为list；
    - 对两个list进行排序；
    - 然后注意比较对应位置的字符是否相等即可。

  - 代码：

    ```python
    def isAnagram(self, s1, s2):
        """
        排序对比法
    
        思路：
        1. 将两个字符串转为list；
        2. 堆两个list进行排序；
        3. 然后注意比较对应位置的字符是否相等即可
        """
        # 特判字符串长度不相同的情况
        # 其实这个不是必须的，只是在输入有可能长度不一的情况下，用这个可能可以提高一点性能
        if len(s1) != len(s2):
            return False
        list1 = list(s1)
        list2 = list(s2)
        list1.sort()
        list2.sort()
    
        for i in range(len(list1)):
            if list1[i] != list2[i]:
                return False
        return True
    ```

- ### 解法2：

  - 思路：

    - 创建两个长度位26的数组；
    - 各自统计两个字符串中每个字符出现的次数；
    - 接着对比两个数组即可。

    > ord => python中的一个内置函数，传入一个字符，会返回其对应的ASCII值

  - 代码：

    ```python
    def isAnagram2(self, s1, s2):
        """
        字符统计对比法(Knowledge)
    
        思路：
        1. 创建两个长度位26的数组；
        2. 各自统计两个字符串中每个字符出现的次数；
        3. 接着对比两个数组即可
    
        PS: ord => python中的一个内置函数，传入一个字符，会返回其对应的ASCII值
        """
        # 特判字符串长度不相同的情况
        # 其实这个不是必须的，只是在输入有可能长度不一的情况下，用这个可能可以提高一点性能
        if len(s1) != len(s2):
            return False
    
        c1 = [0] * 26
        c2 = [0] * 26
    
        # 统计字符出现的次数
        for i in range(len(s1)):
            c1[ord(s1[i]) - ord('a')] += 1
            c2[ord(s1[i]) - ord('a')] += 1
    
        # 对比统计结果
        for i in range(26):
            if c1[i] != c2[i]:
                return False
    
        return True
    ```

  ## 测试验证

  ```python
  class Solution:
      def isAnagram(self, s1, s2):
          """
          排序对比法
  
          思路：
          1. 将两个字符串转为list；
          2. 堆两个list进行排序；
          3. 然后注意比较对应位置的字符是否相等即可
          """
          # 特判字符串长度不相同的情况
          # 其实这个不是必须的，只是在输入有可能长度不一的情况下，用这个可能可以提高一点性能
          if len(s1) != len(s2):
              return False
          list1 = list(s1)
          list2 = list(s2)
          list1.sort()
          list2.sort()
  
          for i in range(len(list1)):
              if list1[i] != list2[i]:
                  return False
          return True
  
      def isAnagram2(self, s1, s2):
          """
          字符统计对比法(Knowledge)
  
          思路：
          1. 创建两个长度位26的数组；
          2. 各自统计两个字符串中每个字符出现的次数；
          3. 接着对比两个数组即可
  
          PS: ord => python中的一个内置函数，传入一个字符，会返回其对应的ASCII值
          """
          # 特判字符串长度不相同的情况
          # 其实这个不是必须的，只是在输入有可能长度不一的情况下，用这个可能可以提高一点性能
          if len(s1) != len(s2):
              return False
  
          c1 = [0] * 26
          c2 = [0] * 26
  
          # 统计字符出现的次数
          for i in range(len(s1)):
              c1[ord(s1[i]) - ord('a')] += 1
              c2[ord(s1[i]) - ord('a')] += 1
  
          # 对比统计结果
          for i in range(26):
              if c1[i] != c2[i]:
                  return False
  
          return True
  
  
  if __name__ == '__main__':
      solution = Solution()
  
      print(solution.isAnagram("heart", "earth"), " == True")
      print(solution.isAnagram("python", "typhon"), " == True")
      print(solution.isAnagram("qwert", "qwertg"), " == False")
  
      print(solution.isAnagram2("heart", "earth"), " == True")
      print(solution.isAnagram2("python", "typhon"), " == True")
      print(solution.isAnagram2("qwert", "qwertg"), " == False")
  ```

