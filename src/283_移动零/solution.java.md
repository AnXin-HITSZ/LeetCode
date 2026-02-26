# 283. 移动零

**目录：**

[TOC]

---

# 一、题解思路

利用双指针思想，设置前指针 `pre` 用于检索元素，同时设置后指针 `tail` 用于指示下一个 `0` 元素将会被放置在哪一位置。

代码实现如下：
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int pre = 0;
        int tail = nums.length - 1;

        for (pre = 0; pre < tail; pre++) {
            if (nums[pre] == 0) {
                for (int i = pre; i < tail; i++) {
                    nums[i] = nums[i + 1];
                }
                nums[tail] = 0;
                pre -= 1;
                tail -= 1;
            }
        }
    }
}
```

需要注意的是，当检测到某一位置的元素为 `0` 并进行处理之后，需要将 `pre` 指针向前回溯 1 个单位，以防止该位置的紧随其后的位置也为 `0` 的情况。例如，当初始数组为 `nums = [0, 0, 1]` 时，如果未进行上述处理，则输出结果为 `[0, 1, 0]`，与预期结果 `[1, 0, 0]` 不相符。