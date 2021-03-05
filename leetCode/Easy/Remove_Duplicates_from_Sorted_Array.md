## Remove Duplicates from Sorted Array

<hr/>

### :heavy_check_mark: 내가 푼 답안

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
const removeDuplicates = function(nums) {
    for (i = 0; i < nums.length; i++){
        if(nums[i] === nums[i+1]){
            nums.splice(i, 1);
            i--;
        }
    }
    
    return nums.length;
}
```
splice를 해주고 ```i--;```를 생각못해서 고생했다.  
잘라주면 index도 바뀌는데 생각을 못했다..  

<hr/>

### :heavy_check_mark: 참고하면 좋은 다른 답안 

Thanks for = https://leetcode.com/problems/merge-two-sorted-lists/discuss/275807/clean-and-fast-javascript

```javascript
var removeDuplicates = function(nums) {
    let i = 0;
    for (let j = 0; j < nums.length; j++) {
        if (nums[j] != nums[i]) 
            nums[++i] = nums[j];
    }
    return ++i;
};
```
내 답안은 동일한 숫자가 올때이고 이건 다른숫자가 올때의 경우다.  



<br/>