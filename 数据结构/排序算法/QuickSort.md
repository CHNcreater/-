# 快速排序

  快速排序属于交换排序的一种，并采用递归的方式处理排序问题。
## 思路过程
  1. 快速排序的思维过程是：在待排序序列中取第一个元素作为基准元素，将原排序序列分为三部分，左边部分为比自己小的元素，右边部分为比自己大的元素，并将该元素放置在这两部分的中间，
  这就是快速排序算法一趟的结果。
  2. 接着对上一步划分的左右两部分分别重复第一步的操作。
  
  ![快速排序](https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=2204553250,24011707&fm=26&gp=0.jpg)
  
  **代码实现**
  ```
  #include <stdio.h>
#include <stdlib.h>

#define MAXSIZE 100

int Apart(int data[],int low, int high){
    int temp = data[low];//取第一个元素为基准元素
    while(low<high){
        while(low<high&&data[high]>=temp){//从后向前比较
            high--;
        }
        data[low] = data[high];//发现比基准小的元素，移动到前面low指针处
        while(low<high&&data[low]<=temp){//从前向后比较
            low++;//比基准小则不需要移动数据，将指针后移
        }
        data[high] = data[low];//发现比指针大的元素，移动到high指针处
    }
    data[low] = temp;
    return low;//high与low相同时，返回开头的基准元素位置
}

void quicksort(int data[],int low,int high){
    if(low<high){
        int k = Apart(data,low,high);
        quicksort(data,0,k-1);//继续对左部做相同操作
        quicksort(data,k+1,high);//对右部进行相同操作
    }
}

void print(int data[],int length){//打印数组元素
    for(int i = 0;i<length;i++){
        printf("%d",data[i]);
    }
}

int main(){
    int data[10] = {5,1,9,6,4,3,7,8,2,0};
    int length  = 10;
    quicksort(data,0,length-1);
    print(data,length);
    return 0;
}
  ```
