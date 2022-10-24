#### 문제 설명

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)
문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.


### [제한사항]

- s는 길이 1 이상 200 이하인 문자열입니다.
- s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
- 숫자는 단어의 첫 문자로만 나옵니다.
- 숫자로만 이루어진 단어는 없습니다.
- 공백문자가 연속해서 나올 수 있습니다.



---

<br>

### 입출력 예

|s|return|
|-|-|
| "3people unFollowed me"	|	"3people Unfollowed Me"| 
| "for the last week"| "For The Last Week" |

<br>

##  내가 작성한 코드

```js
function solution(s) {
    var answer = 
    s.split(' ')
    .map(li => li.charAt(0).toUpperCase() + li.slice(1).toLowerCase())
    .join(' ');

    return answer;
}
```
<br>

1. `split(' ')` 메서드로 공백 기준으로 단어를 나눠 배열로 만든다.
2. for 문은 길다 map을 사용해 요소의 0번째 를 가져와 대문자로 만든다 `CharAt(0)` , `toUpperCase()`
3. 요소의 0번째를 제외한 `slice(1)` 값을 `toLowerCase()` 소문자로 만들고 `join(' ')` 공백을 기준으로 문자열로 만든다.

https://school.programmers.co.kr/learn/courses/30/lessons/12951
