# Day7_哈希表

## \[454] [4Sum II](https://leetcode.com/problems/4sum-ii/description/)

使用一个Map记录a+b之中任意两数之和和出现的次数

计算c+d之中任意两数之和，查找Map中是否有其相反数

时间复杂度 O(2n^2)



## \[383] [Ransom Note](https://leetcode.com/problems/ransom-note/description/)

使用一个Map记录需要组成的string的字符和出现次数

遍历magazine查看是否有足够次数的各字符出现



## \[15] [3Sum](https://leetcode.com/problems/3sum/description/)

>  二刷

排序数组

取第一个数nums[k], 当nums[k] > 0时退出，从k后第一个数开始取第二个数nums[i]，从倒数第一个数开始取第三个数nums[j]，在指针相遇之前，计算三数之和，若<0 i++, 若>0 j--；

k从0到n - 1遍历，当nums[k] = nums[k-1]时跳过本次循环



## \[18] [4Sum](https://leetcode.com/problems/4sum/description/)

> 二刷

与15相似，将k变为前两个加数之和



## 总结

1. 双指针法

   双指针法将时间复杂度：O(n^2)的解法优化为 O(n)的解法。也就是降一个数量级，题目如下：

   - [27.移除元素(opens new window)](https://programmercarl.com/0027.移除元素.html)
   - [15.三数之和(opens new window)](https://programmercarl.com/0015.三数之和.html)
   - [18.四数之和(opens new window)](https://programmercarl.com/0018.四数之和.html)

   链表相关双指针题目：

   - [206.反转链表(opens new window)](https://programmercarl.com/0206.翻转链表.html)
   - [19.删除链表的倒数第N个节点(opens new window)](https://programmercarl.com/0019.删除链表的倒数第N个节点.html)
   - [面试题 02.07. 链表相交(opens new window)](https://programmercarl.com/面试题02.07.链表相交.html)
   - [142题.环形链表II(opens new window)](https://programmercarl.com/0142.环形链表II.html)

2. 哈希表总结