# Day14_BinaryTree

## [226] [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/description/) ✅

交换左右结点

## [101] [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/description/) ✅ 

递归还是不太熟练

```
class Solution {
    public boolean compare(TreeNode left, TreeNode right) {
        if (left == null || right == null) {
            if (left != right) {
                return false;
            }
            return true;
        }
        if (left.val != right.val) {
            return false;
        }
        boolean bleft = compare(left.left, right.right);
        boolean bright = compare(left.right, right.left);
        return bleft && bright;

    }
    public boolean isSymmetric(TreeNode root) {
        if (root == null) {
            return true;
        }
        return compare(root.left, root.right);
    }
}
```

## [104] [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/) ✅



## [111] [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/description/) ✅