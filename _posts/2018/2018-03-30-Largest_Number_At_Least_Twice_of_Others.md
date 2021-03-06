---
layout: post
title: 747. Largest Number At Least Twice of Others
categories: [leetcode]
---

#### QUESTION:

In a given integer array `nums`, there is always exactly one largest element.

Find whether the largest element in the array is at least twice as much as every other number in the array.

If it is, return the **index** of the largest element, otherwise return -1.

**Example 1:**

```
Input: nums = [3, 6, 1, 0]
Output: 1
Explanation: 6 is the largest integer, and for every other number in the array x,
6 is more than twice as big as x.  The index of value 6 is 1, so we return 1.
```

 

**Example 2:**

```
Input: nums = [1, 2, 3, 4]
Output: -1
Explanation: 4 isn't at least as big as twice the value of 3, so we return -1.
```

 

**Note:**

1. `nums` will have a length in the range `[1, 50]`.
2. Every `nums[i]` will be an integer in the range `[0, 99]`.

#### EXPLANATION:

其实就是计算出最大的两位数，同时记录最大数字的index。

然后比较最大的两个数字，最大的数字是否是第二大数字的两倍。

#### SOLUTION:

```JAVA
class Solution {
    public int dominantIndex(int[] nums) {
        if(nums==null||nums.length==0)return -1;
        int biggest = nums[0];
        int second = -1;
        int result = 0;
        for(int i = 1;i<nums.length;i++){
            if(nums[i]>biggest){
                second = biggest;
                biggest = nums[i];
                result=i;
            } else if(nums[i]>second) second = nums[i];
        }
        return biggest>=second*2?result:-1;
    }
}
```

