---
title: 数据结构（python）
date: 2024-02-16T10:02:39Z
lastmod: 2024-11-26T09:15:18Z
tags: [数据结构,python]
thumbnail: images/2024/02/16/3EF5D6D07CECB3A63168D66522FFFBA6-20240217111109-q3bc7sv.jpg
hero: images/2024/02/16/3EF5D6D07CECB3A63168D66522FFFBA6-20240217111109-q3bc7sv.jpg
---

对数据结构的简单介绍，几大经典的排序，二叉树，堆、栈、队列等，以及对应实现的python代码。

<!-- more -->

# 数据结构（python）

　　算法：一个计算过程

　　**程序 = 数据结构 + 算法**

　　数据结构是指相互之间存在着一种或多种关系的数据元素的集合和该集合中数据元素之间的关系组成

　　数据结构就是设计数据以何种方式组织并存储在计算机中

　　eg:列表，集合与字典

　　**分类：** 线性结构，树结构，图结构，集合

　　线性结构：数据中的元素存在一对一的相互关系

　　树结构：数据结构中的元素存在一对多的关系

　　图结构：数据结构中的元素存在多对多的相互关系

　　存储结构 顺序存储，链式存储，索引，散列

　　‍

# 查找(Search)

## 复杂度

### 时间复杂度

　　用来评估算法运行效率的一个式子

```python
print('hello world')    # O(1)

for i in range(n):   # O(n)
	print("hello world")

for i in range(n):   # O(n^2)
	for j in range(n):
		print("hello world")

print("hello")    # O(1)
print("world")

for i in range(n):   # O(n^2)
	print("hello")
	for j in range(n):
		print("world")

while n > 1:   # O(log2(n))或者是O(logn)
	print(n)
	n = n // 2

```

　　时间复杂度是用来估计算法运行时间的一个式子（单位）

　　一般来说，时间复杂度高的算法比复杂度低的算法满

　　常见的时间复杂度（按效率排序）

　　O(1) < $O_{log(n)}$ < O(n) < O(nlogn) < O(n<sup>2</sup>) <  O( n<sup>2</sup> logn ) < O( n<sup>3</sup>)

　　复杂问题的时间复杂度

　　O(n!) O(2<sup>n</sup>) O(n<sup>n</sup>)

　　log

　　快速判断时间复杂度（适用于绝大多数简单情况）

　　1.确定问题规模

　　2.循环减半过程 logn

　　3.k 层关于 n 的循环 n<sup>k</sup>

　　常量为1

　　复杂情况：根据算法执行过程判断

### 空间复杂度

　　用来评估算法内存占用大小的式子

　　空间复杂度的表示方式与时间复杂度完全一样

　　算法使用了几个变量：O(1)

　　算法使用了长度为 n 的一维列表：O(n)

　　算法使用了 m 行 n 列的二维列表：O(mn)

　　“空间换时间”

### 递归

　　递归的特点：调用自身，结束条件

```python
def func3(x):  # 输出321
    if x > 0:
        print(x)
        func3(x - 1)


def func4(x):  # 输出123
    if x > 0:
        func4(x - 1)
        print(x)
```

#### 汉诺塔问题

![image](images/2024/02/16/image-20231206193234-66hhww3.png "汉诺塔问题")

n 个盘子时：

1.把 n-1 个圆盘从 A 经过 C 移动到 B

2.把 n 个圆盘从 A 移动到 C

3.把 n-1 个小圆盘从 B 经过 A 移动到 C

　　在一些数据元素中，通过一定的方法找出与给定关键字相同的数据元素的过程

　　**列表查找（线性表查找）**

　　从列表中查找指定元素

　　输入：列表,待查找元素

　　输出：元素下标（未找到元素时一般返回 None 或-1）

　　内置列表查找函数：index() （第一个）线性查找

## 顺序查找（Linear Search）

　　线性查找，从列表的第一个元素开始，顺序进行搜索，直到找到元素或搜索到列表最后一个元素为止。

```python
def linear_search(li, val):
    for ind, v in enumerate(li):
        if v == val:
            return ind
    else:
        return None
```

　　‍

## 二分查找（Binary Searh）

　　折半查找，从有序列表的初始候选区 li[0:n]开始，通过对待查找的值与候选区中间值的比较，可以使候选区减少一半。

```python
def binary_search(li, val):   # 列表和要查找的元素
    left = 0
    right = len(li) - 1
    while left <= right:  # 候选区有值
        mid = (left + right) // 2
        if li[mid] == val:
            return mid
        elif li[mid] > val:  # 带查找的值在mid左侧
            right = mid - 1
        else:   # mid<val, 待查找的值在mid右侧
            left = mid + 1
    else:
        return None


ci = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(binary_search(ci, 3))
# 有顺序且有大小的时候或者有规律的时候，二分查找才可以使用
# 时间复杂度 O(logn)

print(binary_search(list(iter(range(1000000))), 112200))
# 用迭代器没啥用，且浪费时间
```

　　二分查找需要先排序，字符串的比较是通过 Unicode 码比较的

　　二分查找比线性查找效率高

　　‍

# 排序（Sorted）

　　排序：将列表转化为有规律的排序

　　内置排序函数：sort()

## 排序算法的稳定性

　　在原有的序列中，稳定排序算法会让原本有相等键值的记录维持相对次序。也就是如果一个排序算法是稳定的，当有两个相等键值的记录R和S，且在原本的列表中R出现在S之前，在排序过的列表中R也将会出现在S之前。

　　<u>不稳定排序算法可能会在相等的键值中改变记录的相对次序</u>

![image](images/2024/02/16/image-20240216105555-b54ebs7.png)

![排序分类图](images/2024/02/16/排序分类图-20240222093911-5kxl43t.png)

## 冒泡排序Bubble Sort

　　<u>越小的元素会经由交换慢慢浮到顶端</u>

　　冒泡排序的运作如下：

- 比较相邻的元素。如果第一个比第二个大（升序），就交换它们两个
- 对每一对相邻的元素做同样的工作，从开始第一对到结尾的最后一对。做完这步后，最后的元素会是最大的数。
- 针对所有元素重复以上的步骤，除了最后一个。
- 持续每次对越来越少的元素重复以上的步骤，直到没有任何一对数字需要比较为止

![image](images/2024/02/16/image-20240127102352-fft9bbq.png "冒泡排序过程分析")

　　由上可得，对于一个含n个元素的列表，遍历n-1次

　　每次的比较次数如下：

![1、算法 Image[8\]](images/2024/02/16/1、算法%20Image8-20240128132114-042vc9r.jpg)

### 代码实现

```python
def bubble_sort(alist: list):
    """一个冒泡排序"""
    n = len(alist)
    for j in range(0, n-1):
        for i in range(0, n-j-1):
            if alist[i] > alist[i + 1]:
                alist[i], alist[i+1] = alist[i+1], alist[i]
```

　　**时间复杂度：**​**O(n) ~ O(n**<sup>**2**</sup> **)** 

