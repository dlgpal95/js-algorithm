
## Two Sum

<hr/>

### :heavy_check_mark: 내가 푼 답안

#### arr.indexOf(searchValue, fromIndex) : index 찾기
- searchValue : 찾으려는 문자열
- fromIndex : 문자열에서 찾기 시작하는 위치를 나타내는 인덱스 값

<br/>

#### arr.includes(searchValue, fromIndex) : 포함여부 확인
- searchValue : 찾으려는 문자열
- fromIndex : 문자열에서 찾기 시작하는 위치를 나타내는 인덱스 값

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
const twoSum = function(nums, target) {
    
    const exaNum = [];
    
    nums.forEach((item,index,arr) => {
        
        const isNum = target - item;

        if(arr.includes(isNum,index+1)){
             exaNum.push(index);
             exaNum.push(arr.indexOf(isNum,index+1));
        }
    });
    
    return exaNum;
};

```
<hr/>

### :heavy_check_mark: 더 빠른 답안 

#### 해쉬테이블 이용

Thanks for https://leetcode.com/problems/two-sum/discuss/182680/JavaScript-Beats-86

```javascript
var twoSum = function(nums, target) {
    if (nums.length === 2) return [0, 1];
    const len = nums.length;
    let map = {};
    for(let i = 0; i < len; i++) {
        let n = target - nums[i];
        let find = map[n];
        if(find !== undefined) return [find, i];
        else map[nums[i]] = i;
    }
};
```

무조건 값이 있으니 length가 2면 바로 return [0,1].. 생각치도못했다. <br/>
includes 사용할때 ```[-2,-3,-4,-6], -8``` 같은 경우 -4에 걸리고 말았는데... fromIndex를 사용해서 겨우 풀었다. <br/>
근데 해쉬테이블로 하면 그런문제도 필요없었다..<br/>
중복확인이 쉬운 해쉬테이블을 이용하자
<br/>