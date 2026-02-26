# 49. 字母异位词分组

**目录：**

[TOC]

---

## 一、题解思路

首先将输入的数组 `strs` 中的每个字符串按字母顺序重排组成该字符串的字母，将重排后构成的新的字符串作为哈希表的键，则重排后映射到同一键的单词即为字母异位词。

代码实现如下：
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, ArrayList<String>> map = new HashMap<>();
        for (int i = 0; i < strs.length; i++) {
            String str = strs[i];
            char[] arr = str.toCharArray();
            Arrays.sort(arr);
            String key = new String(arr);
            if (!map.containsKey(key)) {
                ArrayList<String> list = new ArrayList<>();
                list.add(strs[i]);
                map.put(key, list);
            } else {
                map.get(key).add(strs[i]);
            }
        }
        ArrayList<List<String>> list = new ArrayList<>();
        for (ArrayList<String> l : map.values()) {
            list.add(l);
        }
        return list;
    }
}
```