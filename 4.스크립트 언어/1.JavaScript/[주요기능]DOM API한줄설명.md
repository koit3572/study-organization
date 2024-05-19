# 목차
- DOM API한줄설명
  - 선택자(Selector)
  - 탐색(Quest)
  - 이벤트(Event)
  - 요소(Element)
  - 조작
    - HTML조작
    - DOM조작
# DOM API한줄설명
## 선택자(Selector)
|DOM API|설명|
|--|--|
|querySelector|CSS선택자로 찾아진 첫번째 요소만 반환|
|querySelectorAll|CSS선택자로 찾아진 모든 요소를 반환|
|getElementByClassName|class값으로 찾아진 모든 요소를 반환|
|getElementByTagName|특정 태그를 모두 선택한다.|
|getElementById|Id값으로 요소를 찾아 반환|
## 탐색(Quest)
|DOM API|설명|
|--|--|
|parentNode|부모 요소를 탐색|
|firstChild, lastChild| 자식 요소 탐색|
|childNodes|모든 자식 요소를 탐색(Nodelist)|
|children|모든 자식 요소를 탐색(HTMLCollection)|
## 이벤트(Event)
|DOM API|설명|
|--|--|
|addEventListener|요소에 특정 이벤트 발생시 함수 실행|
## 요소(Element)
|DOM API|설명|
|--|--|
|setAttribute|매개변수로("속성","속성값")을 전달받아 요소에 속성을 추가한다.|
|classList.add|전달받은 class 추가(기존 class뒤에 붙임)|
|classList.remove|전달받은 `특정` class만 삭제|
## 조작
innerHTML은 XSS에 취약하다는 단점때문에 텍스트 추가 또는 변경시에는 textContent, 새로운 요소 추가 또는 삭제시에는 DOM 조작방식을 사용하도록 한다.
- innerHTML
  - DOM조작 방식에 비해 빠르고 간편
  - XSS공격에 취약해서 값을 추가할 때 주의
  - 내용을 덮어쓰는 방식이라 비효율적
- DOM
  - 특정 노드 한개를 추가할 때 적합
  - innerHTML보다 느리고 많은 코드 필요
### HTML조작
|DOM API|설명|
|--|--|
|textContent|요소의 텍스트콘텐츠를 얻거나 변경(값으로 HTML코드를 포함시키면 문자열로 인식함)|
|innerText|HTML코드를 제외한 문자열 반환,값을 변경 시 HTML코드를 그대로 추가해야한다 그래서 XSS에 취약하며, 비표준, CSS에 순종적textContent보다 느려 사용을 지양|
|innerHTML|자식요소를 하나의 문자열로 받는다.XSS에 취약|
### DOM조작
|DOM API|설명|
|--|--|
|createElement|인자로 전달된 태그이름으로 태그 생성|
|createTextNode|인자로 전달된 텍스트로 텍스트요소 생성|
|appendChild|인자로 전달된 요소를 DOM트리에서 추가|
|removeChild|인자로 전달된 요소를 DOM트리에서 제거|