## Count Primes

<hr/>

### :heavy_check_mark: 내가 푼 답안

```javascript
var countPrimes = function (n) {
  if (n < 2) return 0;

  let result = 0;

  for (let k = 2; k < n; k++) {
    result += countPri(k);
  }

  function countPri(n) {
    let check = false;
    if (n == 2) return 1;
    if (n % 2 == 0) return 0;

    for (let i = 3; i <= Math.sqrt(n); i += 2) {
      if (n % i == 0 && n != i) {
        check = true;
        break;
      }
    }
    return check ? 0 : 1;
  }

  return result;
};
```

소수구하는 함수를 따로 빼서 구현했다.  
<br/>
