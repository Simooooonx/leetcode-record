# Day4 - 链表

## \[24] [Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/description/)

> 说多了都是泪
>
> 不会用虚拟头结点导致的
>
> 绕麻了

### 无虚拟头结点

要先处理头结点处的交换

```java
class Solution {
    public ListNode swapPairs(ListNode head) {
        if (head == null) {
            return null;
        }
        if (head.next == null) {
            return head;
        }
        ListNode beg = head.next;
        ListNode cur = head;
        cur.next = beg.next;
        beg.next = cur;
        ListNode pre = cur;
        while (cur.next != null) { 
            cur = cur.next;
            if (cur.next == null) {
                break;
            }
            ListNode nextNode = cur.next;
            pre.next = nextNode;
            cur.next = nextNode.next;
            nextNode.next = cur;
            pre = cur;
        }
        return beg;
    }
}
```

### 有虚拟头结点

```java
class Solution {
    public ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        ListNode dummy = new ListNode();
        dummy.next = head;
        ListNode pre = dummy;
        ListNode cur = head;
        while (cur != null && cur.next != null) { 
            ListNode temp = cur.next;
            pre.next = temp;
            cur.next = temp.next;
            temp.next = cur;
            pre = cur;
            cur = pre.next;
        }
        return dummy.next;
    }
}
```

## \[19] [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)

**双指针应用**

先让一个指针往后走n格，然后两个指针一起向后遍历

注意要处理 n = size的边界条件，即删掉头结点；



## \[160] [Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/description/)

依然是双指针应用，好用的双指针

这题思路也很重要

两个指针先走完本链表的结点再走另一个链表的结点，直到重合

> leetcode题解
>
> 你变成我，我变成你，我们便相遇了。



## \[142] [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/description/)

重点：环形链表中双指针的交汇情况