　　稳定性：稳定

### 双向冒泡排序

## 选择排序Selection Sort

　　首先<u>在未排序序列中找到最小(大)元素，存放到排序序列的起始位置</u>，然后，再从剩余未排序元素中继续寻找最小(大)元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排满为止

　　如果某个元素处于正确的最终位置上，则它不会被移动走。

　　选择排序每交换一次，它们中直少有一会移动到最终位置上，因此==对于n个元素，最多进行n-1次交换==

![image](images/2024/02/16/image-20240128150855-kjy9atw.png "选择排序过程分析")

### 代码实现

```python
def select_sort(alist: list):
    """选择排序"""
    n = len(alist)
    for j in range(0, n-1):
        min_index = j
        for i in range(j+1, n):
            if alist[min_index] > alist[i]:
                min_index = i
        alist[j], alist[min_index] = alist[min_index], alist[j]

```

　　**时间复杂度：**​==**O(n^2)**==

　　稳定性：不稳定

## 插入排序Insertion Sort

　　<u>通过构建有序列表，对未排序数据，在已排序序列中从后往前扫描，找到相应位置并且插入</u>。插入排序在实现上，在从后往前扫描过程中，需要反复把已排序元素逐步向后挪为最新元素提供空间。

![image](images/2024/02/16/image-20240128151301-p9syok1.png "插入算法分析")

### 代码实现

```python
def insert_sort(alist: list):
    """插入排序"""
    n = len(alist)
    for j in range(1, n):
        i = j
        while i > 0:
            if alist[i] < alist[i-1]:
                alist[i], alist[i-1] = alist[i-1], alist[i]
                i -= 1
            else:
                break
```

　　**时间复杂度：**​**==O(n)~O(n^2)==**

　　稳定性：稳定

## 希尔排序(Shell Sort)

　　希尔排序（shell sort）是插入排序的一种。也称==缩小增量排序==，是直接插入排序算法的一种更高效的改进版本。希尔算法是非稳定排序算法。希尔排序是<u>把记录按下标的一定增量分组，对每组使用直接插入算法排序；随着增量逐渐减小，每组包含的关键词越来越多，当增量减小到1的时候，整个文件恰好被分成一组，算法便终止。</u>

#### 希尔排序过程

　　将数组列在一个表中并对列分别进行插入排序，重复这过程，不过每次使用更长的列来进行。最后整个表就只有一列了。将数组转换为表是​

![image](images/2024/02/16/image-20240220111527-7qhbvb2.png)

　　为了更好的表达这种算法，其本质任然是使用数组进行排列

![image](images/2024/02/16/image-20240216104454-i877jod.png)

![image](images/2024/02/16/image-20240216104943-4iv3x2o.png)

### 代码实现

```python
def shell_insert(alist):
    """希尔排序"""
    n = len(alist)
    gap = n // 2
    while gap > 0:
        for i in range(gap, n):
            while i > 0:
                if alist[i] < alist[i - gap]:
                    alist[i], alist[i - gap] = alist[i - gap], alist[i]
                    i -= gap
                else:
                    break
        gap //= 2
```

　　时间复杂度：

　　最优时间复杂度：根据步长序列的不同而不同

　　最坏时间复杂度：<span data-type="text" style="background-color: var(--b3-font-background4);">O(n</span><sup>2</sup><span data-type="text" style="background-color: var(--b3-font-background4);">)</span>

　　稳定性：==不稳定==

## 快速排序(Quick Sort)（重点）

　　又称为==划分交换排序==，<u>通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另一部分小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列</u>

　　基于分治的排序

　　步骤为：

　　从数列中挑出一个元素，称为基准

　　重新排序数列，所有元素比基准小的摆放在基准的前面，大的则放在后面

　　递归的把小于基准值元素的子数列和大于基准值元素的子序列排序

　　（难度较高）

　　‍

### 代码实现

　　python

```python
def quick_sort(alist: list, first, last):
    """快速排序"""
    if first >= last:
        return
    mid_value = alist[first]
    low = first
    high = last
    while low < high:
        # high左移
        while low < high and alist[high] >= mid_value:
            high -= 1
        alist[low] = alist[high]

        while low < high and alist[low] < mid_value:
            low += 1
        alist[high] = alist[low]
    # 从循环退出时，high=low
    alist[low] = mid_value

    # 对low左边的列表执行排序
    quick_sort(alist, first, low-1)
    # 对low右边的进行排序
    quick_sort(alist, low + 1, last)


if __name__ == "__main__":
    x1 = [43, 23, 33, 13, 56, 65, 35, 36, 12, 9]
    quick_sort(x1, 0, len(x1)-1)
    print(x1）
```

　　c++

```cpp
#include <iostream>
using namespace std;

int partition(int alist[], int low, int high){
    int pivot = alist[low];
    while (low < high){
        while (low < high && alist[high] >= pivot){
            high--;
        }
        alist[low] = alist[high];
        while (low < high && alist[low] <= pivot){
            low++;
        }
        alist[high] = alist[low];
    }
    alist[low] = pivot;
    return low;
}

void quick_sort(int alist[], int low, int high){
    if (low >= high) {
        return;
    }
    int mid_value = partition(alist, low, high);
    quick_sort(alist, low, mid_value-1);
    quick_sort(alist, mid_value+1, high);
}


int main(){
    int alist[] = {
            43, 23, 33, 13, 56, 65, 35, 36, 12, 9
    };
    int n = sizeof (alist) / sizeof (alist[0]);
    quick_sort(alist, 0, n - 1);
    for (int i = 0; i < n; i++){
        cout << alist[i] << " ";
    }
    cout << endl;
    return 0;
}
```

　　时间复杂度

　　最优时间复杂度：O(nlogn)

　　最坏时间复杂度：O(n<sup>2</sup>)

　　稳定性：不稳定

## 归并排序(Merge Sort)

　　先递归分解数组，在合并数组。

　　将数组分解最小后，然后合并两个有序数组，基本思路是比较两个数组最前面的数，谁小就先取谁，取了之后相应的指针就往后移动一位。然后再比较，直至一个数组为空最后把另一个数组的剩余部分复制过来即可

### 过程分析

![image](images/2024/02/16/image-20240220111402-619ric6.png)

### 代码实现

　　（又不会）

```python
def merge_sort(alist):
    """归并排序"""
    n = len(alist)
    if n <= 1:
        return alist
    mid = n // 2

    # left 采用归并排序后形成的有序的新的列表
    left_li = merge_sort(alist[:mid])
    # right 采用归并排序后形成的新的有序列表
    right_li = merge_sort(alist[mid:])

    # 将两个有序的子序列合并为一个新的整体
    # merge(left, right)
    left_pointer, right_pointer = 0, 0
    result = []

    while left_pointer < len(left_li) and right_pointer < len(right_li):
        if left_li[left_pointer] < right_li[right_pointer]:
            result.append(left_li[left_pointer])
            left_pointer += 1
        else:
            result.append(right_li[right_pointer])
            right_pointer += 1

    result += left_li[left_pointer:]
    result += right_li[right_pointer:]
    return result


if __name__ == "__main__":
    x1 = [43, 23, 33, 13, 56, 65, 35, 36, 12, 9]
    print(merge_sort(x1))
```

