# 两两交换链表中的节点
给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。

### 示例:
给定 1->2->3->4, 你应该返回 2->1->4->3.
### 说明:

1:你的算法只能使用常数的额外空间</br>
2:你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

# code

    /**
    * Definition for singly-linked list.
    * function ListNode(val) {
    *     this.val = val;
    *     this.next = null;
    * }
    */
    /**
    * @param {ListNode} head
    * @return {ListNode}
    */
    var swapPairs = function(head) {
        if(!head){
            return head;
        }
        var first = head,
            ji_index = head,
            move = head;
        var first_lock = 0;
        // 只有两个 
        if(head.next && !head.next.next){
                var tt = head.next;
                tt.next = ji_index;
                ji_index.next = null;
                first = tt;
                return first;
        }
        var tt = null,
            tt2 = null;
        
        while(1){
            if((move.next && move.next.next) ){
                // 交换 
                if(!first_lock){
                    first_lock = true;
                    tt = ji_index.next;
                    move = ji_index;
                    ji_index.next = ji_index.next.next;
                    tt.next = ji_index;
                    ji_index = tt;
                    first = tt;
                }else{
                    tt = move.next; // 3   3-->
                    tt2 = move.next.next; // 4 
                    tt.next = tt2.next; // 3连5
                    tt2.next = tt; // 4连3 
                    move.next = tt2;
                    move= tt;
                    
                }
                
            }else{
                break;
            }
            
        }
        return first;
    };

### 考察点 
基本的链表操作 , 每次跟踪被移动的项即可.