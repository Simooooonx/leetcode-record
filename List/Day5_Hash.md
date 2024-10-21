# Day4_哈希表

今天的提交runtime都好慢，学学答案的方法

## **哈希表理论基础** 





## \[242] [Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)

> 重点：
> 用数组记录字符的方法
> 字符ascii相对数值的计算
> ```java
> s.charAt(i) - 'a'
> ```

本题代码
```java
/**
 * 242. 有效的字母异位词 字典解法
 * 时间复杂度O(m+n) 空间复杂度O(1)
 */
class Solution {
    public boolean isAnagram(String s, String t) {
        int[] record = new int[26];

        for (int i = 0; i < s.length(); i++) {
            record[s.charAt(i) - 'a']++;     // 并不需要记住字符a的ASCII，只要求出一个相对数值就可以了
        }

        for (int i = 0; i < t.length(); i++) {
            record[t.charAt(i) - 'a']--;
        }
        
        for (int count: record) {
            if (count != 0) {               // record数组如果有的元素不为零0，说明字符串s和t 一定是谁多了字符或者谁少了字符。
                return false;
            }
        }
        return true;                        // record数组所有元素都为零0，说明字符串s和t是字母异位词
    }
```

### 相关问题

\[49] [Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)



\[438] [Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/description/)



\[383] [Ransom Note](https://leetcode.com/problems/ransom-note/description/)



## \[349] [Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/description/)

> 一个集合类专为基本类型数组的方法
>
> ```java
> PriorityQueue<Integer> pq = new PriorityQueue<>(Arrays.asList(1, 2, 5));
> 
> int[] arr = pq.stream().mapToInt(Integer::intValue).toArray();
> 
> System.out.println(Arrays.toString(arr)); // [1, 2, 5]
> ```



### 相关问题

\[350] [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/description/)



## \[202] [Happy Number](https://leetcode.com/problems/happy-number/description/)

> 获取各位数字
>
> ```java
>         while (n > 0) {
>             int temp = n % 10;
>             res += temp * temp;
>             n = n / 10;
>         }
> ```



## \[1] [Two Sum](https://leetcode.com/problems/two-sum/description/)

做过了，记录一下方法

对于每个检索到的数字，在map中查找与其匹配的尚未被匹配的数字及其坐标
