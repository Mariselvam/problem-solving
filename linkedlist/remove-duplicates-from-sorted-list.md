# Remove Duplicates from Sorted List

### Problem Statement:

Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

### Approach1 :

    Use Sentinal node approach + Two pointers

```
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
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode newHead = new ListNode(-101);
        newHead.next = head;
        ListNode p1 = newHead;
        ListNode p2 = head;

        while(p2 != null) {
            if(p1.val == p2.val) {
                while(p2 != null && p1.val == p2.val) {
                    p2 = p2.next;
                }
                p1.next = p2;
                p1 = p1.next;
                if(p2 != null) {
                    p2 = p2.next;
                }
            }else {
                p1 = p1.next;
                p2 = p2.next;
            }
        }

        return newHead.next;
    }
}
```

### Approach2 :

Simple and efficient single pointer apporach

```
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
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
       ListNode curr = head;
       while(curr != null && curr.next != null) {
           if(curr.val == curr.next.val) {
               curr.next = curr.next.next;
           }else {
               curr = curr.next;
           }
       }
       return head;
    }
}
```

