# create-react-app
## 목차
- CRA프로젝트 TypeScript적용
  - 제거
  - 설치
  - 기존의 CAR에 TypeScript를 설치 시 추가 설치
- CRA프로젝트에서 이미지 경로를 설정하는 방법
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
## Image저장 폴더 특징
### public
- webpack에 의해 관리되지 않는다.<br/>
  (minify되지 않고, content hash가 포함되지 않는다.)
- public폴더에 접근하기 위해서는 `PUBLIC_URL 환경변수`를 사용해야한다.
- 경로가 없거나 잘못된경우, 컴파일단계에서의 에러가 아닌 404에러를 발생시킨다.
- public폴더에서 관리를 추천하는 경우
  - manifest.webmanifest처럼 build된 결과물에서 특정한 파일 이름이 필요한 경우
  - 수천개의 이미지 파일을 동적으로 참조해야 하는 경우
### src
- 경로가 없거나 잘못된 경우, 컴파일 단계에서 에러를 발생시킨다.
- import할 경우 참조할 수 있는 경로 문자열을 출력한다.

- url : https://velog.io/@rimo09/React-Create-react-app-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90%EC%84%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EA%B2%BD%EB%A1%9C%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-4%EA%B0%80%EC%A7%80-%EB%B0%A9%EB%B2%95