# 57.Insert Interval \#

![](.gitbook/assets/image.png)

给出好几个已排好序的区间和一个新区间。要求把新区间插入到它应该在的位置，如果有重叠，则合并区间。

## 方法一：

跟上题解法类似，做了一点变化。

```text
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
         List<int[]> res = new ArrayList<>();
        
        // Traversal all interval and add them to the list
        for(int[] interval : intervals){
            //when current interval is larger than newInterval
            if(interval[0] > newInterval[1]){
                res.add(newInterval);
                newInterval = interval;
            }
            //when newInterval is larger than current interval
            else if(interval[1] < newInterval[0]){
                res.add(interval);
            }
            // newInterval is overlap with current interval
            else{
                newInterval[0] = Math.min(interval[0], newInterval[0]);
                newInterval[1] = Math.max(interval[1], newInterval[1]);
            }
        }
        // add the last interval left by the for loop
        res.add(newInterval);
        //convert list to array and return
        return res.toArray(new int[res.size()][]);
    }
}
```

**时间复杂度\(Time Complexity\) :** O\(n\)          **空间复杂度\(Space Complexity\):** O\(n\)

