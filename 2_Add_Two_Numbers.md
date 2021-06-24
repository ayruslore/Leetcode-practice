## Question : Add Two Numbers

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list. You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example:**
```
Input : l1 = [2,4,3], l2 = [5,6,4]
Output : [7,0,8]
Explanation : 342 + 465 = 807
```

## Solution :

```python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1, l2):
        carry = 0
        head = result = None
        v = l1.val + l2.val
        if v < 10:
            head = result = ListNode(v)
        else:
            head = result = ListNode(v - 10)
            carry = 1
        l1 = l1.next
        l2 = l2.next
        while l1 != None and l2 != None:
            v = l1.val + l2.val + carry
            if v < 10:
                result.next = ListNode(v)
                carry = 0
            else:
                result.next = ListNode(v - 10)
                carry = 1
            l1 = l1.next
            l2 = l2.next
            result = result.next
        while l1 != None:
            v = l1.val + carry
            if v < 10:
                result.next = ListNode(v)
                carry = 0
            else:
                result.next = ListNode(v - 10)
                carry = 1
            l1 = l1.next
            result = result.next
        while l2 != None:
            v = l2.val + carry
            if v < 10:
                result.next = ListNode(v)
                carry = 0
            else:
                result.next = ListNode(v - 10)
                carry = 1
            l2 = l2.next
            result = result.next
        if carry == 1:
            result.next = ListNode(1)
        return head
```