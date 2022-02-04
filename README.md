# tomorrowHouse

- 김버그의 UI 개발 부트캠프 강의 프로젝트
- 오늘의집 UI 클론
- Sass(SCSS) 수업
  <br/><br/>

## Sass 설치

- 참고링크 : node-sass https://www.npmjs.com/package/node-sass
  <br/><br/>

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

4. Sass Lint extension 사용

   - .stylelintrc.json 생성 : https://gist.github.com/rohjs/3ea4235ea8f044f1acc27e8dc52d40c8
   - 터미널에 install
     ```
     npm install -D stylelint stylelint-config-recess-order stylelint-config-standard stylelint-scss
     ```

## Sass 사용

1. 출력될 scss 파일에 베이스되는 scss 파일 첨부하는 법

   ```
   @import './파일명' // 확장자 생략가능
   ```

2. reset, font 등 기반이 되는 scss 파일은 base 폴더에 \_파일명.scss 로 저장

3. 변수 선언

   - 전역변수, 지역변수 구분 가능
   - value에 number, string, list 등 작성 가능
   - string은 반드시 따옴표('', "") 안에 작성
   - scss import시 가장 상단에 삽입

   ```
   $variable: value;

   // 예시
   $hello-1: 1; // 소문자 사용시 하이픈(-) 사용
   $HELLO_2: 2; // 대문자 사용시 언더바(_) 사용
   ```
