# [문자열](https://ko.javascript.info/string)

인코딩 : 항상 UTF-16

## 특수 문자 설명

|   특수문자   | 설명                                                                                                                                                                                                              |
| :----------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|      \n      | 줄 바꿈                                                                                                                                                                                                           |
|      \r      | 캐리지 리턴(carriage return). Windows에선 캐리지 리턴과 줄 바꿈 특수 문자를 조합(\r\n)해 줄을 바꿉니다. 캐리지 리턴을 단독으론 사용하는 경우는 없습니다.                                                          |
|    \', \"    | 따옴표                                                                                                                                                                                                            |
|      \\      | 역슬래시                                                                                                                                                                                                          |
|      \t      | 탭                                                                                                                                                                                                                |
|  \b, \f, \v  | 탭                                                                                                                                                                                                                |
|      \t      | 각각 백스페이스(Backspace), 폼 피드(Form Feed), 세로 탭(Vertical Tab)을 나타냅니다. 호환성 유지를 위해 남아있는 기호로 요즘엔 사용하지 않습니다.                                                                  |
|     \xXX     | 16진수 유니코드 XX로 표현한 유니코드 글자입니다(예시: 알파벳 'z'는 '\x7A'와 동일함).                                                                                                                              |
|    \uXXXX    | UTF-16 인코딩 규칙을 사용하는 16진수 코드 XXXX로 표현한 유니코드 기호입니다. XXXX는 반드시 네 개의 16진수로 구성되어야 합니다(예시: \u00A9는 저작권 기호 ©의 유니코드임).                                         |
| \u{X…XXXXXX} | (한 개에서 여섯 개 사이의 16진수 글자) UTF-32로 표현한 유니코드 기호입니다. 몇몇 특수한 글자는 두 개의 유니코드 기호를 사용해 인코딩되므로 4바이트를 차지합니다. 이 방법을 사용하면 긴 코드를 삽입할 수 있습니다. |

### 유니코드를 사용한 예시:

```javascript
alert("\u00A9"); // ©
alert("\u{20331}"); // 佫, 중국어(긴 유니코드)
alert("\u{1F60D}"); // 😍, 웃는 얼굴 기호(긴 유니코드)
```

### 문자열의 길이

length 프로퍼티엔 문자열의 길이가 저장됩니다.

```javascript
alert(`My\n`.length); // 3, \n 는 1개로 인식
```

## 특정 글자에 접근하기

두 접근 방식의 차이는 반환할 글자가 없을 때 드러납니다. 접근하려는 위치에 글자가 없는 경우 []는 undefined를, charAt은 빈 문자열을 반환합니다.

```javascript
let str = `Hello`;

alert(str[1000]); // undefined
alert(str.charAt(1000)); // '' (빈 문자열)
```

for..of를 사용하면 문자열을 구성하는 글자를 대상으로 반복 작업을 할 수 있습니다.

```javascript
for (let char of "Hello") {
  alert(char); // H,e,l,l,o (char는 순차적으로 H, e, l, l, o가 됩니다.)
}
```

## 대·소문자 변경하기

메서드 toLowerCase()와 toUpperCase()는 대문자를 소문자로, 소문자를 대문자로 변경(케이스 변경)시켜줍니다.

```javascript
alert("Interface".toUpperCase()); // INTERFACE
alert("Interface".toLowerCase()); // interface
```

글자 하나의 케이스만 변경하는 것도 가능합니다.

```javascript
alert("Interface"[0].toLowerCase()); // 'i'
```

## 부분 문자열 추출하기

| 메서드                | 추출할 부분 문자열              | 음수 허용 여부(인수) |
| :-------------------- | :------------------------------ | :------------------- |
| \*slice(start, end)   | start부터 end까지(end는 미포함) | 음수 허용            |
| substring(start, end) | start와 end 사이                | 음수는 0으로 취급함  |
| substr(start, length) | start부터 length개의 글자       | 음수 허용            |

