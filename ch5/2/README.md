# 과제

## [숫자를 입력할 때까지 반복하기](https://ko.javascript.info/number#ref-368)

## 문제

    중요도: 5
    사용자가 유효한 숫자형 값을 입력할 때까지 계속 입력받는 함수 readNumber 를 만들어보세요.

    반환되는 값은 꼭 숫자형 값이어야 합니다.

    사용자가 아무 입력도 하지 않거나 '취소’를 누르면 입력받기를 멈추고 null을 반환하세요.

## 해답

```javascript
function readNumber() {
  let num;

  do {
    num = prompt("Enter a number please?", 0);
  } while (!isFinite(num));

  if (num === null || num === "") return null;

  return +num;
}

alert(`Read: ${readNumber()}`);
```

사용자가 아무것도 입력하지 않는 경우와 입력값이 null인 경우를 처리해야 해서 해답이 생각보다 복잡합니다.

이 함수는 일반적인 숫자가 입력될 때까지 입력을 받습니다. 사용자가 아무것도 입력하지 않는 경우와 입력을 취소하여 입력값이 null이 되는 경우를 살펴봅시다. 빈 문자열과 null은 숫자 형식으로는 0이기 때문에 일반적인 숫자에 해당합니다.

따라서 사용자가 아무것도 입력하지 않거나 취소하여 null이 된 경우에 그대로 숫자로 변환하게 되면 함수가 0을 반환하기 때문에, 이 두 가지의 특별한 경우에는 함수가 입력받기를 멈추고 null을 반환하도록 처리해야 합니다.

테스트 코드가 담긴 샌드박스를 열어 정답을 확인해보세요.