## 堆排序（Haep Sort）

　　堆必须是一个完全二叉树

![image](images/2024/02/16/image-20240224100759-9rljked.png)

堆序性

小根堆：每个父节点元素小于子节点元素

大根堆：每个父节点元素大于子节点元素

![image](images/2024/02/16/image-20240224101014-n4kxjzg.png)

　　堆的存储：

　　一般用数组来表示，下标为i的节点的父节点下标为(i-1)/2；其左右子节点分别为(2i+1),(2i-1)

堆排序，利用大（小）顶堆堆顶记录最大（小）值，使得每次从无序中选择最大（小）值

![v2-b7907d351809293c60658b0b87053c66_b](images/2024/02/16/v2-b7907d351809293c60658b0b87053c66_b-20240224104300-yyoyvj8.webp)

### 代码实现

　　c++

```cpp
#include <iostream>
#include <algorithm>
using namespace std;
void max_heapify(int arr[], int start, int end) {
    //建立父节点指标和子节点指标
    int dad = start;
    int son = dad * 2 + 1;
    while (son <= end) { //若子节点指标在范围内才做比较
        if (son + 1 <= end && arr[son] < arr[son + 1]) //先比较两个子节点大小，选择最大的
            son++;
        if (arr[dad] > arr[son]) //如果父节点大于子节点代表调整完毕，直接跳出函数
            return;
        else { //否则交换父子内容再继续子节点和孙节点比较
            swap(arr[dad], arr[son]);
            dad = son;
            son = dad * 2 + 1;
        }
    }
}
void heap_sort(int arr[], int len) {
    //初始化，i从最后一个父节点开始调整
    for (int i = len / 2 - 1; i >= 0; i--)
        max_heapify(arr, i, len - 1);
    //先将第一个元素和已经排好的元素前一位做交换，再从新调整(刚调整的元素之前的元素)，直到排序完毕
    for (int i = len - 1; i > 0; i--) {
        swap(arr[0], arr[i]);
        max_heapify(arr, 0, i - 1);
    }
}
int main() {
    int arr[] = { 3, 5, 3, 0, 8, 6, 1, 5, 8, 6, 2, 4, 9, 4, 7, 0, 1, 8, 9, 7, 3, 1, 2, 5, 9, 7, 4, 0, 2, 6 };
    int len = (int) sizeof(arr) / sizeof(*arr);
    heap_sort(arr, len);
    for (int i = 0; i < len; i++)
        cout << arr[i] << ' ';
    cout << endl;
    return 0;
}
```

　　python

```cpp

def heapify(alist, start, end):
    dad = start
    son = dad * 2 + 1
    while son <= end:
        if son + 1 <= end and alist[son] < alist[son + 1]:
            son += 1
        if alist[dad] > alist[son]:
            return
        else:
            alist[dad], alist[son] = alist[son], alist[dad]
            dad = son
            son = dad * 2 + 1


def heap_sort(alist, length):
    for i in range(length//2-1, -1, -1):
        heapify(alist, i, length-1)
    for i in range(length-1, 0, -1):
        alist[0], alist[i] = alist[i], alist[0]
        heapify(alist, 0, i-1)


if __name__ == "__main__":
    x1 = [43, 23, 33, 13, 56, 65, 35, 36, 12, 9]
    heap_sort(x1, len(x1))
    print(x1)
```

## 计数排序(Counting Sort)

　　一种稳定的线性时间排序算法

　　计数排序使用一个额外的数组C，其中第i个元素是待排序数组A中值等于I的元素的个数

![v2-827d96b8ca3682e8775f4916f22b45ac_b](images/2024/02/16/v2-827d96b8ca3682e8775f4916f22b45ac_b-20240225102446-tgkc9oy.webp)

### 代码实现

　　感觉有点问题，之后再改

```cpp
def counting_sort(alist, max_value):
    bucket_len = max_value + 1
    bucket = [0] * bucket_len
    sorted_index = 0
    for i in range(len(alist)):
        if not bucket[alist[i]]:
            bucket[alist[i]] = 0
        bucket[alist[i]] += 1
    for j in range(bucket_len):
        while bucket[j] > 0:
            alist[sorted_index] = j
            sorted_index += 1
            bucket[j] -= 1
    return alist


if __name__ == "__main__":
    x1 = [43, 23, 33, 13, 56, 65, 35, 36, 12, 9]
    counting_sort(x1, max(x1))
    print(x1)
```

　　时间复杂度：O（n）

　　稳定性：稳定

## 桶排序(Bucket Sort)

　　首先将元素分在不同的桶中，在对每个桶中的元素进行排序

### 代码实现

　　那个主讲讲的有问题，这个我之后改

```cpp
def bucket_sort(alist, n=10, max_number=1000):
    buckets = [[] for _ in range(n)]  # 创建桶
    for var in alist:
        i = min(var // (max_number // n), n - 1)
        buckets[i].append(var)
        for j in range(len(buckets[i])-1, 0, -1):
            if buckets[i][j] < buckets[i][j-1]:
                buckets[i][j], buckets[i][j-1] = buckets[i][j-1], buckets[i][j]
            else:
                break
    sort_alist = []
    for buc in buckets:
        sort_alist.extend(buc)
    return sort_alist


if __name__ == "__main__":
    x1 = [43, 23, 33, 13, 56, 65, 35, 36, 12, 9]
    print(bucket_sort(x1))
```

## 基数排序(Radix Sort)

　　属于分配式排序，通过键值的各个位的值，将要排序的元素分配到某些桶中，待到排序的作用

　　基本思想：

　　将所有待比较数值统一为同样的数位长度，数位较短的前面补0，然后从最低为开始依次进行排序

![36275e6835df49ffb3e60f0cdae96993](images/2024/02/16/36275e6835df49ffb3e60f0cdae96993-20240225212647-nnoeynz.gif)

　　最低有效位优先（LSD）

　　最高有效位优先（*MSD*）

### 代码实现

```cpp
def counting_sort(arr, exp):
    n = len(arr)
    output = [0] * n
    count = [0] * 10

    for i in range(n):
        index = arr[i] // exp
        count[index % 10] += 1

    for i in range(1, 10):
        count[i] += count[i - 1]

    i = n - 1
    while i >= 0:
        index = arr[i] // exp
        output[count[index % 10] - 1] = arr[i]
        count[index % 10] -= 1
        i -= 1

    for i in range(n):
        arr[i] = output[i]


def radix_sort(arr):
    max_element = max(arr)
    exp = 1
    while max_element // exp > 0:
        counting_sort(arr, exp)
        exp *= 10


if __name__ == "__main__":
    x1 = [43, 23, 33, 13, 56, 65, 35, 36, 12, 9]
    radix_sort(x1)
    print(x1)
```

