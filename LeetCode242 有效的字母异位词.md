

# 242.有效的字母异位词

给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的字母异位词。

注意：若 s 和 t 中每个字符出现的次数都相同，则称 s 和 t 互为字母异位词。

 

示例 1:

输入: s = "anagram", t = "nagaram"
输出: true
示例 2:

输入: s = "rat", t = "car"
输出: false


提示:

1 <= s.length, t.length <= 5 * 104
s 和 t 仅包含小写字母

进阶: 如果输入字符串包含 unicode 字符怎么办？你能否调整你的解法来应对这种情况？

> 统计在26个字母中出现的次序，最后两个进行对比
>
> | a    | b    | c    | d    | ...  |      | z    |
> | ---- | ---- | ---- | ---- | :--: | :--: | ---- |
> | 0    | 1    | 2    | 3    | ...  |      | 25   |
>
> 

```c
//c语言
#include<stdio.h>
#include<stdbool.h>//函数返回值为bool
#include<string.h>//参数为char,需要用到字符串运算

bool isAnagram(char* s,char* t){
    int statS[26]={0};/定义数组统计字符串中字母出现的次数
    int statT[26]={0};
    int lenS=strlen(s);
    int lenT=strlen(t);
    if (lenS!=lenT)
        return false;//如果长度不相同直接返回false
    int i;
    //拿出s的第i个字母，我们要知道这个字母要统计在数组的哪个位置
    for (i=0;i<lenS;i++){
        int index=s[i]-'a';//第i个字母在数组中对应的下标,用字母减去'a'就可以得到
        statS[index]++; 
    }
    for (i=0;i<lenT;i++){
        int index=t[i]-'a';
        statT[index]++; 
    }
    for (i=0;i<26;i++){
        if (statS[i]!=statT[i]){
            return false;
        }    
    }
    return true;
}

int main{
    char*s="hello";
    cha* t="abcde";
    printf("%d\n",isAngram(s,t));
    return 0;
    
}
```

参考：https://www.bilibili.com/video/BV13s41197my/?spm_id_from=333.999.0.0&vd_source=faf0776077e2eb91fbb8b452bbd732b0