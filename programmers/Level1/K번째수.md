## K번째수

<hr/>

### :heavy_check_mark: 내가 푼 답안

```javascript
function solution(array, commands) {
  var answer = [];

  for (let item of commands) {
    var result = array.slice(item[0] - 1, item[1]).sort((x, y) => x - y)[
      item[2] - 1
    ];
    answer.push(result);
  }

  return answer;
}
```

`sort()`만 사용하니까 예제하나가 자꼬 오류가 나서 `sort((x, y) => x - y) x,y`를 추가했더니 통과했다.
찾아보니 sort()를 수행하면 요소를 문자열로 변경하고 유니코드에 따라 오름차순 정렬된다고한다.  
만약 **[20, 4, 2, 1]** 숫자를 `sort()`로 정렬하면 숫자의 오름차순인 **[1, 2, 4, 20]** 이 아니라 문자열의 오름차순인 **[1, 2, 20, 4]** 이 된다. 다음부터는 인자를 꼭 넣자 !

<hr/>

### :heavy_check_mark: 참고하면 좋은 다른 답안

Thanks for https://programmers.co.kr/learn/courses/30/lessons/42748/solution_groups?language=javascript&type=all

```javascript
function solution(array, commands) {
  return commands.map((command) => {
    const [sPosition, ePosition, position] = command;
    const newArray = array
      .filter(
        (value, fIndex) => fIndex >= sPosition - 1 && fIndex <= ePosition - 1
      )
      .sort((a, b) => a - b);

    return newArray[position - 1];
  });
}
```

내 코드의 `item[0]`같이 해놓은것 보다 `const [sPosition, ePosition, position] = command` 구조분해 할당을 사용하니 훨씬 정리가 된 느낌이다.  
filter함수를 이용해서 slice처럼 구현하는 방법도 참고하면 좋을 것 같다.  
다음엔 for문말고 map함수도 사용해봐야겠다!

<br/>
