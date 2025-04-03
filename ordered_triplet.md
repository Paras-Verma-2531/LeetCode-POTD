# April 3,2025

## 300.Maximum Value Of Ordered Triplet II

```java
class Solution {
    public long maximumTripletValue(int[] nums) {
        long maxDiff = Integer.MIN_VALUE, maxTriplet = 0, maxNum=0;
        for(int i=0;i<nums.length;i++)
        {
            maxNum=Math.max(maxNum,nums[i]);
            if(i>=2)maxTriplet = Math.max(maxTriplet, maxDiff * (long)nums[i]);
            if(i>=1)maxDiff = Math.max(maxDiff, maxNum-nums[i]);
        }return maxTriplet;
    }
}
