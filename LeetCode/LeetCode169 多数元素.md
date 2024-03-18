给定一个大小为 n 的数组 nums ，返回其中的多数元素。多数元素是指在数组中出现次数 大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

 

示例 1：

输入：nums = [3,2,3]
输出：3
示例 2：

输入：nums = [2,2,1,1,1,2,2]
输出：2


提示：
n == nums.length
1 <= n <= 5 * 104
-109 <= nums[i] <= 109



```c
//排序后输出中位数！！超出时间限制
int majorityElement(int* nums, int numsSize){
    int i,j;
    int temp;
    for(j=0;j<numsSize;j++){
        for(i=0;i<numsSize-1;i++){
            if (nums[i]>nums[i+1]){
                temp=nums[i];
                nums[i]=nums[i+1];
                nums[i+1]=temp;}
        }
    }
    return nums[numsSize/2];

}
```



> 利用栈数据结构，
>
> 时间复杂度$O(n)$，空间复杂度为$O(n)$

```c
#include<stdio.h>
#inlcude<stdlib.h>
#include<stdbool.h>

int majorityElement(int* nums, int numsSize){
    int* stack=malloc(sizeof(int)* numsSize);
    int top=-1;
    
    int i;
    for(i=0;i<numsSize;i++){
        if(top==-1){
            stack[++top]=nums[i];
        }
        else if(stack[top]==nums[i]){
            stack[++top]=nums[i];
        }
        else {
            top--;
        }
    }
    return stack[0];
}

int main(){
    int nums[]={1,1,1,1,2,3,4};
    int result=majorityElement(nums,7);
    printf("result=%d\n",result);
    return 0;
}
//降低空间复杂度
int majorityElement(int* nums, int numsSize){
    int cand;//记录栈顶元素
    int count=0;//记录现在栈中有多少个数
    int i;
    for(i=0;i<numsSize;i++){
        if(count==0){
            cand=nums[i];
            count++;
        }
        else if(cand==nums[i]){
            count++;
        }
        else {
            count--;
        }
    }
    return cand;
}
```