## 双调排序(Bitonic Sort)

　　‍

## 猴子排序(Bogo Sort)

　　赌狗真神

　　代码

```cpp
import random


def is_sorted(data):
    """检查列表是否已经排序"""
    for i in range(len(data) - 1):
        if data[i] > data[i + 1]:
            return False
    return True


def bogo_sort(data):
    """猴子排序"""
    while not is_sorted(data):
        random.shuffle(data)
    return data


if __name__ == "__main__":
    x1 = [35, 36, 12, 9]
    bogo_sort(x1)
    print(x1)
```

# 线性表(List)

　　有序数据项的集合，其中每一个数据项都有==唯一==的前驱和后驱

　　除了第一个没有前驱，最后一个没有后继，新的数据项加入到数据集中时，只会加入到原有的某个数据项之前或之后，具有这种性质的数据集，就称为线性结构

　　不同线性结构的关键区别在于==数据项增减的方式==

　　栈stack，队列queue，双端列表deque，列表list

　　数据结构是指<u>相互之间存在着一种或多种关系的数据元素的集合和该集合中数据元素之间的关系组成</u>

　　数据结构就是设计数据以何种方式组织并存储在计算机中

　　连续存储，顺序存储

　　eg:列表，集合与字典

　　**分类：** 线性结构，树结构，图结构

　　线性结构：数据中的元素存在一对一的相互关系

　　树结构：数据结构中的元素存在一对多的关系

　　图结构：数据结构中的元素存在多对多的相互关系

　　平均时间复杂度是指在一个算法处理一系列不同输入时，其平均运行时间随着输入规模增长的变化趋势。它可以通过对每种可能输入所对应的基本操作次数乘以该输入出现的概率，然后求和的方式来计算。

　　数学公式表示如下：

　　$�(�)=∑�∈���⋅��$**$A$**$($**$n$**$)$**$=$**$I$**$∈$**$S$**$∑P$**$I⋅$**$t$**$I$  

　　其中：

- �**S** 是所有可能的输入规模集合。
- �**I** 是集合 �**S** 中的一个特定输入规模。
- ��**P**I 是输入规模为 �**I** 时对应的概率。
- ��**t**I 是对于输入规模为 �**I** 的情况下，算法所需的基本操作次数。
- ‍

## 列表

　　32位机器上(最大4G)，一个整数占4字节，一个地址占4个地址

　　python中列表存的是内存地址

　　插入和删除对于列表来说都是O(n)的复杂度

　　数组与列表的不同：1.数组元素类型要相同

　　				   2.数组长度固定

### 代码实现

　　pass

## 栈（stack）

一个数据集合，类似与只能在一端进行插入或删除的列表

特点：==后进先出LIFO（last-in, frist-out）==

概念：栈顶，栈底

基本操作：进栈：push

出栈：pop

取栈顶：gettop

### 栈的实现方式

#### 基于数组

1.使用一般的列表结构可以实现栈

进栈：li.append  出栈：li.pop  取栈顶：li[-1]

2.用类的方式

Stack()：创建一个空栈，不包含任何数据项

push(item)：将item加入到栈顶，无返回值

pop()：将栈顶数据项移除，并返回，栈被修改

peek()：查看栈顶数据项，返回栈顶的数据项但不移除，栈不被修改

isEmpty()：返回栈是否为空栈

size()：返回栈中有多少个数据项

‍

```python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, element):
        self.stack.append(element)

    def pop(self):
        return self.stack.pop()

    def get_top(self):
        if len(self.stack) > 0:
            return self.stack[-1]
        else:
            return None


stack = Stack()
stack.push(1)
stack.push(2)
stack.push(3)
print(stack.pop())
```

　　把列表的最开始作为栈顶也可以

　　<u>栈顶在列表首端的时候pop复杂度为O(n)，在尾端时复杂度为O(1)</u>

　　注：<u>pop列表中的最后一个元素的时间复杂度比第一个元素的时间复杂度低</u>

#### 基于链表

　　（有手就行）

### 括号匹配问题

　　给一个字符串，其中包含小括号，中括号，大括号，求该字符串中的括号是否匹配

　　左括号入栈，右括号出栈

```python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, element):
        self.stack.append(element)

    def pop(self):
        return self.stack.pop()

    def get_top(self):
        if len(self.stack) > 0:
            return self.stack[-1]
        else:
            return None

    def is_empty(self):
        return len(self.stack) == 0


def brace_match(s):
    match = {'}': '{', ']': '[', ')': '('}
    stack = Stack()
    for ch in s:
        if ch in {'(', '[', '{'}:
            stack.push(ch)
        else:  # ch in
            if stack.is_empty():
                return False
            elif stack.get_top() == match[ch]:
                stack.pop()
            else:
                return False
    if stack.is_empty():
        return True
    else:
        return False


print(brace_match('[{[]()({}{[[]()]})}]'))
print(brace_match('{[}{]()}'))
```

```python
class Stack:
    def __init__(self):
        self.item = []

    def is_empty(self):
        return self.item == []

    def push(self, item):
        self.item.append(item)

    def pop(self):
        return self.item.pop(-1)

    def peek(self):
        return self.item[-1]

    def size(self):
        return len(self.item)


def par_checker(symbol):
    s = Stack()
    balance = True
    index = 0
    while index < len(symbol) and balance:
        sym = symbol[index]
        index += 1
        indexer = {"}": "{", "]": "[", ")": "("}
        if sym in indexer.values():   # 如果是左括号入栈
            s.push(sym)
        elif sym in indexer.keys():
            if len(s.item) == 0:
                balance = False
            elif s.item[-1] == indexer[sym]:
                s.pop()
            else:
                balance = False
    if balance and s.is_empty():
        return True
    else:
        return False


if __name__ == "__main__":
    print(par_checker(input()))
```

## 队列（Queue）

　　一个数据集合，<u>仅允许在列表的一端进行插入，另一端进行删除</u>

　　插入的一端称为队尾(rear)，插入动作称为进队或入队

　　进行删除的一端称为队头(front)，删除动作称为出队

　　队列的性质：==先进先出（Frist-in,Frist-out）== (进程池？) （感觉像迭代器）

　　（广度优先？）

　　列表pop时，删除第一个元素时，所有下标向前移动一格，时间复杂度较高

### 实现方式

#### 基于数组

　　有手就行

#### 基于链表

　　有手就行

### **实现方式-环形队列**

当队尾指针front == maxsize + 1时，再前进一个位置就自动到0

队首指针前进1：front = (front + 1)  % maxsize

队尾指针前进1：rear = (rear + 1)  % maxsize

对空条件：rear == front

队满条件：(rear + 1) % maxsize == front

