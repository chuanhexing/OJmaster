对于定义一个简单的函数，Python 还提供了另外一种方法，即使用 lambda 表达式。

lambda 表达式，又称匿名函数，常用来表示内部仅包含 1 行表达式的函数。如果一个函数的函数体仅有 1 行表达式，则该函数就可以用 lambda 表达式来代替。

lambda 表达式的语法格式如下：
```
name = lambda [list] : 表达式

```
其中，定义 lambda 表达式，必须使用 lambda 关键字；[list] 作为可选参数，等同于定义函数是指定的参数列表；value 为该表达式的名称。

该语法格式转换成普通函数的形式，如下所示：
```
def name(list):
    return 表达式
name(list)
```
显然，使用普通方法定义此函数，需要 3 行代码，而使用 lambda 表达式仅需 1 行。


举个例子，如果设计一个求 2 个数之和的函数，使用普通函数的方式，定义如下：
def add(x, y):
    return x+ y
print(add(3,4))
程序执行结果为：
7

由于上面程序中，add() 函数内部仅有 1 行表达式，因此该函数可以直接用 lambda 表达式表示：
add = lambda x,y:x+y
print(add(3,4))
程序输出结果为：
7


可以这样理解 lambda 表达式，其就是简单函数（函数体仅是单行的表达式）的简写版本。相比函数，lamba 表达式具有以下  2 个优势：
对于单行函数，使用 lambda 表达式可以省去定义函数的过程，让代码更加简洁；
对于不需要多次复用的函数，使用 lambda 表达式可以在用完之后立即释放，提高程序执行的性能。


（2）将lambda函数作为参数传递给其他函数比如说结合map、filter、sorted、reduce等一些Python内置函数使用

fliter(lambda x:x%3==0,[1,2,3,4,5,6])

[3,6]


squares = map(lambda x:x**2,range(5)
print(lsit(squares))
[0,1,4,9,16]

与sorted函数结合使用，比如：创建由元组构成的列表：

```python
a=[('b',3),('a',2),('d',4),('c',1)]

#按照第一个元素排序
sorted(a,key=lambda x:x[0])
[('a',2),('b',3),('c',1),('d',4)]

#按照第二个元素排序
sorted(a,key=lambda x:x[1])
[('c',1),('a',2),('b',3),('d',4)]
```
与reduce函数结合使用

from functools import reduce
print(reduce(lambda a,b:'{},{}'.format(a,b),[1,2,3,4,5,6,7,8,9]))

1,2,3,4,5,6,7,8,9



在Python中有两种函数，一种是def定义的函数，另一种是lambda函数，也就是大家常说的匿名函数。今天我就和大家聊聊lambda函数，在Python编程中，大家习惯将其称为表达式。

1.为什么要用lambda函数？

先举一个例子：将一个列表里的每个元素都平方。

先用def来定义函数，代码如下

def sq(x):
    return x*x

map(sq,[y for y in range(10)])
再用lambda函数来编写代码

map(lambda x: x*x,[y for y in range(10)])
从这个简单的例子，我们可以看出，用lambda函数首先减少了代码的冗余，其次，用lambda函数，不用费神地去命名一个函数的名字，可以快速的实现某项功能，最后，lambda函数使代码的可读性更强，程序看起来更加简洁。

从上面这个简单的例子，也可以看出来lambda函数的语法是唯一的，其形式如下：

lambda argument_list:expersion
语法中的argument_list是参数列表，它的结构与Python中函数(function)的参数列表是一样的，例如

a,b
a=1,b=2
*args
**kwargs
a,b=1,*args
空
....
语法中的expression是一个关于参数的表达式，表达式中出现的参数需要在argument_list中有定义，并且表达式只能是单行的。比如以下的一些合法的表达式

1
None
a+b
sum(a)
1 if a >10 else 0
......
除了上面提到的lambda函数的优点外，我看有的文章说用lambda函数会提高效率，那究竟是不是呢？我们写一段代码来验证一下

import time


# 测试的Def函数
def square1(n):
    return n ** 2


# 测试的Lambda函数
square2 = lambda n: n ** 2

print(time.time())

# 使用Def函数
i = 0
while i < 1000000000:
    square1(100)
    i += 1

print(time.time())

# 使用lambda函数
i = 0
while i < 1000000000:
    square2(100)
    i += 1

print(time.time())

1413272496.27
1413272703.05 (Def   函数:207s)
1413272904.49 (Lambda函数:201s)
从上面可以看出，两种的所需的时间差不多，效率丝毫不受影响。

2.lambad函数的用法上面也讲到了匿名函数的优点，那它到底有哪些用处呢？

（1）直接赋给一个变量，然后再像一般函数那样调用

c=lambda x,y,z:x*y*z
c(2,3,4)

24
当然，也可以在函数后面直接传递实参

(lambda x:x**2)(3)
9
（2）将lambda函数作为参数传递给其他函数比如说结合map、filter、sorted、reduce等一些Python内置函数使用，下面举例说明。

fliter(lambda x:x%3==0,[1,2,3,4,5,6])

[3,6]


squares = map(lambda x:x**2,range(5)
print(lsit(squares))
[0,1,4,9,16]
与sorted函数结合使用，比如：创建由元组构成的列表：

a=[('b',3),('a',2),('d',4),('c',1)]
按照第一个元素排序

sorted(a,key=lambda x:x[0])
[('a',2),('b',3),('c',1),('d',4)]
按照第二个元素排序

sorted(a,key=lambda x:x[1])
[('c',1),('a',2),('b',3),('d',4)]
与reduce函数结合使用

from functools import reduce
print(reduce(lambda a,b:'{},{}'.format(a,b),[1,2,3,4,5,6,7,8,9]))

1,2,3,4,5,6,7,8,9
（3）嵌套使用将lambda函数嵌套到普通函数中，lambda函数本身做为return的值

def increment(n):
    return lambda x:x+n

f=increment(4)
f(2)
6
（4）字符串联合，有默认值，也可以用x=(lambda...)这种格式

x=(lambda x='Boo',y='Too',z='Z00'：x+y+z)
print(x('Foo'))

'FooTooZoo'
（5）在tkinter中定义内联的callback函数

import sys
from tkinter import Button,mainloop

x=Button(text='Press me',command=(lambda :sys.stdout.write('Hello,World\n')))
x.pack()
x.mainloop()
这段代码还是挺有意思的，希望小伙伴们可以复制粘贴运行一下哈。（6）判断字符串是否以某个字母开头有

Names = ['Anne', 'Amy', 'Bob', 'David', 'Carrie', 'Barbara', 'Zach']
B_Name= filter(lambda x: x.startswith('B'),Names)
print(B_Name)

['Bob', 'Barbara']
（7）求两个列表元素的和

a = [1,2,3,4]
b = [5,6,7,8]
print(list(map(lambda x,y:x+y, a,b)))

[6,8,10,12]
（8）求字符串每个单词的长度

sentence = "Welcome To Beijing!"
words = sentence.split()
lengths  = map(lambda x:len(x),words)
print(list(lengths))
[7,2,8]
总结

对于lambda函数的使用在Python社区一直存在争议，支持一方认为lambad函数的使用，使得Python代码更加紧凑，更加Pythonic；反对方则认为Python的lambda函数限制多多，最严重的当属于它只能由一条表达式组成，用多了以后反而使得程序看起来不那么清晰。

但我个人觉得作为一个Python的初级用户，lambda函数确实让编码更简洁，更省事，一句话好用就行，其余的看神仙打架吧！

56.合并区间
[][def]

[56.合并区间]: /problems/56.合并区间.md