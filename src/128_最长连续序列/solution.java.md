# 128. 最长连续序列

**目录：**

[TOC]

---

## 一、题解思路

根据示例输入可知，输入的整数数组 `nums` 中可能包含重复元素，因此可以使用 `HashSet` 对 `nums` 进行去重预处理。

设置 `maxLength` 记录数字连续的最长序列长度。对于去重后的 `HashSet`，遍历其中的每个元素 `n`：如果 `n - 1` 存在于 `HashSet` 中，则以 `n - 1` 起始的序列长度一定大于以 `n` 起始的序列长度，因此不去计算以 `n` 起始的序列长度。

代码实现如下：
```java
class Solution {
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for (int i = 0; i < nums.length; i++) {
            set.add(nums[i]);
        }
        int maxLength = 0;
        for (int n : set) {
            int tMaxLength = 0;
            if (!set.contains(n - 1)) {
                tMaxLength++;
                while (set.contains(++n)) {
                    tMaxLength++;
                }
                if (tMaxLength > maxLength) {
                    maxLength = tMaxLength;
                }
            }
        }
        return maxLength;
    }
}
```