7. Reverse Integer
中等
3.9K
相关企业
Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

 

Example 1:

Input: x = 123
Output: 321
Example 2:

Input: x = -123
Output: -321
Example 3:

Input: x = 120
Output: 21
 

Constraints:

-231 <= x <= 231 - 1

## Python3
```
class Solution:
    def reverse(self, x: int) -> int:
        R = 0   #返回值
        flag = 1 #标记输入值的正负
        if x<0:
            x = abs(x)
            flag = -1 #输入是负数
        while x != 0:
            R = R*10+x%10
            x = x//10
        if -2147483647<R< 2147483648:#判断是否越界
            return R*flag
        else:
            return 0
```
def twoSum(self, nums: List[int], target: int) -> List[int]:
这是3.5版中的新功能。
这就是所谓的“类型提示”（或“功能注释”；这些功能自Python 3.0起可用）。
-> List[int] 表示该函数应返回一个整数列表。
nums: List[int], target: int表示应该nums是整数列表，并且应该target是整数。
但是，这并不是硬性要求，即您仍然可以使用传递给这些参数的不同类型的对象来调用该函数，并且该函数还可以返回不同于整数列表的某些内容
（与Java等其他语言中提供错误类型的情况不同）会导致编译错误）。
换句话说：类型提示与程序执行无关，它们在运行时会被忽略（忽略类型提示只是默认行为，但可以在运行时通过来使用它们__annotations__，因此您可以对它们进行处理）。
