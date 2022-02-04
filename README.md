# tomorrowHouse

- 김버그의 UI 개발 부트캠프 강의 프로젝트
- 오늘의집 UI 클론
- Sass project
  <br/><br/>

## Sass 설치

- 참고링크 : node-sass https://www.npmjs.com/package/node-sass

1. 터미널에 node-sass install

   ```
   npm i node-sass
   ```

2. package.json 파일에 script 추가

   ```
   node-sass [options] <input> [output] Or: cat <input> | node-sass > output
   // 예시 "sass": "node-sass -wr --source-map true styles/main.scss style.css"
   ```

3. 터미널에 npm 시작

   ```
   npm run 스크립트명
   // 예시 npm run sass
   ```

   <br/>

## Sass 사용

1. 출력될 scss 파일에 베이스되는 scss 파일 첨부하는 법

   ```
   @import './파일명' // 확장자 생략가능
   ```

2. reset, font 등 기반이 되는 scss 파일은 base 폴더에 \_파일명.scss 로 저장
