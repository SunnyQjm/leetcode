# Leetcode 720 词典中最长的单词

> [词典中最长的单词](https://leetcode-cn.com/problems/longest-word-in-dictionary/)

## 题目

给出一个字符串数组`words`组成的一本英语词典。从中找出最长的一个单词，该单词是由`words`词典中其他单词逐步添加一个字母组成。若其中有多个可行的答案，则返回答案中字典序最小的单词。

## 解答

- 思路：

  - 用一个集合valid存储满足题目中限定的若干字符串；
  - 根据长度对原字符串列表排序，然后对排序后的字符串列表进行遍历；
  - 对每个字符串word，判断word[:-1]是否在valid当中，在则将其也放入到valid当中；
  - 最后对valid进行按字典序排序，然后返回长度最大的元素即可。

- 代码：

  ```python
  def longestWord(self, words: List[str]) -> str:
      """
      :type words: List[str]
      :rtype str
      
      (knowledge)
  
      思路：  
      1. 用一个集合valid存储满足题目中限定的若干字符串；
      2. 根据长度对原字符串列表排序，然后对排序后的字符串列表进行遍历；
      3. 对每个字符串word，判断word[:-1]是否在valid当中，在则将其也放入到valid当中
      4. 最后对valid进行按字典序排序，然后返回长度最大的元素即可
      """
  
      valid = {""}
  
      for word in sorted(words, key=len):
          if word[:-1] in valid:
              valid.add(word)
  
      return max(sorted(valid), key=len)
  ```

## 测试验证

```python
from typing import List


class Solution:
    def longestWord(self, words: List[str]) -> str:
        """
        :type words: List[str]
        :rtype str
        
        (knowledge)

        思路：  
        1. 用一个集合valid存储满足题目中限定的若干字符串；
        2. 根据长度对原字符串列表排序，然后对排序后的字符串列表进行遍历；
        3. 对每个字符串word，判断word[:-1]是否在valid当中，在则将其也放入到valid当中
        4. 最后对valid进行按字典序排序，然后返回长度最大的元素即可
        """

        valid = {""}

        for word in sorted(words, key=len):
            if word[:-1] in valid:
                valid.add(word)

        return max(sorted(valid), key=len)


if __name__ == '__main__':
    solution = Solution()
    words = ["a", "banana", "app", "appl", "ap", "apply", "apple"]
    print(solution.longestWord(words), "= apple")
```