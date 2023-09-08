剑指 Offer 45. 把数组排成最小的数
中等
681
相关企业
输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。

 

示例 1:

输入: [10,2]
输出: "102"
示例 2:

输入: [3,30,34,5,9]
输出: "3033459"
 

提示:

0 < nums.length <= 100
说明:

输出结果可能非常大，所以你需要返回一个字符串而不是整数
拼接起来的数字可能会有前导 0，最后结果不需要去掉前导 0

# 思考


## Python3

```python
import functools

class Solution:
    def minNumber(self, nums: List[int]) -> str:
        def cmp(a, b):
            if a + b == b + a:
                return 0
            elif a + b > b + a:
                return 1
            else:
                return -1

        nums_s = list(map(str, nums))
        nums_s.sort(key=functools.cmp_to_key(cmp))
        return ''.join(nums_s)

```


错误解法
最后执行的输入
[0,0]
```python
import functools

class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        def cmp(a, b):
            if a + b == b + a:
                return 0
            elif a + b < b + a:
                return 1
            else:
                return -1

        nums_s = list(map(str, nums))
        nums_s.sort(key=functools.cmp_to_key(cmp))
        return ''.join(nums_s)

```
直接copy剑指offer45然后修改了a+b<b+a