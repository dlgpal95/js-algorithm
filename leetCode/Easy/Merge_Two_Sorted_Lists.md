## Merge Two Sorted Lists

<hr/>

### :heavy_check_mark: 내가 푼 답안

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
const mergeTwoLists = function(l1, l2) {
    let mergedlist = new ListNode;
    let change = mergedlist;
    
    while(l1 != null && l2 != null){
        if(l1.val >= l2.val){
            change.next = l2;
            l2 = l2.next;
        }else{
            change.next = l1;
            l1 = l1.next;
        }           
        change = change.next;        
    }
    
    if(l1 == null){
        change.next = l2;
    }
    if(l2 == null){
        change.next = l1;
    }
    
    return mergedlist.next;
};
```
linked list가 익숙하지 않아서 다른 답안은 참고해서 짰다.  
다음에는 처음부터 안보고 짜봐야겠다.  
```    let mergedlist = new ListNode; let change = mergedlist;``` 을 하는 이유는 .next값을 유지하기 위해서(?)인것 같다.  
마지막 null 체크를 ```crt.next = l1 || l2;```로 줄이면 좋을 것 같다.  

<hr/>


### :heavy_check_mark: 참고하면 좋은 다른 답안 

Thanks for = https://leetcode.com/problems/merge-two-sorted-lists/discuss/275807/clean-and-fast-javascript

```javascript
var mergeTwoLists = function(l1, l2) {
    if(!l1 || !l2) return l1 || l2
    if(l1.val < l2.val){
        l1.next = mergeTwoLists(l1.next, l2)
        return l1
    }
    l2.next = mergeTwoLists(l1, l2.next)
    return l2
};
```
재귀함수를 이용한 코드이다.  
비교하여 작은값을 return 하여 반복하는 코드이다.  good.  


<br/>