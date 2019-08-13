# 95.Unique Binary Search Trees II \#

![](.gitbook/assets/image%20%2833%29.png)

给定一个数n，求出所有由1到n节点所构成的BST。

## 方法一：

递归。把每一个节点都尝试作为根节点，试遍所有结果。对每个节点的左子树和右子树再分别调用函数，取得所有可能的左子树和右子树。

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    // The idea of this algorithm is take each node as root node, and we need to consider all of its possible left sub-tree and right sub-tree. The genTree function can handle all the siutations by using recursive method
    public List<TreeNode> generateTrees(int n) {
        if(n == 0) return new ArrayList<TreeNode>();
        return genTree(1, n);
    }
    
    public List<TreeNode> genTree(int start, int end){
        List<TreeNode> list = new ArrayList<TreeNode>();
        if(start > end) list.add(null);
        
        for(int idx = start; idx <= end; idx++){
            List<TreeNode> leftlists = genTree(start, idx - 1);
            List<TreeNode> rightlists = genTree(idx + 1, end);
            for(TreeNode left : leftlists){
                for(TreeNode right : rightlists){
                    TreeNode root = new TreeNode(idx);
                    root.left = left;
                    root.right = right;
                    list.add(root);
                }
            }
        }
        return list;
    }
}
```

**时间复杂度\(Time Complexity\) :** O\(\)          **空间复杂度\(Space Complexity\):** O\(\)

