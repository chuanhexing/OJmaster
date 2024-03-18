# 题目描述
- 标签：array
- 难度：简单
You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.

Increment the large integer by one and return the resulting array of digits.

Example 1:

Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
Incrementing by one gives 123 + 1 = 124.
Thus, the result should be [1,2,4].
Example 2:

Input: digits = [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.
Incrementing by one gives 4321 + 1 = 4322.
Thus, the result should be [4,3,2,2].
Example 3:

Input: digits = [9]
Output: [1,0]
Explanation: The array represents the integer 9.
Incrementing by one gives 9 + 1 = 10.
Thus, the result should be [1,0].
Constraints:

1 <= digits.length <= 100
0 <= digits[i] <= 9
digits does not contain any leading 0's.


# 解题思路
题目用数组表示一个十进制数字，要求加1后输出结果数组，先想简单情况是数组中最后一位数不是9，所以是最后一位数字加1，例如12+1=13、456+1=457；如果存在9，那么19+1=20，所以是9变成了0，前一位数加1,再进一步想如果是9+1=10,99+1=100,999+1=1000


# 代码
## Python3
```
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        for j in range(len(digits)-1, -1, -1):
                    if digits[j] == 9:
                        digits[j] = 0
                    else:
                        digits[j] += 1
                        return digits
        return [1] + digits
``` 
range(start, stop[, step])
参数说明：
start: 计数从 start 开始。默认是从 0 开始。例如range（5）等价于range（0， 5）;
stop: 计数到 stop 结束，但不包括 stop。例如：range（0， 5） 是[0, 1, 2, 3, 4]没有5
step：步长，默认为1。例如：range（0， 5） 等价于 range(0, 5, 1)
