## 题目描述

把只包含因子2、3和5的数称作丑数（Ugly Number）。例如6、8都是丑数，但14不是，因为它包含因子7。 习惯上我们把1当做是第一个丑数。求按从小到大的顺序的第N个丑数。



## 丑数

所谓丑数，就是不能被2，3，5以外的其他素数整除的数。1，2，3，4，5，6，8，9，10，12，15，16，18是最前面的13个丑数。



## 分析

丑数形式只能表达为
$$
uglyNum = 2^x*3^y*5^z
$$
应用到DP思想，第一个丑数必然是1，下一个丑数必然是已有丑数的基础上乘以2、3、5中的一个获得。
$$
k[i]=min(k[t2]*2,min(k[t3]*3,k[t5]*5));
$$


## 代码

```c++
int GetUglyNumber_Solution(int index) {
        if (index<=0) return 0;
        if (index==1) return 1;
        vector<int>k(index);k[0]=1;
        int t2=0,t3=0,t5=0;
        for (int i=1;i<index;i++) {
            k[i]=min(k[t2]*2,min(k[t3]*3,k[t5]*5));
            if (k[i]==k[t2]*2) t2++;
            if (k[i]==k[t3]*3) t3++;
            if (k[i]==k[t5]*5) t5++;
        }
        return k[index-1];
    }
```

