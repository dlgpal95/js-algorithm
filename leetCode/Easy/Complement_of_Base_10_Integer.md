## Complement of Base 10 Integer

<hr/>

### :heavy_check_mark: 내가 푼 답안

```javascript
var bitwiseComplement = function (n) {
  let num = n.toString(2);

  let result = '';

  for (let i = 0; i < num.length; i++) {
    num[i] == 0 ? (result += 1) : (result += 0);
  }
  return parseInt(result, 2);
};
```

<hr/>

### :heavy_check_mark: 참고하면 좋은 다른 답안

Thanks for https://leetcode.com/problems/complement-of-base-10-integer/discuss/1003197/Javascript-Solution-Single-Line

```javascript
const bitwiseComplement = (N) => parseInt([...N.toString(2)].map((b) => b ^ 1).join``, 2);
```

XOR연산자를 사용한 코드이다.

<br/>
