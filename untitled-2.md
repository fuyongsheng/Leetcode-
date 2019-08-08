# 88. Merge Sorted Array \#

![](.gitbook/assets/image%20%281%29.png)

给出两个已排序数组，其中含有的元素数目分别为m和n。假设第一个数组足够长，长度大于等于m + n。现在需要我们把所有的数已排好序的顺序放入第一个数组中。

## 方法一：

从后往前迭代。因为从前往后迭代会把我们要用的值覆盖掉，所以我们采取从后往前迭代的方法来处理该问题。从第一个数组的m + n - 1位开始往前填充。每一次填上两个数组尾端相对较大的那个数。若其中一个数组填完，则直接把另一个数组剩余的数填到前面。

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int len1 =  m - 1;
        int len2 = n - 1;
        for(int i = m + n - 1; i >= 0; i--){
            if(len1 >= 0 && len2 >= 0){
                if(nums1[len1] > nums2[len2])
                    nums1[i] = nums1[len1--];
                else
                    nums1[i] = nums2[len2--];
            }
            else{
                while(len1 >= 0){
                    nums1[i--] = nums1[len1--];
                }
                while(len2 >= 0){
                    nums1[i--] = nums2[len2--];
                }
            }
        }
    }
}
```

**时间复杂度\(Time Complexity\) :** O\(m + n\)          **空间复杂度\(Space Complexity\):** O\(1\)

