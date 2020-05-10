给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。（京东二面时遇到这道题）

```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        
        def preorder(root):
            if not root:
                return None
            
            if root == p or root == q:  # 直接返回，不用考虑root的左右子
                return root

            l = preorder(root.left)
            r = preorder(root.right)

            if l and r:
                return root
            return l or r
        
        return preorder(root)
```
虽然两周前刚做过，但是今天重新做的时候，还是重新思考，并用了不太简洁的语句实现。
