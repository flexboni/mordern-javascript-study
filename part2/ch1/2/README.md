# DOM 트리

HTML 태그들은 모두 객체이다.

## 기타 노드 타입

주석도 노드가 됩니다.

```javascript
<!DOCTYPE HTML>
<html>
<body>
  사슴에 관한 진실.
  <ol>
    <li>사슴은 똑똑합니다.</li>
    <!-- comment -->
    <li>그리고 잔꾀를 잘 부리죠!</li>
  </ol>
</body>
</html>
```

![image](https://user-images.githubusercontent.com/29271126/163297095-ba896d3b-6285-41a7-ad8e-9b3e5e56653f.png)

## 요약

HTML/XML 문서는 브라우저 안에서 DOM 트리로 표현됩니다.

- 태그는 요소 노드가 되고 트리 구조를 형성합니다.
- 문자는 텍스트 노드가 됩니다.
- 이 외에 HTML 내의 모든 것은 DOM을 구성합니다. 주석까지도 말이죠.

개발자 도구를 사용하면 DOM을 검사하고, 바로 수정해 볼 수 있습니다.

지금까지 소개해 드린 개발자 도구 사용법은 가장 많이 사용되고, 중요한 기능 위주였습니다. Chrome 개발자 도구 문서 사이트 https://developers.google.com/web/tools/chrome-devtools 로 가시면 다양한 기능을 살펴볼 수 있습니다. 툴을 배울 때 가장 좋은 방법은 이리저리 클릭해보고 메뉴를 직접 열어보는 것입니다. 다양한 옵션을 확인하는 것 또한 잊으면 안되죠. 이런 과정을 통해 도구가 어느 정도 손에 익으면 문서를 정독해 부족한 나머지를 채우면 됩니다.

DOM 노드는 노드 간 이동, 수정 등을 가능하게 해주는 프로퍼티와 메서드를 지원합니다.