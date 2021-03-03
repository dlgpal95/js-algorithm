
## Valid Parentheses

<hr/>

### :heavy_check_mark: 내가 푼 답안

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
const isValid = function(s) {
    
    if(!s.length || s.length==1){
        return false;
    }
    
    const setBrak = new Map();
    setBrak.set('(',')');
    setBrak.set('[',']');
    setBrak.set('{','}');
    
    const arr = [];
    
    for(let i of s.split('')){
        
       if(setBrak.get(i)){
            arr.push(i);
        }else{
            if(setBrak.get(arr.pop()) != i){
                 return false;
            }
        }      
    }
    return arr.length != 0 ? false :true;
};
```
Map에 각 세트들을 넣고 for문을 돌려서 Map의 key값이면 새로운 arr에 넣어두고  
key값이 아니면 arr에서 pop()을 이용해 최근에 넣었던것을 꺼내서 비교해줬다.  
마지막에 arr의 남아있는게 있으면 false로 return해줬다.  

<hr/>

### :heavy_check_mark: 참고하면 좋은 다른 답안 

Thanks for https://leetcode.com/problems/valid-parentheses/discuss/469626/JavaScript-48-ms-faster-than-96.58

```javascript
var isValid = function(s) {   
    const stack = [];
    
    for (let i = 0 ; i < s.length ; i++) {
        let c = s.charAt(i);
        switch(c) {
            case '(': stack.push(')');
                break;
            case '[': stack.push(']');
                break;
            case '{': stack.push('}');
                break;
            default:
                if (c !== stack.pop()) {
                    return false;
                }
        }
    }
    
    return stack.length === 0;
};
```
내 답안이랑 방식은 비슷한데 stack을 이용했다.  
switch문을 이용하여 map대신 경우의 수를 나눠서 짠 코드이다. 깔끔한 것 같다.  
내 답안은  ```arr.length != 0 ? false :true;``` .. 어차피 결과는 T/F 인데 삼항연산자를 바보같이 썼다.  
위에 답안처럼 쓰는게 좋을 것 같다.  


<hr/>

### :heavy_check_mark: 참고하면 좋은 다른 답안2

Thanks for https://leetcode.com/problems/valid-parentheses/discuss/469626/JavaScript-48-ms-faster-than-96.58

```javascript
var isValid = function(s) {   
    const stack = [];
    const map = {
      '(': ')',
      '[': ']',
      '{': '}'
    }
    
    for (let i = 0 ; i < s.length ; i++) {
        let c = s[i];
        if (map[c]) {
          stack.push(map[c])
        } else if (c !== stack.pop()) {
          return false;
        } 
    }
    
    return !stack.length;
};
```
방식은 똑같고 Map + Stack을 이용한 답안이다.  

<br/>

