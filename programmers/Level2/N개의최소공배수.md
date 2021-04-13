## N개의 최소공배수

<hr/>

### :heavy_check_mark: 내가 푼 답안

```javascript
function solution(arr) {
  const gcd = (a, b) => (b ? gcd(b, a % b) : a);
  return arr.reduce((a, b) => (a * b) / gcd(a, b));
}
```

여러수의 최소공배수는 앞에서부터 두개의 수를 최소공배수로 리턴하는 방식으로 구한다.
ex) [2,6,8,14] => [6, 8, 14] => [24, 14] => [168]

<br/>
