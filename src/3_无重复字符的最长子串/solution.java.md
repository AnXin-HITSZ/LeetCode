# 3. 无重复字符的最长子串

**目录：**

[TOC]

## 一、题解思路

利用滑动窗口，左指针从前往后依次遍历字符串 s 中的每个元素，右指针向后移动，计算无重复字符的最长子串。

需要注意处理 `s.length() == 0` 以及 `s.length() == 1` 的边界情况。

代码实现如下：
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if (s.length() == 0) {
            return 0;
        }
        if (s.length() == 1) {
            return 1;
        }
        HashSet<Character> set = new HashSet<>();
        int left = 0;
        int right = left + 1;
        int max = 0;
        set.add(s.charAt(left));
        while (left < s.length() && right < s.length()) {
            while (right < s.length() && !set.contains(s.charAt(right))) {
                set.add(s.charAt(right++));
            }
            max = set.size() > max ? set.size() : max;
            set.remove(s.charAt(left));
            left++;
        }
        return max;
    }
}
```