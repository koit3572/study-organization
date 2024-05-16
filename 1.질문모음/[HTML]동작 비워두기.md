# [JavaScript]동작 비워두기
## 질문 의도
a태그의 href에 지정할 페이지가 준비되지 않았을때 채워넣을 수 있는 값
## 해답
### \#
```html
<a href="#">hello</a>
```
### javascript:void(0)
JavaScript를 통해서 어떤 기능을 동작시킬때, 해당 동작이 아무것도 없다(void)는것을 의미한다.
#보다는 해당문장을 권장하는데 해당문장은 정말 아무런 기능이 일어나지 않지만 \#기호는 페이지의 약간의 변화가 있을 수 있다.
```html
<a href="javascript:void(0)">hello</a>
```