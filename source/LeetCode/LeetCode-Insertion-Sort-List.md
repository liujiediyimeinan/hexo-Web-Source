title: 'LeetCode: Insertion Sort List'
date: 2015-06-24 00:03:22
---
 ```java
/**
 * Description: Sort a linked list using insertion sort.
 *
 * @author hzhou
 */
 public class InsertionSortList {
     public ListNode insertionSortList(ListNode head) {
         if (head == null || head.next == null) {
             return head;
         }
         ListNode cursor = head;
         ListNode next, pre;
         ListNode preHead = new ListNode(0);
         preHead.next = head;
         while (cursor.next != null) {
             pre = preHead;
             next = cursor.next;
             while (pre.next != null && pre.next != next && pre.next.val <= next.val) {
                 pre = pre.next;
             }
             if (pre.next == next) {
                 cursor = next;
                 continue;
             }
             cursor.next = next.next;
             next.next = pre.next;
             pre.next = next;
         }
         return preHead.next;
     }
 }
```
