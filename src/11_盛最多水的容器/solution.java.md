# 11. 盛最多水的容器

**目录：**

[TOC]

---

## 一、个人思路

由于两条线中较短的那一条线决定了可容纳的水量，因此设置双指针 `prev`、`tail` 分别指向前后两条线，同时设置变量 `max` 记录最大的盛水量。

开始时 `prev` 为 `0` 且 `tail` 为 `height.length - 1`，每一轮中拥有较小 `height` 的指针向对方移动，同时计算盛水量并与 `max` 进行比较；当两指针重合时结束，并输出 `max` 值，即为容器可以储存的最大水量。

代码实现如下：
```java
class Solution {
    public int maxArea(int[] height) {
        int prev = 0;
        int tail = height.length - 1;
        int max = 0;
        while (prev < tail) {
            int tMax = (tail - prev) * (height[prev] < height[tail] ? height[prev] : height[tail]);
            if (tMax > max) {
                max = tMax;
            }
            if (height[prev] < height[tail]) {
                prev++;
            } else {
                tail--;
            }
        }
        return max;
    }
}
```