```python
class Queue:
    def __init__(self, size=10):
        self.queue = [0 for i in range(size)]
        self.size = size
        self.rear = 0  # 队尾指针
        self.front = 0  # 队首指针

    def push(self, element):
        if not self.is_filled():
            self.rear = (self.rear + 1) % self.size
            self.queue[self.rear] = element
        else:
            raise IndexError("Queue is filled")

    def pop(self):
        if not self.is_empty():
            self.front = (self.front + 1) % self.size
            return self.queue[self.front]
        else:
            raise IndexError("Queue is empty")

    # 判断队空
    def is_empty(self):
        return self.rear == self.front

    def is_filled(self):
        return (self.rear + 1) % self.size == self.front


q = Queue(5)   # 空了一格长度为5只能存4个
for i in range(4):
    q.push(i)
print(q.pop())
q.push("哈哈哈")
```

### 双向队列

　　两端都支持进队和出队操作

　　基本操作：==队首进队，队首出队，队尾进队，队尾出队==

### python队列内置模块

　　使用方法：`from collections import deque`

　　extend()一次性从右端添加多个元素。

　　append()从右端添加一个元素

　　eetendleft()从左端添加多个元素

　　appendleft()从左端添加一个元素

　　pop()从右端移除元素

　　popleft()从左端移除元素

　　rorate(n)旋转移动元素 n为正向右移动，为负向左移动

　　count(x1) 统计列表个数

　　reverse()反转列表

```python
import threading
qel = deque([i for i in range(101)])
x1 = threading.Thread(target=qel.append(1))
x2 = threading.Thread(target=qel.append(2))
x1.start()
x2.start()
print(qel)
# 可以使用多线程同时移除或者添加
```

```python
from collections import deque   # 双向队列
# import queue  # 保证线程安全

q = deque([1, 2, 3, 5, 6], maxlen=3)  # maxlen貌似可以省略
# 队尾指针自带一格,自带队列超出范围后，保留队尾
q.append(1)  # 队尾进队
print(q.popleft())  # 队首出队
print(q)

# 用于双向队列
q.appendleft(1)  # 队首进队
q.pop()   # 队尾出队
print(q)
```

### 迷宫问题

![image](images/2024/02/16/image-20231210104827-hc5b9j7.png "迷宫问题")

#### 栈-深度优先搜索

回溯法

从一个节点开始，任意找下一个能走的点，当找不到能走的点时，退回上一个点寻找是否有其它方向的点

使用栈存储当前路径

不一定是最短路径

```python
maze = [
    [1, 0, 0, 1, 0],
    [1, 1, 0, 0, 0],
    [0, 1, 0, 1, 1],
    [1, 0, 1, 1, 0],
    [0, 0, 0, 1, 1]
]

dirs = [
    lambda x, y: (x + 1, y),
    lambda x, y: (x - 1, y),
    lambda x, y: (x, y + 1),
    lambda x, y: (x, y - 1)
]


def maze_path(x1, y1, x2, y2):
    stack = list()
    stack.append((x1, y1))
    while stack:
        cur_node = stack[-1]
        if cur_node[0] == x2 and cur_node[1] == y2:
            for p in stack:
                print(p)
            return True
        for direction in dirs:
            next_node = direction(cur_node[0], cur_node[1])
            # 判断下一个节点是否越界
            if (
                    0 <= next_node[0] < len(maze) and 
                    0 <= next_node[1] < len(maze[0]) and 
                    maze[next_node[0]][next_node[1]] == 0
            ):   # 没法简化链式比较(不会做)，现在摆烂了，就这样吧……
                stack.append(next_node)
                maze[next_node[0]][next_node[1]] = 2  # 标记为已经走过
                break
        else:
            stack.pop()

    print("没有路")
    return False


maze_path(0, 1, 4, 4)
#  摆烂了。用AI写的
```

#### 队列--广度优先搜索

　　思路：从一个节点开始，寻找所有接下来能继续走的点，继续不断寻找，直到找到出口

　　使用队列存储当前正在考虑的节点

　　一定是最短路径

```python
# 看不懂！
```

# 链表（Linked List ）

　　（数组？）

　　定义：一种线性表，在每一个节点里存放下一个节点的位置信息

![image](images/2024/02/16/image-20240305192845-0ix8crc.png)

　　物理结构很大程度上决定了程序对内存和缓存的使用率

## 单向链表

　　单链表，每个节点包含两个域，一个信息域（元素域）和一个链接域。

　　这个链接指向链表中的下一个节点，而最后一个节点指向一个空值

![image](images/2024/02/16/image-20240105150314-bzvh34b.png)

　　表元素域用来存放具体的数据

　　链接域用来存放下一个节点的位置

　　第一个节点称为头节点，最后一个是尾节点

　　（用递归实现？）

```python
class Node:
    def __init__(self, elem):
        self.elem = elem
        self.next = None


class SingleNode:  # 单链表
    def __init__(self, node=None):
        self.__head = node

    def is_empty(self):
        """判断链表长度是否为空"""
        return self.__head is None

    def length(self):
        """链表长度"""
        # cur游标，用来移动遍历节点
        cur = self.__head
        # count记录数量
        count = 0  # count初始值为1的时候，需要考虑空链表的情况
        while cur is not None:
            count += 1
            cur = cur.next
        return count

    def travel(self):
        """遍历整个链表"""
        cur = self.__head
        while cur is not None:
            print(cur.elem, end=" ")
            cur = cur.next
        print("")

    def add(self, item):
        """链表头部添加元素,头插法"""
        node = Node(item)
        node.next = self.__head
        self.__head = node

    def append(self, item):
        """链表尾部添加,尾插法"""
        node = Node(item)
        if self.is_empty():
            self.__head = node
        else:
            cur = self.__head
            while cur.next is not None:
                cur = cur.next
            cur.next = node

    def insert(self, pos, item):
        """指定位置添加元素
        :param pos 从0开始"""
        if pos <= 0:
            self.add(item)
        elif pos > self.length() - 1:
            self.append(item)
        else:
            pre = self.__head
            count = 0
            while count < pos - 1:
                count += 1
                pre = pre.next
            # 当循环退出后，pre指向pos-1
            node = Node(item)
            node.next = pre.next
            pre.next = node

    def remove(self, item):
        """删除节点,删除具体的数据"""
        cur = self.__head
        pre = None
        while cur is not None:
            if cur.elem == item:
                # 先判断此节点是否为头节点
                if cur == self.__head:
                    self.__head = cur.next
                else:
                    pre.next = cur.next
                break
            else:
                pre = cur
                cur = cur.next

    def search(self, item):
        """查找节点是否存在"""
        cur = self.__head
        while cur is not None:
            if cur.elem == item:
                return True
            else:
                cur = cur.next
        return False


if __name__ == "__main__":
    ll = SingleNode()
    print(ll.is_empty())
    print(ll.length())

    ll.append(1)
    print(ll.is_empty())
    print(ll.length())

    ll.append("你好呀")
    ll.append("of course")
    ll.travel()

    ll.insert(-1, 9)
    ll.travel()
    ll.insert(3, 100)
    ll.travel()
    ll.insert(10, 2000)
    ll.travel()

    ll.remove(9)
    ll.travel()
```

