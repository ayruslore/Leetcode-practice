## Question : Validate Binary Search Tree

Given the `root` of a binary tree, determine if it is a valid binary search tree (BST).

A **valid BST** is defined as follows:
1. The left subtree of a node contains only nodes with keys **less than** the node's key.
1. The right subtree of a node contains only nodes with keys **greater than** the node's key.
1. Both the left and right subtrees must also be binary search trees.

**Example:**
```
Input: root = [2,1,3]
Output: True
```

## Solution :

```python3
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        pre, cur, stack = None, root, []
        while stack or cur:
            while cur:
                stack.append(cur)
                cur = cur.left
            s = stack.pop()
            if pre and s.val <= pre.val:
                return False
            pre, cur = s, s.right
        return True
```