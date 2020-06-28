# Leetcode 226 翻转二叉树

> [翻转二叉树](https://leetcode-cn.com/problems/invert-binary-tree/)

## 题目

翻转一棵二叉树。

**示例：**

输入：

```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

输出：

```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

## 解答

- 思路：

  - 每次交换当前节点的两个子树；
  - 然后递归对左右子树进行翻转。

- 代码：

  ```python
  def invertTree(self, root):
      """
      :type root: TreeNode
      :rtype TreeNode
  
      (knowledege)
  
      思路：
      1. 每次交换当前节点的两个子树；
      2. 然后递归对左右子树进行翻转
      """
      if not root:
          return None
      root.left, root.right = root.right, root.left
      
      self.invertTree(root.left)
      self.invertTree(root.right)
      return root
  ```

## 测试验证

```python
class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None

    def __repr__(self):
        if self:
            return "{}->{}->{}".format(self.val, repr(self.left), repr(self.right))


class Solution:
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype TreeNode

        (knowledege)

        思路：
        1. 每次交换当前节点的两个子树；
        2. 然后递归对左右子树进行翻转
        """
        if not root:
            return None
        root.left, root.right = root.right, root.left
        
        self.invertTree(root.left)
        self.invertTree(root.right)
        return root


if __name__ == '__main__':
    solution = Solution()
    root = TreeNode(4)
    root.left = TreeNode(2)
    root.left.left = TreeNode(1)
    root.left.right = TreeNode(3)
    root.right = TreeNode(7)
    root.right.left = TreeNode(6)
    root.right.right = TreeNode(9)

    print(solution.invertTree(root))
```