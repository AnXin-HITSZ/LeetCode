# 15. 三数之和

**目录：**

[TOC]

---

## 一、题解思路

首先对数组 `nums` 进行升序排序。

对升序排序后的 `nums` 数组，依次遍历其元素 `nums[i]` 作为固定元素；同时设立左指针 `left` 和 右指针 `right`，初始时分别有 `left = i + 1` 和 `right = nums.length - 1`。每一轮次中根据 `nums[i] + nums[left] + nums[right]` 的值与 0 的大小关系，判断如何移动左右指针。

在获取符合条件的三元组的过程中，需要注意内、外层循环中对重复三元组的处理。

代码实现如下：
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        ArrayList<List<Integer>> lists = new ArrayList<>();
        for (int i = 0; i < nums.length; i++) {
            if (i != 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            int left = i + 1;
            int right = nums.length - 1;
            while (left < right) {
                if (nums[i] + nums[left] + nums[right] == 0) {
                    ArrayList<Integer> list = new ArrayList<>();
                    list.add(nums[i]);
                    list.add(nums[left]);
                    list.add(nums[right]);
                    lists.add(list);
                    while (left < right && nums[left + 1] == nums[left]) {
                        left++;
                    }
                    while (right > left && nums[right - 1] == nums[right]) {
                        right--;
                    }
                    left++;
                    right--;
                } else if (nums[i] + nums[left] + nums[right] > 0) {
                    right--;
                } else if (nums[i] + nums[left] + nums[right] < 0) {
                    left++;
                }
            }
        }
        return lists;
    }
}
```