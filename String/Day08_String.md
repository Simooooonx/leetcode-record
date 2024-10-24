# Day08_String

## \[344] [Reverse String](https://leetcode.com/problems/reverse-string/description/)

> You must do this by modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) with `O(1)` extra memory.

```java
class Solution {
    public void reverseString(char[] s) {
        int i = 0, j = s.length - 1;
        while (i < j) { 
            char temp = s[i];
            s[i] = s[j];
            s[j] = temp;
            i++;
            j--;
        }
    }
}
```



## \[541]  [Reverse String II](https://leetcode.com/problems/reverse-string-ii/description/)

344分段，注意i的增加幅度

```java
class Solution {
    public String reverseStr(String s, int k) {
        char[] res = s.toCharArray();
        for (int i = 0; 2 * i <= s.length(); i = i + k) {
            int p = 2 * i, q = Math.min(s.length() - 1, 2 * i + k - 1);
            while (p < q) { 
                char temp = res[p];
                res[p] = res[q];
                res[q] = temp;
                p++;
                q--;
            }
        }
        return String.valueOf(res);
    }
}
```



## [替换数字](https://kamacoder.com/problempage.php?pid=1064)

Stringbuffer转string

```java
import java.util.*;

public class Main {
    public static void main(String[] args){
        Scanner in = new Scanner(System.in);
        String s = in.nextLine();
        StringBuffer res = new StringBuffer();
        for (int i = 0; i < s.length(); i++){
            if (Character.isDigit(s.charAt(i))) {
                res.append("number");
            } else {
                res.append(s.charAt(i));
            }
        }
        System.out.println(res);
    }
}
```



