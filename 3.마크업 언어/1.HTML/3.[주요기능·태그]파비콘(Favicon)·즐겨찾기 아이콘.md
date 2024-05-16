# 목차
- [주요기능·태그]파비콘(Favicon)·즐겨찾기 아이콘
# [주요기능·태그]파비콘(Favicon)·즐겨찾기 아이콘
웹페이지의 아이콘, 웹페이지의 로고를 설정하는 방법이다.
대부분의 경우에 favicon.ico파일을 배치하면 자동으로 찾아 로드하기 때문에 \<link/>를 필요로 하지 않는다.
그러나 favicon.png파일을 사용해 해상도를 높이고 싶다면 \<link/>코드를 삽입해야 한다.
```html
<link rel="icon" href="./favicon.png" />
```
## 아이콘 사이즈
- favicon.ico
  - 64px x 64px
  - 32px x 32px
  - 16px x 16px
- favicon.png
  - 500pxx500px
## .ico파일 제작 사이트
[iconifier](https://iconifier.net/)
해당 사이트에 이미지를 업로드하면 .ico파일을 제작할 수 있다.