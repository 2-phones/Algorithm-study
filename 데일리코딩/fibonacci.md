## fibonacci
---
### 문제
---
아래와 같이 정의된 피보나치 수열 중 n번째 항의 수를 리턴해야 합니다.
- 0번째 피보나치 수는 0이고, 1번째 피보나치 수는 1입니다. 그 다음 2번째 피보나치 수부터는 바로 직전의 두 피보나치 수의 합으로 정의합니다.
- 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, ...
### 입력
---
**인자 1 : n**
- number 타입의 n (n은 0 이상의 정수)
### 출력
- number 타입을 리턴해야합니다.
### 주의사항
- 재귀함수를 이용해 구현해야 합니다.
- 반복문(for, while) 사용은 금지됩니다.
- 함수 fibonacci가 반드시 재귀함수일 필요는 없습니다.
입출력 예시
```js
let output = fibonacci(0);
console.log(output); // --> 0

output = fibonacci(1);
console.log(output); // --> 1

output = fibonacci(5);
console.log(output); // --> 5

output = fibonacci(9);
console.log(output); // --> 34
```
### hint
- 피보나치 수열을 구하는 효율적인 알고리즘(O(N))이 존재합니다. 재귀함수의 호출을 직접 관찰하여 비효율이 있는지 확인해 보시기 바랍니다.
---

### ✔️ 내가 작성한 코드
```js

function fibonacci(n){
  if(n <= 1){
    return n;
  }

    return fibonacci(n -2) + fibonacci(n - 1);
}
```
<br>
그냥 재귀함수를 사용을 했을더니 n값이 커지면 처리속도도 증가하여<Br>
굉장히 오래 걸렸다. 이게 바로 빅오표기법 O(N) 인것같다.
<br>
<br>

```js
let memo = [0];
function fibonacci(n){
    if(n <= 1){
        return n;
    }
    if(memo[n] !== null) return memo[n];

    memo[n] = fibonacci(n -2) + fibonacci(n - 1);

    return memo[n];
}
```

처리속도를 줄여 효율적으로 푸는 방법을 학습했다.<br>
메모이지, 동적계획법 을 사용했는데 그냥 재귀를 사용하면, n값의 수가 커지면 컴퓨터가 푸는시간이 매우 오래걸린다.<br> 그래서 겹치는 것을 줄이기 위하여 피보라는 저장공간에 할당시켜  겹치지 않는경우만 재귀를 돌리도록 하였다.

---
```jsx

 function fibonacci (n) {
  const memo = [0, 1];
  const aux = (n) => {
    // 이미 해결한 적이 있으면, 메모해둔 정답을 리턴한다.
    if (memo[n] !== undefined) return memo[n];
    // 새롭게 풀어야하는 경우, 문제를 풀고 메모해둔다.
    memo[n] = aux(n - 1) + aux(n - 2);
    return memo[n];
  };
  return aux(n);
};
```

레퍼런스 코드인데, 왜 함수안에 또 함수를 적어줬는지, 메모를 함수안에 선언 시켰는지 질문했다.<br>

변수 메모는 함수호출시 실행되면 소멸되기 때문에 피보나치 밖에다가 선언하던가, 아니면 함수하나 더 작성하여 그함수를 재귀로 만들어 메모 변수를 재사용 할수 있게 만들었다고한다.<br>

그리고 크루분이 null 보다는 undefined 사용 하기를 권장했다.