# hot 100 recording

### \[160] 





### \[236] [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/)

> 递归
>
> 左子树里找到 -> 右子树里找到
>
> 使用此方法时，要求结点p、q都在树中

```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        return findLCA(root, p, q);
    }
    
    private TreeNode findLCA(TreeNode node, TreeNode p, TreeNode q) {
        if (node == null) {
            return null;
        }

        // If the current node is either p or q
        if (node == p || node == q) {
            return node;
        }

        TreeNode left = findLCA(node.left, p, q);
        TreeNode right = findLCA(node.right, p, q);

        // If p and q found in left and right of this subtree, root is LCA
        if (left != null && right != null) {
            return node;
        }

        // Otherwise, return the non-null value (either from left or right)
        return (left != null) ? left : right;
    }
}
```

