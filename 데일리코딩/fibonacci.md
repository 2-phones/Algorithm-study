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
    return n
  }
  return fibonacci(n -2) + fibonacci(n - 1)
  
}
```
그냥 재귀함수를 사용을 했을더니 n값이 커지면 처리속도도 증가하여<Br>
굉장히 오래 걸렸다. 이게 바로 빅오표기법 O(N) 인것같다.


```js
let memo = [0];
function fibonacci(n){
  if(n <= 1){
    return n
  }
  if(memo[n] !== undefined) return memo[n]

memo[n] = fibonacci(n -2) + fibonacci(n - 1)
  return memo[n]
  
}
```

알고리즘 동적계획법 을 활용하여 이미 계산된 값은 다시 하지않도록<br>
처리속도를 줄여 효율적으로 푸는 방법을 학습했다.