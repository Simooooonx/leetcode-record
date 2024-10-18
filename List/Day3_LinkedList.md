# Day3 - 链表

> 数组已经完结了，这两天抽空做一下整理

## [链表理论基础](https://programmercarl.com/链表理论基础.html)





## \[203] [Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/description/)

> 注意链表的输入输出方式和结点的结构
>
> 注意结点为空时 node.next等会报错，所以每次循环要注意判空
>
> 如果头节点需要删除怎么操作，或者说，**头结点如何加入循环** - > 创建一个虚拟头结点
>
> 本题最关键是要理解 **虚拟头结点**的使用技巧，这个对链表题目很重要。

那么因为单链表的特殊性，只能指向下一个节点，如果删除的是头结点又该怎么办呢？这里就涉及如下链表操作的两种方式：

- **直接使用原来的链表来进行删除操作。**
- **设置一个虚拟头结点在进行删除操作。**

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
public ListNode removeElements(ListNode head, int val) {
    // 设置一个虚拟的头结点
    ListNode dummy = new ListNode();
    dummy.next = head;
    ListNode cur = dummy;
    while (cur.next != null) {
      //直接判断next，就不用记录pre
        if (cur.next.val == val) {
            cur.next = cur.next.next;
        } else {
            cur = cur.next;        
        }
    }
    return dummy.next;
}
```

## \[707] [Design Linked List](https://leetcode.com/problems/design-linked-list/description/)

维护一个有头节点的链表

可用单链表/双向链表实现



## \[206] [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/description/)

1. 创建一个虚拟头结点；
2. 指针cur指向头结点；
3. 将cur的下一个结点temp插入虚拟头结点和虚拟头结点的下一个结点之间；
4. temp的下一个结点赋值给cur.next;
5. 循环直至cur的下一个结点为null

