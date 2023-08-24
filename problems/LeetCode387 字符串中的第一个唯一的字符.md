
387. First Unique Character in a String
简单
691
相关企业
Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.

 

Example 1:

Input: s = "leetcode"
Output: 0
Example 2:

Input: s = "loveleetcode"
Output: 2
Example 3:

Input: s = "aabb"
Output: -1
 

Constraints:

1 <= s.length <= 105
s consists of only lowercase English letters.

## Python 3
```
class Solution:
    def firstUniqChar(self, s: str) -> int:
        count = collections.Counter(s)# Python基础库里词频统计的集成函数

        index = 0

        for ch in s:

            if count[ch] == 1:

                return index

            else:

                index += 1
```
 

        return -1
