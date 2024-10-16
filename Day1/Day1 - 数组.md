# Day1 - 数组

## 数组理论基础
> 注意在每次数组取值时防止溢出，如添加判断约束等

## 二分查找

### [704] Binary Search

> 整数除法 - > 向下取整
> 其他取整方式 - > 
> 边界条件 - 
> 开闭范围 - > 影响 - > 判断逻辑
1. 闭区间
   1. 循环条件 while(left <= right)
   2. right = mid - 1 ，left = mid + 1 
2. 左闭右开区间
   1. 循环条件 while(left < right)
   2. right = mid，left = mid + 1
   3. right的初始值为 nums.length
3. **middle的计算方式（防止溢出）**：

   ```java
   int middle = left + ((right - left) / 2);
   //或者
   int middle = left + ((right - left) >> 1);
   ```

### [34] Find First and Last Position of Element in Sorted Array

> 注意退出条件的变化
```java
            if (nums[lo] == nums[hi]) {
                begins = -1;
                ends = -1;
                break;
            }
```

> 下一个边界的取值 - 若用闭区间时，仍然是除去所有与当前mid值相同的值。
> lo < hi防止溢出
> 也可以直接用二分查找，不调整取值变化
```java
            if (nums[mid] < target) {
                lo = mid + 1;
                while (nums[lo] == nums[mid] && lo < hi ) { 
                    lo ++;
                }
            }
            if (nums[mid] > target) {
                hi = mid - 1;
                while (nums[hi] == nums[mid] && hi > lo ) { 
                    hi --;
                }
            }
```

### [35] Search Insert Position
​
```java
     // 分别处理如下四种情况
     // 目标值在数组所有元素之前  [0, -1]
     // 目标值等于数组中某一个元素  return middle;
     // 目标值插入数组中的位置 [left, right]，return right + 1
     // 目标值在数组所有元素之后的情况 [left, right]， 因为是右闭区间，所以 return right + 1
            if (lo == hi) {
                res = (nums[mid] < target)? mid + 1: mid;
                break;
            }
```



## 移除元素

### [27] Remove Element

两种方法，看题目对输出数组的要求
一种像本题之中的要求或无要求，就用双指针对数组进行扫描后交换
另一种要求其他数字仍然保持原序，维护一个target出现的次数k，将非target复制到k个位置之前
注意双指针在指针变化时防止数组溢出



## 有序数组的平方

### [977] Squares of a Sorted Array

双指针，新建一个与原数组大小相同的数组并倒序向内填绝对值较大的数的平方