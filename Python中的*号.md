https://bas.codes/posts/python-asterisks

大多数开发人员都知道星号 ( *) 字符是 Python 中的乘法运算符：

product = 4 * 2  # 8
但是，星号对于列表或字典数据结构有一些特殊含义。

*args和**kwargs
*args在函数定义中
Python 中星号运算符（也称为解构运算符）最广为人知的用法是它在函数中的用法。

假设您有一个可以添加值并返回这些值之和的函数：

def add(number_1, number_2):
    return number_1 + number_2

print(add(1,2)) # 3
如果您想对任意数量的值求和怎么办？您可以在参数名称前面添加一个星号，如下所示：

def add(*numbers):
    sum = 0
    for number in numbers:
        sum += number
    return sum
正如您可能已经从函数体中注意到的那样，我们期望它numbers是一个可迭代的。事实上，如果你检查类型，numbers是一个tuple. 事实上，我们现在可以使用任意数量的参数调用该函数：

add(1, 2, 3, 4) # 10
*在函数调用中
到目前为止我们已经看到，我们可以定义一个函数，以便它接受一个参数列表。但是，如果我们有一个带有一组固定参数的函数，并且想要向它传递一个值列表，该怎么办？考虑这个函数：

def add(number_1, number_2, number_3):
    return number_1 + number_2 + number_3
该函数仅需要3 个参数。假设我们有一个包含三个元素的列表。当然，我们可以这样调用我们的函数：

my_list = [1, 2, 3]

add(my_list[0], my_list[1], my_list[2])
幸运的是，解构运算符 ( *) 有两种工作方式。我们已经看到了函数定义中的用法，但我们也可以使用它来调用函数：

my_list = [1, 2, 3]

add(*my_list)
**kwargs在函数定义中
就像我们可以使用星号 ( *) 运算符解构列表一样，我们可以使用双星号 ( **) 运算符来解构 Python 函数中的字典。

考虑这样的函数：

def change_user_details(username, email, phone, date_of_birth, street_address):
    user = get_user(username)
    user.email = email
    user.phone = phone
    ...
如果我们使用关键字参数 ( kwargs) 来调用它，函数调用可能如下所示：

change_user_details('bascodes', email='blog@bascodes.example.com', phone='...', ...)
在这种情况下，我们可以像这样重写我们的函数以接受任意数量的关键字参数，然后将这些关键字参数表示为名为的字典kwargs：

def change_user_details(username, **kwargs):
    user = get_user(username)
    user.email = kwargs['email']
    user.phone = kwargs['phone']
    ...
当然，我们可以kwargs像 Python 中的任何其他字典一样使用字典，这样如果我们实际使用字典数据结构，函数可能会变得更干净一些，如下所示：

def change_user_details(username, **kwargs):
    user = get_user(username)
    for attribute, value in kwargs.items():
        setattr(user, attribute, value)
    ...
**在函数调用中
当然，该**运算符也适用于调用函数：

details = {
    'email': 'blog@bascodes.example.com',
    ...
}
change_user_detail('bascodes', **details)
限制函数的调用方式
仅关键字参数
函数定义中星号最令人惊讶的特征之一是它可以独立使用，即没有变量（参数）名称。话虽这么说，这是 Python 中完全有效的函数定义：

def my_function(*, keyword_arg_1):
    ...
但在这种情况下，独立的星号会做什么呢？正如我们在上面看到的，星号捕获列表中的所有（非关键字）参数。在我们的例子中，没有变量名可以进入列表。在之后*我们有一个名为 的变量keyword_arg_1。由于*已经匹配了所有位置参数，因此我们剩下keyword_arg_1，它必须用作关键字参数。

调用上面的函数my_function(1)会引发错误：

TypeError: my_function() takes 0 positional arguments but 1 was given
仅位置参数
如果我们想强制函数的用户仅使用位置参数——而不是仅在最后一个示例中使用关键字参数，该怎么办？

嗯，有一种非常 Pythonic 的方式。我们解释/符号（乘法的相反）来实现这个目的：

def only_positional_arguments(arg1, arg2, /):
    ...
令人惊讶的是，很少有 Python 开发人员知道这个技巧，它已通过PEP 570引入到 Python 3.8 中。

如果您使用 调用最后一个函数only_positional_arguments(arg1=1, arg2=2)，这将引发 TypeError：

TypeError: only_positional_arguments() got some positional-only arguments passed as keyword arguments: 'arg1, arg2'
*和**在文字中的用法
星号 ( *) 和双星号 ( **) 运算符不仅适用于函数定义和调用，还可以用于构造列表和字典。

构建列表
假设我们有两个列表并想要合并它们。

my_list_1 = [1, 2, 3]
my_list_2 = [10, 20, 30]
当然，我们可以将这些列表与+运算符合并：

merged_list = my_list_1 + my_list_2
然而，*操作符给了我们更多的灵活性。比方说，我们想在中间包含一个标量值，我们可以使用：

some_value = 42
merged_list = [*my_list_1, some_value, *my_list_2]

# [1, 2, 3, 42, 10, 20, 30]
构建字典
同样，对于列表和星号 ( *) 运算符适用的情况对于字典和双星号运算符 ( **) 也适用。

social_media_details = {
    'twitter': 'bascodes'
}

contact_details = {
    'email': 'blog@bascodes.example.com'
}

user_dict = {'username': 'bas', **social_media_details, **contact_details}
# {'email': 'blog@bascodes.example.com', 'twitter': 'bascodes', 'username': 'bas'}
解构列表
您可能已经知道，您可以将列表的元素拆分为多个变量，如下所示：

my_list = [1, 2, 3]
a, b, c = my_list

# a -> 1
# b -> 2
# c -> 3
*但是您是否知道，当您有任意长度的列表时，可以使用星号 ( ) 来分配变量？

比如说，您希望列表中的第一个元素和最后一个元素位于特定变量中。

您可以通过使用星号来完成此操作，如下所示：

my_list = [1, 2, 3]
a, *b, c = my_list
在此示例中，a现在包含 的第一个元素，并c包含 的最后一个元素my_list。b然而，里面是什么？

在 中b，有整个列表，不包括第一个和最后一个元素，即[2]。请注意，b现在是一个列表。

当我们查看更大的列表时，这个想法可能会变得更清晰一些：

my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
a, *b, c = my_list

# a -> 1
# b -> [2, 3, 4, 5, 6, 7, 8, 9]
# c -> 10