　　第二种写法，上面那个是看视频嫖的，写的看着有些复杂。

　　这个写了一半，就不写了……思路已经get到了，感觉有些问题

```python
# 在相同数据量下，链表比数组占更多的空间（数组是顺序的）


class ListNode(object):
    """构建链表节点"""
    def __init__(self, val):
        self.val = val  # 节点值
        self.next: ListNode | None = None  # 指向下一个节点
        # | 可以用 or 代替


# 初始化链表，初始化各个节点
n0 = ListNode(1)
n1 = ListNode(4)
n2 = ListNode(5)
n3 = ListNode(7)
n4 = ListNode(2)

# 构建节点间的引用
n0.next = n1
n1.next = n2
n2.next = n3
n3.next = n4
# 通常将节点头当作链表的代称，如n1


# 插入节点
def insert(a1, a2):
    """在链表的节点a1后插入a2"""
    a3 = a1.next
    a1.next = a2
    a2.next = a3
  

# 删除节点
def remove(a1):
    """删除当中的某一个节点"""
    if a1.next is None:
        return 
    a2 = a1.next.next
    a1.next = a2
```

　　双向链表和环形链表与之同理，双向链表就是加一个指向前一个的节点，环形链表就是把头节点和尾节点相连，即**尾节点指向头节点**（代码有手就行，就不敲了，基本和之前的一样）

# 哈希表(Hash)

　　（集合的实现方式）

　　定义：一个通过哈希函数来计算数据存储位置的数据结构，通常支持以下操作

　　insert(key, value):插入键值对（key, value）

　　get(key):如果存在键为key的键值则返回其value，否则返回空值

　　delete(key)：删除键为key的键值对

　　用于集合（没有value）和字典（有value）

　　哈希表，又称为**散列表**，是一种<u>线性存储</u>（有点不确定对不对）结构。

　　哈希表由一个**直接寻址**表和一个**哈希函数**组成。

　　哈希函数h(k)将元素关键字k作自变量，返回元素的存储下标。

![image](images/2024/02/16/image-20240109112439-ahnkkpy.png)

　　在哈希表中进行增删查改的时间复杂度都是O(1)

　　‍

### 直接寻址表

　　当关键字的全域U比较小时，直接寻址表是一种简单而有效的方法

![image](images/2024/02/16/image-20240109102518-4u3hqi0.png "直接寻址表")

　　缺点：

- 当域很大时，需要消耗大量内存，很不实际
- 如果域很大而实际出现的key较少，则大量空间被浪费
- 无法处理关键字不是数字的情况

## 开放寻址表

　　构建大小为m的寻指表

　　key为k的元素放到h(k)位置上

　　h(k)是一个函数，其将域U映射到表T[0, 1, ……, m-1]

　　哈希冲突：哈希表的大小是有限的，而要存储的值的数量是无限的，因此对于任何哈希函数，都会出现两个不同元素映射到同一位置上的情况，即<u>可能会出现多个元素对应同一个值</u>

　　eg:h(k)=k%7, h(0) = h(7) = h(14) ……

## 解决哈希冲突

　　哈希表扩容：当哈希表出现冲突时将表扩容，即将原哈希表迁移到新哈希表

　　负载因子：哈希表的元素除以桶数量，用于衡量哈希冲突的严重程度，也常作为哈希表扩容的触发条件。

　　开放寻址表：如果哈希数返回的位置已经有值，则可以向后探查新的位置来存储这个值。

　　线性探查：如果位置i被占用，这探查i+1, i + 2,……

　　二次探查：如果位置i被占用，则探查i+1<sup>2,</sup> i - 1<sup>2</sup>, i + 2 <sup>2</sup>, i - 2<sup>2</sup>,……

　　二度哈希：有n给哈希函数，当使用第一个哈希函数h1发生冲突时，则尝试使用h2,h3……（看不懂）

　　拉链法：哈希表每个位置都连接一个链表，当冲突发生时，冲突的元素将被添加到该位置链表的最后

　　D-J-B哈希函数：（可忽略）

　　（一脸懵逼……）

### 常见哈希函数

　　m是哈希表的长度

　　除法哈希法

　　h(k) = k % m

　　乘法哈希法

　　h(k) = floor(m * (A * key % 1))

　　全域哈希法

　　h<sub>a,b</sub>(k) = ((a * key + b ) mod p) mod m a,b == 1, 2,……p-1

## 基于数组的实现方式

　　就是构建两个列表，让其一一对应，（之前看成集合了，写上注解还是很有必要的，规范），但是这个key的类型不固定

```python
class Pair:
    """键值对"""
    def __init__(self, key: int, var: str):
        self.key = key
        self.var = var


class ArrayHashMap:
    """基于数组实现的哈希表"""

    def __init__(self):
        """构造方法"""
        # 初始化数组，设置有多少个桶
        self.buckets: list[Pair | None] = [None] * 100  # 这里写了一个注解

    def hash_func(self, key: int) -> int:  # 有的时候注解真的非常重要
        """哈希函数"""
        index = key % 100
        return index

    def get(self, key: int) -> str:
        index = self.hash_func(key)
        pair: Pair = self.buckets[index]
        if pair is None:
            return "None"
        return pair.var

    def put(self, key: int, var: str):
        """添加操作"""
        pair = Pair(key, var)
        index = self.hash_func(key)
        self.buckets[index] = pair

    def remove(self, key: int):
        """删除操作"""
        index = self.hash_func(key)
        # 将其转换为None，即代表为删除
        self.buckets[index] = None

    def entry_set(self) -> list[Pair]:
        """获取所有键值对"""
        result: list[Pair] = []
        for pair in self.buckets:
            if pair is not None:
                result.append(pair)
        return result

    def key_set(self) -> list[int]:
        """获取所有键"""
        result = []
        for pair in self.buckets:
            if pair is not None:
                result.append(pair.key)
        return result

    def value_set(self) -> list[str]:
        """获取所有值"""
        result = []
        for pair in self.buckets:
            if pair is not None:
                result.append(pair.var)
        return result

    def print(self):
        """打印哈希表"""
        for pair in self.buckets:
            if pair is not None:
                print(f"{pair.key}->{pair.var}", end=" , ")
```

　　‍

## 链式地址

　　缺点：效率低，空间大

　　简化写法：用动态数组代替链表，负载因子边界设置为2/3

　　‍

## 开放寻址

## 基于链表的代码实现

　　拉链哈希表

　　在拉链法中，将映射到同一个数组下标上的元素，存储到同一个单链表中，哈希表的表头通过指针实现，表体由单链表组成。

　　将插入的数据除以哈希表表长，得到的余数即为数据映射在哈希表中的位置，而数据会保存在该位置后面的单链表中。

