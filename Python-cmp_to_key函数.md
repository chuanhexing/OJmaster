cmp_to_key() 是 Python 内置模块 functools 的一个高阶函数，将 (旧式的) 比较函数转换为新式的 key function 

下面的代码是基于python@3的，python@2不适用。from functools import cmp_to_key
```python
nums = [1,5,8,7,9,3]
def cmp(x, y):
    return y-x
nums2 = sorted(nums, key=cmp_to_key(cmp))
print(nums,nums2)
```

输出结果：
[1, 5, 8, 7, 9, 3] 
[9, 8, 7, 5, 3, 1]

cmp_to_key()就是专门用于转化cmp参数到key参数的。cmp参数和key参数，是用于python内排序的参数，代表函数是sorted()和.sort()。这个cmp_to_key()函数就是用来python@2到python@3过度的一个临时产物。

from functools import cmp_to_key
nums = [7,3,8,1,9,5]
def cmp(x, y):
    return y-x
nums2 = sorted(nums, key=cmp_to_key(cmp))
print(nums,nums2)
# [7, 3, 8, 1, 9, 5] [1, 3, 5, 7, 8, 9]

使用方式二：
from functools import cmp_to_key
nums = [7,3,8,1,9,5]
nums.sort(key=cmp_to_key(cmp),reverse=True)
print(nums)
# [1, 3, 5, 7, 8, 9]

