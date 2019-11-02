# 希尔排序
  希尔排序是插入排序的一种，希尔排序的是为了解决直接插入排序算法的弊端而出现的。
  直接插入排序算法一般对小规模数据和基本有序数据的排序非常高效，但是当用到大规模或数据极为混乱的情况中，就显得差强人意，为了解决这个问题，就出现了希尔排序。
## 基本思路
  ![希尔排序](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1572706690407&di=6879991c7d6a8fe4748d7a2b31ac50f4&imgtype=0&src=http%3A%2F%2Fimg.mp.itc.cn%2Fupload%2F20160926%2F10d498ef63e74a6990b78f567f36805c_th.png)
    1. 把较大的数据集合分割成若干个小组(逻辑上分组)，然后对每一个小组分别进行插入排序，此时，插入排序所作用的数据量比较小，插入的效率比较高。
    2. 每个分组进行插入排序后，各个分组就变成了有序的了。
    
    基于这个思路，下面是代码实现：
    ```
    #include <stdio.h>
#include <stdlib.h>

void HellSort(int data,int length){
    for(int gap = length/2;gap>0;gap /= 2){//初始分组按照数组最长长度的一半，以后每一轮减小一半
        DirectlyInsertSort(data,gap,length);
    }
}

void DirectlyInsertSort(int data[],int gap,int length){//直接插入排序算法
    for(int i = gap;i<length;i++){
        int temp = data[i];
        int j = i;
        while(j-gap>=0&&data[j-gap]>temp){
            data[j] = data[j-gap];
            j = j - gap;
        }
        data[j] = temp;
    }
}

void print(int data[],int length){
    for(int i = 0;i<length;i++){
        printf("%d",data[i]);
    }
}

int main()
{
    int data[10] = {5,1,9,2,8,6,4,7,3,0};
    int length = 10;
    HellSort(data,length);
    print(data,length);
    return 0;
}

    ```