## 문자열 비교

### 문자열 크기

```javascript
let str = "";

for (let i = 65; i <= 220; i++) {
  str += String.fromCodePoint(i);
}
alert(str);
// ABCDEFGHIJKLMNOPQRSTUVWXYZ[\]^_`abcdefghijklmnopqrstuvwxyz{|}~
// ¡¢£¤¥¦§¨©ª«¬­®¯°±²³´µ¶·¸¹º»¼½¾¿ÀÁÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖ×ØÙÚÛÜ
```

보이시나요? 대문자 알파벳이 가장 먼저 나오고 특수 문자 몇 개가 나온 다음에 소문자 알파벳이 나오네요. Ö은 거의 마지막에 출력됩니다.

## 요약

- 자바스크립트엔 세 종류의 따옴표가 있는데, 이 중 하나인 백틱은 문자열을 여러 줄에 걸쳐 쓸 수 있게 해주고 문자열 중간에 ${…}을 사용해 표현식도 넣을 수 있다는 점이 특징입니다.
- 자바스크립트에선 UTF-16을 사용해 문자열을 인코딩합니다.
- \n 같은 특수 문자를 사용할 수 있습니다. \u...를 사용하면 해당 문자의 유니코드를 사용해 글자를 만들 수 있습니다.
- 문자열 내의 글자 하나를 얻으려면 대괄호 []를 사용하세요.
- 부분 문자열을 얻으려면 slice나 substring을 사용하세요.
- 소문자로 바꾸려면 toLowerCase, 대문자로 바꾸려면 toUpperCase를 사용하세요.
- indexOf를 사용하면 부분 문자열의 위치를 얻을 수 있습니다. 부분 문자열 여부만 알고 싶다면 includes/startsWith/endsWith를 사용하면 됩니다.
- 특정 언어에 적합한 비교 기준 사용해 문자열을 비교하려면 localeCompare를 사용하세요. 이 메서드를 사용하지 않으면 글자 코드를 기준으로 문자열이 비교됩니다.

이외에도 문자열에 쓸 수 있는 유용한 메서드 몇 가지가 있습니다.

- str.trim() – 문자열 앞과 끝의 공백 문자를 다듬어 줍니다(제거함).
- str.repeat(n) – 문자열을 n번 반복합니다.

이 외의 메서드는 MDN 문서에서 확인해보시기 바랍니다.

## 과제

### 첫 글자를 대문자로 변경하기 (중요도: 5)

    str의 첫 글자를 대문자로 바꿔 반환하는 함수, ucFirst(str)를 만들어보세요. 함수 실행 결과는 아래 예시를 충족해야 합니다.

```javascript
ucFirst("john") == "John";
```

### 스팸 문자열 걸러내기 (중요도: 5)

    str에 'viagra’나 'XXX’라는 문자열이 있으면 true를 반환해주는 함수 checkSpam(str)을 만들어보세요. 해당 문자열이 없으면 false를 반환하면 됩니다.

    함수는 대·소문자 관계없이 해당 단어를 걸러주어야 합니다.

```javascript
checkSpam("buy ViAgRA now") == true;
checkSpam("free xxxxx") == true;
checkSpam("innocent rabbit") == false;
```

### 문자열 줄이기 (중요도: 5)

    str의 길이를 확인하고, 최대 길이 maxlength를 초과하는 경우 str의 끝을 생략 부호 ("…")로 대체해주는 함수 truncate(str, maxlength)를 만들어봅시다. 새로 만든 문자열의 길이는 maxlength가 되어야 합니다.

    함수의 반환 값은 원하는 길이로 줄여진 문자열이 되어야 합니다.

예시:

```javascript
truncate("What I'd like to tell on this topic is:", 20) = "What I'd like to te…"

truncate("Hi everyone!", 20) = "Hi everyone!"
```