```cpp
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None


class HashTable:
    def __init__(self, size=10):
        self.head = [ListNode(0) for _ in range(size)]

    def hash_func(self, key):
        return key % len(self.head)

    # 实现将key值插入到哈希表中
    def insert(self, key):
        node = ListNode(key)  # 创建一个新的保存key的节点
        hash_value = self.hash_func(key)  # 调用hash_func计算key的哈希值
        node.next = self.head[hash_value].next  # 新节点的next指向head_hash后的节点
        self.head[hash_value].next = node  # 将head_hash的next指向新节点

    # 查找数据是否存在在哈希表中
    def search(self, key):
        hash_value = self.hash_func(key)  # 计算key的哈希值
        # 找到hash对应的链表，head_hash,将head指向它的下一个节点
        head = self.head[hash_value].next
        while head is not None:  # 使用head遍历该链表
            if head.val == key:  # 当节点值与key相同时
                return True
            head = head.next
        return False
```

　　‍

# 二叉树(Binary Tree)

## 树

　　树是一种抽象数据类型或是这种数据类型的数据结构，用来模拟具有树状结构性质的数据集合。

　　由n（n>=1）个有限节点组成一个具有层次关系的集合。

　　树具有以下特点：

- 每个节点具有零个或者是多个子节点。
- 没有父节点的节点称为根节点。
- 除了根节点以外，每个子节点可以分为多个不相交子树

### 树的术语

- **节点的度**：一个节点含有的子数个数称为该节点的度
- **树的度**：一棵树中，最大的节点的度称为树的度
- **叶节点或终端节点**：度为零的节点
- **父节点**：若一个节点含有子节点，则这个节点称为其子节点的父节点
- **子节点**：一封节点含有的子数的节点称为该节点的子节点
- **兄弟节点**：具有相同父节点的节点称为兄弟节点
- 节点的层次：从根开始定义起，根为第一层，根的子节点为第二层，以此类推
- **树的高度或深度**：树节点中的最大层次
- **堂兄弟节点**：父节点在同一层的节点互为堂兄弟
- **节点的祖先**：从根到该节点所有分支上的所有节点
- **子孙**：以某节点为根的子树中任意一节点都称为该节点的子孙
- **森林**：由m棵互不相交的树的集合称为森林

### 树的种类

　　**无序树**：树中任意节点的子节点之间没有顺序关系，这种树称为无序树，也称为自由树。

　　**有序树**：树的仁义节点之间有顺序关系

　　**二叉树**：每个节点最多含有两个子树

　　**完全二叉树**：对于一个二叉树，假设其深度为d，除了第d层以外，其它各层的节点数均已达到最大值，且d层所有节点从左向右连续的紧密排列，这样的树称为完全二叉树，其中**满二叉树**的定义是所有叶节点都在底层的完全二叉树

　　**平衡二叉树(AVL树)** ：当且仅当任何节点的两棵子树的高度差不大于1的二叉树

　　排序二叉树：二叉查找树

　　**霍夫曼树(用于信息编码)** ：带权路径最短的二叉树称为哈夫曼树或最优二叉树

　　**B树**：一种对读写操作进行优化的自平衡的二叉查找树，能够保持数据有序，拥有多余两颗子树

　　‍

### 树的存储与表示

　　**顺序存储**：将数据结构存储在固定的**数组**中，在遍历上具有一定的优势，但所占空间比较大，是非主流二叉树

　　**链式存储**：由于节点个数无法掌握，常见树的存储模式都转换为二叉树进行处理，子节点个数最多为2.

## 二叉树

### 二叉树的基本概念

　　二叉树是每个节点最多有两个子树的结构。通常子树被称为“左子树”和“右子树”

### 二叉树的性质（特性）

　　在二叉树的第i层上至多有2<sup>i-1</sup>个节点

　　深度为k的二叉树至多有2<sup>k-1</sup>个节点

　　对于任意一颗二叉树，如果其叶节点数为N0，而度数为2的节点总数为N2，则N0=N2+1

　　n个节点的完全二叉树的深度必定为log<sub>2</sub>(n+1)

　　对于完全二叉树，若从上到下，从左到右编号，则编号为i的起点，其左孩子编号一定为2i，其右孩子编号一定为2i+1；其双亲的编号一定为i/2

　　‍

## 二叉树的表示

```python
class Node:
    def __init__(self, item):
        self.elem = item
        self.l_child = None
        self.r_child = None


class Tree:
    """二叉树"""
    def __init__(self):
        self.root = None

    def add(self, item):
        node = Node(item)
        if self.root is None:
            self.root = node
            return
        queue = [self.root]
        while queue:
            cur_node = queue.pop(0)
            if cur_node.l_child is None:
                cur_node.l_child = node
                return
            else:
                queue.append(cur_node.l_child)
            if cur_node.r_child is None:
                cur_node.r_child = node
                return
            else:
                queue.append(cur_node.r_child)

    def breadth_travel(self):
        """广度遍历"""
        if self.root is None:
            return
        queue = [self.root]
        while queue:
            cur_node = queue.pop(0)
            print(cur_node.elem, end=" ")
            if cur_node.l_child is not None:
                queue.append(cur_node.l_child)
            if cur_node.r_child is not None:
                queue.append(cur_node.r_child)

    def preorder(self, node):
        """先序遍历"""
        if node is None:
            return
        print(node.elem, end=" ")
        self.preorder(node.l_child)
        self.preorder(node.r_child)

    def inorder(self, node):
        """中序遍历"""
        if node is None:
            return
        self.inorder(node.l_child)
        print(node.elem, end=" ")
        self.inorder(node.r_child)

    def postorder(self, node):
        """后序遍历"""
        if node is None:
            return
        self.postorder(node.l_child)
        self.postorder(node.r_child)
        print(node.elem, end=" ")


if __name__ == "__main__":
    tree = Tree()
    for i in range(10):
        tree.add(i)
    tree.breadth_travel()
    print(" ")
    tree.preorder(tree.root)
    print("  ")
    tree.inorder(tree.root)
    print()
    tree.postorder(tree.root)
```

　　‍

### 二叉树的遍历

#### 广度优先遍历（层次遍历）

　　从树的root开始，从上到下，从左到右遍历整个树的节点

```python
        def breadth_travel(self):
        """广度遍历"""
        if self.root is None:
            return
        queue = [self.root]
        while queue:
            cur_node = queue.pop(0)
            print(cur_node.elem, end=" ")
            if cur_node.l_child is not None:
                queue.append(cur_node.l_child)
            if cur_node.r_child is not None:
                queue.append(cur_node.r_child)
```

#### 深度优先遍历（重点掌握）

　　先序遍历：根节点 —> 左子树 —> 右子树

```python
        def preorder(self, node):
        """先序遍历"""
        if node is None:
            return
        print(node.elem, end=" ")
        self.preorder(node.l_child)
        self.preorder(node.r_child)
```

　　中序遍历：左子树 —> 根节点 —> 右子树

```python
    def preorder(self, node):
        """先序遍历"""
        if node is None:
            return
        print(node.elem, end=" ")
        self.inorder(node.l_child)
        self.inorder(node.r_child)
```

　　后序遍历：左子树 —> 右子树 —> 根节点

