## 回文链表
请判断一个链表是否为回文链表。

示例 1:
```
输入: 1->2
输出: false
```
示例 2:
```
输入: 1->2->2->1
输出: true
```
进阶：
你能否用 O(n) 时间复杂度和 O(1) 空间复杂度解决此题？

### 代码
``` js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {boolean}
 */
var isPalindrome = function(head) {
  if (!head || !head.next) return true;
  let slow = head;
  let fast = head;
  while (fast.next && fast.next.next) {
    slow = slow.next;
    fast = fast.next.next;
  }
  let last = slow.next;
  let pre = head;
  while(last.next) {
    let tmp = last.next;
    last.next = tmp.next;
    tmp.next = slow.next;
    slow.next = tmp
  }
  while (slow.next) {
    slow = slow.next;
    if(pre.val !== slow.val) {
      return false;
    }
    pre = pre.next;
  }
  return true;
};
```