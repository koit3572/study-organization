# 목차
- [주요기능·태그]오픈 그래프(OGTag)와 트위터카드(Twitter Card)
  - 오픈 그래프(OGTag)
  - 트위터 카드(Twitter Card)

# [주요기능·태그]오픈 그래프(OGTag)와 트위터카드(twitter card)
- 슬랙
  - ![슬랙 이미지](./openGraphImage1.jpg)
- 카카오톡
  - ![카카오톡 이미지](./openGraphImage2.jpg)
## 오픈 그래프(OGTag)
웹페이지가 소셜 미디어(페이스북 등)로 공유될 때 우선적으로 활용되는 정보를 지정
- [더 많은 오픈 그래프 속성 보기](https://ogp.me/)
### 기본 구조
|속성값|설명|
|--|--|
|og:type| 페이지의 내용(예, website, video.movie)|
|og:site_name| 행동하는 장소의 이름|
|og:title| 페이지의 이름(제목)|
|og:description| 페이지의 구성설명|
|og:image| 페이지의 대표 이미지 주소(URL)|
|og:url| 페이지(주소)|
```html
<meta property="og:type" content="website" />
<meta property="og:site_name" content="Starbucks" />
<meta property="og:title" content="Starbucks Coffee Korea" />
<meta property="og:description" content="스타벅스는 세계에서 가장 큰 다국적 커피 전문점으로, 64개국에서 총 23,187개의 매점을 운영하고 있습니다." />
<meta property="og:image" content="./images/starbucks_seo.jpg" />
<meta property="og:url" content="https://starbucks.co.kr" />
```
## 트위터카드(Twitter Card)
웹페이지가 신규 미디어(트위터)로 공유될 때 우선적으로 활용되는 정보
- [더 많은 트위터 카드 속성 보기](https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started)
### 기본 구조
|속성값|설명|
|--|--|
|twitter:card| 페이지(카드)의 내용(예: summary, player)|
|twitter:site| 행동하는 장소의 이름|
|twitter:title| 페이지의 이름(제목)|
|twitter:description| 페이지의 구성설명|
|twitter:image| 페이지의 대표 이미지 주소(URL)|
|twitter:url| 페이지(주소)|
```html
<meta property="twitter:card" content="summary" />
<meta property="twitter:site" content="Starbucks" />
<meta property="twitter:title" content="Starbucks Coffee Korea" />
<meta property="twitter:description" content="스타벅스는 세계에서 가장 큰 다국적 커피 전문점으로, 64개국에서 총 23,187개의 매점을 운영하고 있습니다." />
<meta property="twitter:image" content="./images/starbucks_seo.jpg" />
<meta property="twitter:url" content="https://starbucks.co.kr" />
```