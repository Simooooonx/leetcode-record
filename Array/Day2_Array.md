# Day2 - 数组

## \[209] [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/description/)

循环问题搞了好久
确定循环结束后指针的指向
记录一下循环判断对指针的影响问题

> 注意子串长度 = 尾位置 - 首位置 + 1
```
class Solution {
    public static int minSubArrayLen(int target, int[] nums) {
        int lo = 0, hi = 0;
        int sum = 0;
        int min_len = Integer.MAX_VALUE;
        //每次循环后i指向下一个数
        for (int i = hi; i < nums.length && sum < target; i++, hi ++) {
            sum += nums[i];
            //System.out.println(sum);
        }
        //所有和比target小
        if (hi == nums.length && sum < target) {
            return 0;
        }
        min_len = hi;
        //每次循环后hi指向下一个数
        //要处理当前尾数,可能存在当前尾数大于前几个数之和的情况-> eg 11 12345
        for (int i = hi - 1; i < nums.length; i++) {
            //System.out.println(sum);
            //当处理当前数时,不操作sum
            sum = i == hi - 1? sum: sum + nums[i];
            //每次循环后lo指向当前数
            //因为这里判断的是sum - nums[j],对当前指向的数做判断
            //i是当前尾指针
            for (int j = lo; j <= i && sum - nums[j] >= target; j++, lo++) {
                sum -= nums[j];
            }
            //所以要在这里加一
            min_len = Math.min(i - lo + 1, min_len);
        }
        return min_len;
    }
}
```

## \[904] [Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/description/)

> 滑动窗口，但是需要改进内存使用率
> - 91/91 cases passed (27 ms)
> - Your runtime beats 87.13 % of java submissions
> - Your memory usage beats 5.91 % of java submissions (57.3 MB)



## \[76] [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/description/)

> 二刷，也是滑动窗口
> 滑动窗口，注意扩张和收缩，使得窗口遍历一次数组之后就能找到答案

维护两个map存储需要的字符数量和已有字符数量


## \[59] [Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/description/)

流程控制，注意一下对边界调整的时机

方法一、用判断控制位置变化

> 用top、left、buttom、right记录当前没有填充的最外层的边
> 写的时候有点绕

方法二、用循环控制

```java
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] nums = new int[n][n];
        int startX = 0, startY = 0;  // 每一圈的起始点
        int offset = 1;
        int count = 1;  // 矩阵中需要填写的数字
        int loop = 1; // 记录当前的圈数
        int i, j; // j 代表列, i 代表行;
        while (loop <= n / 2) {
            // 顶部
            // 左闭右开，所以判断循环结束时， j 不能等于 n - offset
            for (j = startY; j < n - offset; j++) {
                nums[startX][j] = count++;
            }
            // 右列
            // 左闭右开，所以判断循环结束时， i 不能等于 n - offset
            for (i = startX; i < n - offset; i++) {
                nums[i][j] = count++;
            }
            // 底部
            // 左闭右开，所以判断循环结束时， j != startY
            for (; j > startY; j--) {
                nums[i][j] = count++;
            }
            // 左列
            // 左闭右开，所以判断循环结束时， i != startX
            for (; i > startX; i--) {
                nums[i][j] = count++;
            }
            startX++;
            startY++;
            offset++;
            loop++;
        }
        if (n % 2 == 1) { // n 为奇数时，单独处理矩阵中心的值
            nums[startX][startY] = count;
        }
        return nums;
    }
}

```



## [区间和](https://www.programmercarl.com/kamacoder/0058.区间和.html)

给定一个整数数组 Array，请计算该数组在每个指定区间内元素的总和。

> 数组 上常用的解题技巧：前缀和
> **前缀和 在涉及计算区间和的问题时非常有用**！
> 用数组记录每个位置及之前的所有数之和



## [开发商购买土地](https://kamacoder.com/problempage.php?pid=1044)

在一个城市区域内，被划分成了n * m个连续的区块，每个区块都拥有不同的权值，代表着其土地价值。目前，有两家开发公司，A 公司和 B 公司，希望购买这个城市区域的土地。 
现在，需要将这个城市区域的所有区块分配给 A 公司和 B 公司。
然而，由于城市规划的限制，只允许将区域按横向或纵向划分成两个子区域，而且每个子区域都必须包含一个或多个区块。 为了确保公平竞争，你需要找到一种分配方式，使得 A 公司和 B 公司各自的子区域内的土地总价值之差最小。 
注意：区块不可再分。

> 注意acm模式提交时别有多余的控制台打印
