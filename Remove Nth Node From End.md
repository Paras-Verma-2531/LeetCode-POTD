# March-3
## 19. Remove Nth Node From End
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
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if(head==null||head.next==null)return null;
        ListNode temp=head,slow=head;
        while(n--!=0)temp=temp.next;
        if(temp==null)return head.next;
        while(temp.next!=null)
        {
            slow=slow.next;
            temp=temp.next;
        }
        slow.next=slow.next.next;
        return head;
    }
}
