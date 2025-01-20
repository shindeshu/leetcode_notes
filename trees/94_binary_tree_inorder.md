## Problem

Given the root of a binary tree, return the inorder traversal of its nodes' values.

 

Example 1:

Input: root = [1,null,2,3]

Output: [1,3,2]

Explanation:

## Solution

Recursive & Iterative

## Code

Recursive:

```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        res = []
        def dfs(root):
            if not root:
                return 
            dfs(root.left)
            res.append(root.val)
            dfs(root.right)
        dfs(root)
        return res
```

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
    
        res = []
        stack = []
        curr = root
        while curr or stack:
            # run while curr is non-null or stack is non-empty
            while curr:
                # run the pointer to leftmost possible
                stack.append(curr)
                curr = curr.left
            # now curr is null, but stack has all the left nodes
            # latest left node is given by stack pop
            curr = stack.pop()
            # thats our result
            res.append(curr.val)
            # now move to the right side of the leftmost node
            # and repeat everything again
            curr = curr.right 
        return res
```
