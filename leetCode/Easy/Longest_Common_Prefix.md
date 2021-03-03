
## Longest Common Prefix

<hr/>

### :heavy_check_mark: 내가 푼 답안

```javascript
/**
 * @param {string[]} strs
 * @return {string}
 */
const longestCommonPrefix = function(strs) {
    if(strs.length == 1 ){
        return strs[0];
    }
    
    if(strs.length == 0 || (strs && strs[0].split('') == "")){
        return "";
    }
    
    for(let i=1 ; i <= strs[0].length ; i++){
        
        const prefix = strs[0].split('',i).join('');
        
        for(let item of strs){
              const check = item.startsWith(prefix); 

            if(!check){
                return i==1 ? "" : prefix.substring(0,prefix.length-1);   
            }          
        }
    }
    return strs[0];
};
```
돌릴때마다 조건이 걸려서 if문을 걸어서 빠져나갔는데,, 지저분하다,,


<hr/>

### :heavy_check_mark: 참고하면 좋은 다른 답안 

Thanks for https://leetcode.com/problems/longest-common-prefix/discuss/6983/Js-higher-order-function-solution-with-concise-and-easy-to-understand-code  

```javascript
var longestCommonPrefix = function(strs) {
    'use strict';
    if (strs === undefined || strs.length === 0) { return ''; }
    
    return strs.reduce((prev, next) => {
        let i = 0;
        while (prev[i] && next[i] && prev[i] === next[i]) i++;
        return prev.slice(0, i);
    });
};
```

reduce함수를 이용한 답안이다.  
```prev[i]``` 이렇게 사용하면 split을 사용안해도 string이 나뉘는것을 처음알았다.  
while문 조건을 통해 내 답안  ```(strs && strs[0].split('') == "")```와 ```strs.length == 1 ```을 안써도 되는것이 좋았다.  
마지막 파싱을 할때 ```refix.length-1```..말고 ```i```를 쓰면 됐었다. 

<hr/>

### :heavy_check_mark: 참고하면 좋은 다른 답안2

Thanks for https://leetcode.com/problems/longest-common-prefix/discuss/801411/JavaScript-Clean-Solution  

```javascript
var longestCommonPrefix = function(strs) {
    if(!strs.length) return '';
    
    for(let i = 0; i < strs[0].length; i++) {
        for(let s of strs) {
            if(s[i] !== strs[0][i]) return s.slice(0, i);
        }
    }
    return strs[0];
};
```

```if(!strs.length) return '';``` 0이 fasle니까 ```!str.length```를 통해 ```strs === undefined || strs.length === 0```을 줄여쓰는것이 좋았다.  
함수 사용없이 이중for문이 깔끔한 답안이다.  


<br/>

