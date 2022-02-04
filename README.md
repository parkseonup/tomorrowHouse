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
   ```

   ```
   // 예시 "sass": "node-sass -wr --source-map true styles/main.scss style.css"
   ```

3. 터미널에 npm 시작

   ```
   npm run 스크립트명
   ```

   ```
   // 예시 npm run sass
   ```

4. Sass Lint extension 사용

   - 터미널에 install

     ```
     npm install -D stylelint stylelint-config-recess-order stylelint-config-standard stylelint-scss
     ```

   - .stylelintrc.json 생성 : https://gist.github.com/rohjs/3ea4235ea8f044f1acc27e8dc52d40c8

## Sass 사용

1. 출력될 scss 파일에 다른 scss 파일 첨부하는 법

   ```
   @import './파일명' // 확장자 생략가능
   ```

2. reset, font 등 기반이 되는 scss 파일은 base 폴더에 \_파일명.scss 로 저장

3. 변수 선언

   - 선언 방법

     ```
     $variable: value;
     ```

     ```
     // 예시
     $hello-1: 1; // 소문자 사용시 하이픈(-) 사용
     $HELLO_2: 2; // 대문자 사용시 언더바(_) 사용
     ```

   - 전역변수, 지역변수 구분 가능
   - value에 number, string, list 등 작성 가능
   - string은 반드시 따옴표('', "") 안에 작성
   - scss import시 가장 상단에 삽입
   - string과 변수 조합

     ```
     #{$변수명}
     ```

     ```
     예시
     .col-sm-$i -> .col-sm-#{$i}
     ```

4. 디버그

   ```
   @debug
   ```

   - 터미널에 값을 출력할 때 사용 (js에서 console 같은 역할)

5. for 반복문

   ```
   @for 순서변수 from 시작순서 through 마지막순서 {}
   ```

   ```
   // 예시
   @for $i from 1 through 4 {
     @debug $i; // 결과값 1, 2, 3, 4
   }
   ```

6. 내장 함수

   - percentage(num) : 백분율 구해주는 함수
