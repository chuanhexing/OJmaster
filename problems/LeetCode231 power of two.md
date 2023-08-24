

给你一个整数 n，请你判断该整数是否是 2 的幂次方。如果是，返回 true ；否则，返回 false 。

如果存在一个整数 x 使得 n == 2x ，则认为 n 是 2 的幂次方。

 

示例 1：

输入：n = 1
输出：true
解释：20 = 1
示例 2：

输入：n = 16
输出：true
解释：24 = 16
示例 3：

输入：n = 3
输出：false
示例 4：

输入：n = 4
输出：true
示例 5：

输入：n = 5
输出：false


提示：

-231 <= n <= 231 - 1


进阶：你能够不使用循环/递归解决此问题吗？

来源：力扣（LeetCode）
链接：https://leetcode.cn/problems/power-of-two
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



```c
#include <stdio.h>
#include <stdbool.h>//需要用到bool数据类型

bool isPowerOfTwo(int n){
    if (n == 0)
        return false;
    while(n % 2 == 0) {
        n = n / 2;
    }
    if (n == 1) {
        return true;
    }
    else {
        return false;
    }

}//超时的情况下考虑特殊情况，n=0

int main() {
    printf("%d\n", isPowerOfTwo(4));
}
```





```c
//递归
bool isPowerOfTwo(int n){
    if (n == 0)
        return false;
    if (n == 1) {
        return true;
    }
    else if(n%2==0) {
        return isPowerOfTwo(n/2); 
    }
    else {
        
        return false;   
    }

}
```



```c
//位运算,负数也会通过，所以要在开始把负数情况排除
bool isPowerOfTwo(int n){
    if (n <= 0)
        return false;
    else if (n == 1) {
        return true;
    }
    else {
        if ((n & (n-1))==0) {
            return true;
        }
        else {
            return false;
        }
    }

}
```

