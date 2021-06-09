## Special Array With X Elements Greater Than or Equal X

<hr/>

### :heavy_check_mark: 내가 푼 답안

```javascript
var specialArray = function (nums) {
  for (let i = 1; i <= nums.length; i++) {
    if (i == nums.filter((e) => e >= i).length) return i;
  }

  return -1;
};
```

filter함수를 이용하여 1부터 nums의 길이만큼 조건에 해당하는 것이 있으면 return i를 바로해주고  
해당 조건에 걸리지 않으면 -1 해줬다.

<br/>
