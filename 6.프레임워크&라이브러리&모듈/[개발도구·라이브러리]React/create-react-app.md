# create-react-app
## 목차
- CRA프로젝트 TypeScript적용
  - 제거
  - 설치
  - 기존의 CAR에 TypeScript를 설치 시 추가 설치
- CRA 기본 구조
- CRA프로젝트에서 이미지 경로를 설정하는 방법
  - CRA프로젝트 기본 구조(이미지)
  - Image저장 폴더
  - html반환 시 

# CRA프로젝트 TypeScript적용
## 제거
사용 전 패키지를 제거하여 항상 최신 버전을 사용하는것이 좋다.
```
npm uninstall -g create-react-app

yarn global remove create-react-app
```
## 설치
```
npx create-react-app my-app --template typescript

yarn create react-app my-app --template typescript
```
## 기존의 CAR에 TypeScript를 설치 시 추가 설치
- 모든 js파일을 TypeScript파일로 바꾸고 개발서버를 다시 시작해야한다.
```
npm install --save typescript @types/node @types/react @types/react-dom @types/jest

yarn add typescript @types/node @types/react @types/react-dom @types/jest
```

# CAR 기본 구조
## public
### favicon.icon
- favicon.icon이라는 파일이 public에 있다면, 해당 파일을 찾아 페이지의 탭의 아이콘으로 사용하게 된다.
- 만약 favicon.icon파일이 해상도가 너무 떨어져 더 고해상도의 png파일을 사용하고 싶다면 favicon.png파일을 생성 후 index.html파일의 head부분에 link태그를 삽입하면된다.
```html
<link rel="icon" href="./favicon.png"/>
```
### manifest.json
- url : https://velog.io/@rmaomina/manifest-json-metadata
# CRA프로젝트에서 이미지 경로를 설정하는 방법
CRA프로젝트에서 이미지는 public폴더나 src폴더에 저장한다.
## CRA프로젝트 기본 구조(이미지)
```
- my-app
  ㄴ public
    ㄴ public_assets      // public폴더에 image저장시
      ㄴ image.png
    ㄴ ...
  ㄴ src                  
    ㄴ src_assets         // src폴더에 image저장시
      ㄴ image.png
    ㄴ ...
  ...
```
## Image저장 폴더
결론적으로는 src폴더에서 이미지를 관리하는것이 좋다.
### public
- webpack에 의해 관리되지 않는다.<br/>
  (minify되지 않고, content hash가 포함되지 않는다.)
- public폴더에 접근하기 위해서는 `PUBLIC_URL 환경변수`를 사용해야한다.
- `경로가 없거나 잘못된경우`, 컴파일단계에서의 에러가 아닌 `404에러`를 발생시킨다.
- public폴더에서 관리를 추천하는 경우
  - manifest.webmanifest처럼 build된 결과물에서 특정한 파일 이름이 필요한 경우
  - 수천개의 이미지 파일을 동적으로 참조해야 하는 경우
- CSS에서 이미지 경로 설정 
  - CSS파일에서 절대경로를 설정하면 src기준으로 경로를 찾기 때문에 에러 발생<br/>
    (src외부에 public폴더가 있기 때문)
#### public 폴더에 있는 이미지 사용
- 공식문서에서는 환경변수의 PUBLIC_URL을 사용하라고 명시되어 있지만, 다른 방식도 잘 불러와진다.
```jsx
const App = () => {
  return (
    <img
      src={`${process.env.PUBLIC_URL}/public_assets/logo.png`}
      className='App-logo'
      alt='logo'
    /> 
    // 아래의 방식도 가능
    // src={'/public_assets/logo.png'}
    // src={'public_assets/logo.png'}
  )
}
export default App;
```
### src
- 경로가 없거나 잘못된 경우, 컴파일 단계에서 에러를 발생시킨다.
- import할 경우 참조할 수 있는 경로 문자열을 출력한다.
- `content hash가 파일명에 포함`된다.<br/>
  (해당 특징으로 파일 수정전(오래된 버전)의 파일을 캐싱하고 있는 경우를 고려하지 않아도 됨, 파일 변경시만 hash값 변경)
- 서버 요청 횟수를 줄이기 위해 `10,000 bytes 이하의 이미지는 path대신 data URL을 반환`(bmp,gif,jpeg,png파일에만 적용)
  - 파일크기기준(10,000bytes) 변경 : IMAGE_INLINE_SIZE_LIMIT 환경변수로 설정
#### src 폴더에 있는 이미지 사용
- 절대경로도 src 폴더를 기준으로 하기 때문에 상대경로, 절대경로 다 사용 가능하다.
```jsx
// import 방식
import logo from "./srs_assets/logo.png";
const App = () => {
  return (
    <img
      src={logo} 
      className='App-logo' 
      alt='logo' />
    />
  )
}
export default App;
```
- node.js 환경이기 때문에 require로 문서 어디서나 파일을 불러올 수 있다
  - 해당 방법은, inline으로 src의 이미지 파일경로를 바로 지정 가능<br/>
    (처음에 모든 이미지 파일을 import 하지 않아도 되기 때문에 편리)
```jsx
// require 방식
const App = () => {
  return (
    <img 
      src={require('./src_assets/logo.png').default}
      className='App-logo'
      alt='logo'
    />
  )
}
export default App
```
## html반환 시 
### public
- minify되지 않고, content hash가 포함되지 않는다
```html
<!--content hash-->
<img src = "/public_assets/logo.png" class='App-logo' alt='logo'>
<!--dataURL-->
```
### src
- 
```html
<!--dataURL-->
<img src="data:image/png;base64,iVBOR...pkV7PpmLQrwAAAABJRU5Erkggg==" class='App-logo' alt='logo'/>
<!--content hash-->
<img src="/static/media/logo.6ce24c58.svg" class='App-logo' alt='logo'/>
```