```python
     def postorder(self, node):
        """后序遍历"""
        if node is None:
            return
        self.postorder(node.l_child)
        self.postorder(node.r_child)
        print(node.elem, end=" ")
```

 ![image](images/2024/02/16/image-20240121110139-570s7yg.png)

# 图(Graph)

## 最小生成树

　　（理解思路，但写不来）

![image](images/2024/02/16/image-20240124125355-xc9l0zv.png)

　　在无向图里面求一棵树（n-1条边，无环，联通所有点），而且这棵树的边权和最小

　　如何花最小的线连接所有的点

### Prim算法(加点法)

　　距离已经找亮的点找最近的点，答案不是唯一的

　　更加适合于==稠密图==（）

![image](images/2024/02/16/image-20240124130314-ggj9t2w.png)

### Kruskal算法(加边法)

　　边的两个端点在不在同一个联通分量里（不一定是直连）

　　更适合和==稀疏图==

![image](images/2024/02/16/image-20240124131045-cd86kkt.png)

　　‍

# 堆（Heap）

# 分治(Divide and Conquer)

# 回溯（Backtracking）

　　暴力搜索算法，一种通过穷举来解决问题的方法

　　回溯与递归相辅相成，有回溯就有递归

　　解决问题：组合问题，切割问题，子集问题，排列问题，棋盘问题

　　理解：抽象为一个树形结构

　　模板：![image](images/2024/02/16/image-20240307110236-5qahqw6.png)

　　自己跟着敲的代码：

```python
def bracktracking(参数):
    if 停止条件:
        收集结果
        return
    for i in (集合的元素集或者是所有子节点的个数):
        处理节点
        递归函数
        回溯操作（撤销处理节点的情况）
    return
```

## 组合问题

　　‍

# 贪心（Greedy Algorithm)

　　‍

# 动态规划(DP)

　　递归，分治，动态规划，贪心，回溯，枚举

## 介绍

　　定义：给定一个问题，将其拆分成一个个子问题，直到子问题可以直接解决，让后将子问题的答案保存起来，以<u>减少重复计算</u>。再根据子问题答案反推，得出原问题解的一种方法，即解决==多阶段决策问题==的过程称为动态规划

　　动态规划是对解最优化问题的一种途径，<u>不是一种特殊算法</u>。由于各种问题的性质不同，确定最优解的条件也不同，因此不存在一种万能的动态规划算法可以解决各类最优化问题

　　动态规划：阶段 ->状态->决策->策略->状态转移方程

　　常见的DP类型：线性模型，区间DP，背包DP，数位DP，状态压缩DP，树状DP

　　常见的DP优化方法：滚动数组优化（空间），矩阵乘法优化（时间），斜率优化，四边形不等式优化，决策单调性优化，数据结构优化

　　阶段和阶段变量：将问题的全过程恰当的分成若干个相互联系的阶段。阶段的划分一般根据时间和空间的自然特征去划分。阶段的划分要便于把问题转换成多阶段决策问题

　　状态和状态变量：通常一个阶段包含若干状态。状态可由变量来描述。

　　决策：在对问题的处理中做出的每种选择性的行动就是决策。即从该阶段的每一个状态出发，通过一次选择性的行动转移至下一阶段的相应状态

　　决策变量：一个实际问题可能需要有多次决策和多个决策点，在每一个阶段的每一个状态中都需要有一次决策，决策也可以用变量来描述，称这种变量为决策变量

　　决策允许集合：在实际问题中，决策变量的取值往往限制在某一个范围内，此范围就称为决策允许集合

　　策略：所有阶段一次排列构成问题的全过程。全过程中各阶段决策变量所组成的有序总体称为策略

　　最优策略：在实际问题中，从决策允许集合中找出最优效果的策略称为最优策略

　　状态转移方程：前一阶段的终点就是后一阶段的起点，对前一阶段的状态做出某种决策，产生后一种阶段的状态，这种关系描述了从I阶段到I+1阶段状态的演变规律，称为状态转移方程

## 性质

　　使用前提：最优化原理，无后效性原则

　　最优化原理：一个问题的最优解只取决于其子问题的最优解

　　无后效性原则：某阶段的状态一旦确定，则此后过程的演变不再受此前各状态及决策的影响

　　对于不能划分阶段的题，不能用动态规划来解

　　不符合最优化原理，不能用动态规划

　　不具备无后效性原则的，不能用动态规划来解

　　动态规划设计方法：

　　正推：从初始状态开始，通过对中间阶段的决策的选择，达到结束状态。称为递推

　　倒推：从结束状态开始，通过对中间阶段的决策的选择，达到开始状态，称为记忆化搜索

## 记忆化搜索

　　实现一个函数，用搜索的方法实现DP的更新，通常用于解决转移顺序不方便人为确定的DP

### [数字三角形](https://lx.lanqiao.cn/problem.page?gpid=T312)

#### 问题描述

![image](images/2024/02/16/image-20240303141527-qivdjhp.png)

　　设f[i][j]表示走到第i行第j列的最大值。

　　正常DP：f[i][j]=max(f[i-1][j], f[i-1][j-1]+a[i][j])

![image](images/2024/02/16/image-20240303142319-r37a96m.png)

## 例题讲解

### [台阶问题](https://lx.lanqiao.cn/problem.page?gpid=T1507)

#### 问题描述

　　　楼梯有N（N\<25）级台阶，上楼时一步可以走一级台阶，也可以走二级或三级台阶。请编写一个递归程序，计算共有多少种不同的走法？

#### 代码

　　**dfs暴力解决**

```python
def dfs(n):
    if n == 1:
        return 1
    elif n == 2:
        return 2
    elif n == 3:
        return 4
    else:
        return dfs(n-1) + dfs(n-2) + dfs(n-3)
```

　　失败的递推，会运行超时

　　**记忆化搜索**

![image](images/2024/02/16/image-20240302184037-wo3emzt.png "过程演示")

```python
a1 = int(input())
num_list = [None] * (a1 + 1)


# 记忆化搜索
def steps(n):
    if num_list[n]:
        return num_list[n]
    if n == 1:
        sum_1 = 1
    elif n == 2:
        sum_1 = 2
    elif n == 3:
        sum_1 = 4
    else:
        sum_1 = steps(n-1)+steps(n-2)+steps(n-3)
    num_list[n] = sum_1
    return sum_1


print(steps(a1))
```

　　（只会让ai帮忙改代码的废物）

　　**递推**

　　递归的过程：只有“归”的过程才是产生答案的过程，“递”的过程是把大问题分解子问题的过程

 ![image](images/2024/02/16/image-20240303131713-bdbqr5a.png)

　　（我自己用python代码敲的直接卡死了，就不发了）

　　记忆化搜索 = 暴力dfs +记录答案

　　递推的公式 = dfs向下递归的公式

　　递推数组的初始值 = 递归的边界

![image](images/2024/02/16/image-20240303133752-9ecg8an.png)

　　‍

　　‍

　　‍
