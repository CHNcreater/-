# 插入排序算法
  插入排序算法的基本思想就是向已排序好的序列插入带排序的数据，插入后得到的序列仍然是有序序列。
## 插入排序算法的分类：
  插入排序算法根据实现的方式不同还可以分为：直接插入排序算法、二分插入排序算法、希尔排序算法，接下来将对每一个算法进行详细介绍。
### 直接插入排序算法
  1. 基本思想图解：  
  ![直接插入排序](https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=242458598,74617249&fm=26&gp=0.jpg)
  2. C语言代码实现：
  ```
#include <stdio.h>
#include <stdlib.h>

void InsertSort(int data[],int length){
    int i,j,temp;
    for(i = 1;i<length;i++){
        j = i;
        temp = data[i];
        while(j>0&&temp<data[j-1]){
            data[j] = data[j-1];
            j--;
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
    int data[10] = {5,2,9,8,3,4,7,6,1,0};
    int length = 10;
    InsertSort(data,length);
    print(data,length);
    return 0;
}
  ```
3. 时间复杂度分析
  平均时间复杂度为O(n^2)  
  数据基本有序时时间复杂度为O(n)  
  可以证明的是直接插入排序算法平均时间复杂度为O(n^2/4)  
  当n<16时，n^2/4<nlogn，因此当n＜16时，直接插入排序算法比nlogn的算法快，因此直接插入排序算法更适合小数据集。  
  
