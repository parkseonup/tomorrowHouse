# 내일의 집

- 김버그의 UI 개발 부트캠프 강의 프로젝트
- 오늘의집 UI 클론
- Sass(SCSS) 수업
- lnb 반응형으로 할 때 버그있음. 나중에 잡기
  <br/><br/>

### 1. GNB

- 로그인을 하지 않은 경우

```html
<div class="button-group">
  <button
    class="gnb-icon-button is-search lg-hidden"
    type="button"
    aria-label="검색창 열기 버튼"
  >
    <i class="ic-search" aria-hidden></i>
  </button>
  <a
    class="gnb-icon-button is-cart"
    href="/"
    aria-label="장바구니 페이지로 이동"
  >
    <i class="ic-cart" aria-hidden></i>
    <strong class="badge">5</strong>
  </a>
  <div class="gnb-auth sm-hidden">
    <a href="/">로그인</a>
    <a href="/">회원가입</a>
  </div>
</div>
```

- 로그인을 했을 경우

```html
<div class="button-group">
  <button
    class="gnb-icon-button is-search lg-hidden"
    type="button"
    aria-label="검색창 열기 버튼"
  >
    <i class="ic-search" aria-hidden></i>
  </button>

  <a
    class="gnb-icon-button sm-hidden"
    href="/"
    aria-label="스크랩북 페이지로 이동"
  >
    <i class="ic-bookmark" aria-hidden></i>
  </a>

  <a
    class="gnb-icon-button sm-hidden"
    href="/"
    aria-label="내 소식 페이지로 이동"
  >
    <i class="ic-bell" aria-hidden></i>
  </a>

  <a
    class="gnb-icon-button is-cart"
    href="/"
    aria-label="장바구니 페이지로 이동"
  >
    <i class="ic-cart" aria-hidden></i>
    <strong class="badge">5</strong>
  </a>

  <button
    class="gnb-avatart-button sm-hidden"
    type="button"
    aria-label="마이메뉴 열기 버튼"
  >
    <div class="avartar-32">
      <img src="./assets/images/img-user-01.jpg" alt="사달라 아저씨" />
    </div>
  </button>
</div>
```

### 2. Sidebar

- 로그인을 하지 않은 경우

  ```html
  <div class="sidebar-auth">
    <a class="btn-outlined btn-40" href="/">로그인</a>
    <a class="btn-primary btn-40" href="/">회원가입</a>
  </div>
  ```

- 로그인을 한 경우

  ```html
  <div class="sidebar-user">
    <a href="/">
      <div class="avartar-32">
        <img src="./assets/images/img-user-01.jpg" alt="사달라 아저씨" />
      </div>
      <strong class="username">사달라</strong>
    </a>
  </div>
  ```

## Sass

### Sass 설치

_참고링크 : node-sass https://www.npmjs.com/package/node-sass_
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
   // 예시

   "sass": "node-sass -wr --source-map true styles/main.scss style.css"
   ```

3. 터미널에 npm 시작

   ```
   npm run 스크립트명
   ```

   ```
   // 예시

   npm run sass
   ```

4. Sass Lint extension 사용

   - 터미널에 install

     ```
     npm install -D stylelint stylelint-config-recess-order stylelint-config-standard stylelint-scss
     ```

   - .stylelintrc.json 생성 : https://gist.github.com/rohjs/3ea4235ea8f044f1acc27e8dc52d40c8

### Sass 사용

- 출력될 scss 파일에 다른 scss 파일 첨부하는 법

  ```scss
  @import './파일명'; // 확장자 생략가능
  ```

- reset, font 등 기반이 되는 scss 파일은 base 폴더에 \_파일명.scss 로 저장

- **$variable** : 변수 선언

  - 선언 방법

    ```scss
    $variable: value;
    ```

    ```scss
    // 예시

    $hello-1: 1; // 소문자 사용시 하이픈(-) 사용
    $HELLO_2: 2; // 대문자 사용시 언더바(_) 사용
    ```

  - 전역변수, 지역변수 구분 가능
  - value에 number, string, list 등 작성 가능
  - string은 반드시 따옴표('', "") 안에 작성
  - scss import시 가장 상단에 삽입
  - string과 변수 조합

    ```scss
    #{$변수명}
    ```

    ```scss
    //예시

    .col-sm-$i -> .col-sm-#{$i}
    ```

- **Map**

  - key: value 형태로 이뤄짐 (자바스크립트의 Object와 비슷)
  - 선언시

    ```
    $변수명: (
      key1: value1,
      key2: value2,
    )
    ```

  - 사용시

    ```scss
    map-get($변수명, $key);
    ```

- **@mixin**

  - 함수와 비슷하나, 코드를 반환함

  - **기본** 선언 및 사용

    ```scss
    // 선언
    @mixin mixin명() {
      // css 내용
    }

    // 사용
    selector {
      @include mixin명();
    }
    ```

  - **parameter** 선언 및 사용

    ```scss
    // 선언
    @mixin mixin명($parameter) {
      속성: $parameter;
    }

    // 사용
    selector {
      @include mixin명($parameter);
    }
    ```

    - parameter를 안쓸 경우를 대비하여 기본값을 작성해줌

      ```scss
      @mixin mixin명($parameter: 기본값) {
        속성: $parameter;
      }
      ```

      ```scss
      // 예시

      @mixin text-style($color: false) {
        @if (type-of($color) === color) {
          color: $color;
        }
        // color 값에 px이나 boolean 값이 출력되지 않게 하기 위해 if문 작성
      }
      ```

  - **@content**

    - mixin을 include시 mixin 내부에 코드를 작성하고 싶을 때 추가로 선언해줘야 하는 것

    - 예시

      ```scss
      // 선언시
      @mixin responsive($screen) {
        if ($screen == T) {
          @media screen and (min-width: 1200px) {
            @content;
          }
        }
      }

      // 사용시
      p {
        @include responsive(T) {
          font-size: 12px;
        }
      }

      // 결과값
      p {
        @media screen and (min-width: 1200px) {
          font-size: 12px;
        }
      }
      ```

- **placeholder**

  - 공통된 스타일을 묶어서 작성해줄 때 사용
  - 선언시

    ```scss
    %스타일명 {
      // 공통스타일 작성
    }
    ```

    ```scss
    // 예시
    %tag-base {
      font-size: 12px;
      height: 20px;
      padding: 0 6px;
    }
    ```

  - 사용시

    ```scss
    선택자 {
      @extent %스타일명;
    }
    ```

    ```scss
    // 예시
    .tag-red {
      @extent %tag-base;
      background-color: red;
    }
    ```

- **@function** : 함수 선언

  - mixin과 비슷하나, 코드가 아닌 값만 반환함

    ```scss
    @function 함수명() {
      @return 값;
    }
    ```

- 내장 함수

  - **percentage()** : 백분율 구하는 함수
  - **type-of()** : type 구하는 함수

- **@debug** : 디버그

  ```scss
  @debug;
  ```

  - 터미널에 값을 출력할 때 사용 (js에서 console 같은 역할)

- **for 반복문**

  ```scss
  @for 순서변수 from 시작순서 through 마지막순서 {
  }
  ```

  ```scss
  // 예시

  @for $i from 1 through 4 {
    @debug $i; // 결과값 1, 2, 3, 4
  }
  ```
