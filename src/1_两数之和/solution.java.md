# 1. 两数之和

**目录：**

[TOC]

---

## 一、题解思路

对于数组 `nums` 使用两重嵌套 `for` 循环遍历，找出和为目标值 `target` 的那两个整数，将这两个整数的下标存放在新另创建的结果数组中返回。

代码实现如下：
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    int[] ret = new int[2];
                    ret[0] = i;
                    ret[1] = j;

                    return ret;
                }
            }
        }

        return null;
    }
}
```

算法的时间复杂度为 $O(n^2)$。