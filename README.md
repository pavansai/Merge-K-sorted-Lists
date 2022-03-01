# Merge-K-sorted-Lists



class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        if(lists == null || lists.length == 0) return null;
        return mergeLists(lists, 0, lists.length-1);
    }
    private ListNode mergeLists(ListNode[] list, int start, int end){
        if(start == end) return list[start];
        int mid = start + (end-start) / 2; [Same as int mid = (start + end) / 2];
        ListNode left = mergeLists(list, start, mid);
        ListNode right = mergeLists(list, mid+1, end);
        return merge(left, right);
    }
    private ListNode merge(ListNode l1, ListNode l2){
        ListNode result = new ListNode(-1);
        ListNode current = result;
        while(l1!=null || l2!=null){
            if(l1 == null){
               current.next = l2;
                l2=l2.next;
            }else if(l2 == null){
                current.next = l1;
                l1 = l1.next;
            } else if(l1.val < l2.val){
                current.next = l1;
                l1 = l1.next;
            }else{
                current.next = l2;
                l2=l2.next;
            }
            current = current.next;
        }
        return result.next;
    }
}
