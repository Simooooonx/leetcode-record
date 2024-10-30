# Day_09 String

## \[151] [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/description/)

别用String != null 比较 ！！！

-> !strings[k].isEmpty()

去除首尾空格 s.trim();

```java
class Solution {
    public String reverseWords(String s) {
        s = s.trim();
        //s = s.replace(" ", ",");
        StringBuilder res = new StringBuilder();
        String[] strings = s.split(" ");
        int i = 0, j = strings.length - 1;
        while (i < j) {
            while (strings[i] == null && i < j) {
                i++;
            }
            while (strings[j] == null && i < j) {
                i--;
            }
            String temp = strings[i];
            strings[i] = strings[j];
            strings[j] = temp;
            i++;
            j--;
        }
        //StringBuilder res = new StringBuilder();
        int k = 0;
        while (k < strings.length) {
            if (!strings[k].isEmpty() && !" ".equals(strings[k])) {
                res.append(strings[k]);
                res.append(" ");
            }
            k++;
        }
        return res.toString().trim();
    }
}
```



## [右旋字符串](https://kamacoder.com/problempage.php?pid=1065)

> 字符串的右旋转操作是把字符串尾部的若干个字符转移到字符串的前面。给定一个字符串 s 和一个正整数 k，请编写一个函数，将字符串中的后面 k 个字符移到字符串的前面，实现字符串的右旋转操作。 例如，对于输入字符串 "abcdefg" 和整数 2，函数应该将其转换为 "fgabcde"。

s.substring(); 没有大写

```
import java.util.*;

public class Main {
    public static void main (String[] args) {
        /* code */
        Scanner in = new Scanner(System.in);
        int num = in.nextInt();
        in.nextLine();
        String s = in.nextLine();
        StringBuilder res = new StringBuilder();
        res.append(s.substring(s.length() - num, s.length()));
        res.append(s.substring(0, s.length() - num));
        System.out.println(res.toString());
    }
}
```



## \[28] [Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)





## [459] [Repeated Substring Pattern](https://leetcode.com/problems/repeated-substring-pattern/description/)

> kmp的应用



## [194] [Transpose File](https://leetcode.com/problems/transpose-file/description/)

偶然看到，结合输入输出复习

## 字符串总结

还差经典字典序