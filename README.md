### React ESLint & Prettier

#### \* [개발자 초기세팅]()

1. Tool 에 확장프로그램 설치

   - VSCode <br>
     - ESLint <br>
     - Prittier - Code formatter<br>

2. Tool settings - VSCode <br> 1) VSCode preferences -> Settings 접속 (Ctrl + ,) <br></br> 2) format on save 검색 -> Editor: Format On Save 체크 <br>
   : 파일저장 시 코드 eslint 적용 스타일로 변경<br><br> 3) default formatter 검색 -> Editor: Default Formmatter 수정 <br>
   : Prettier - Code formatter로 수정<br><br>
   <br>

#### \* [확장프로그램 설치]() (참고)

- Reactjs code snippets : <br>
  rsc 명령어 등으로 코드 자동완성
  <br>

#### \* [구현기록]()

- **create-react-app**

  ```
  $ npx create-react-app react-eslint-prettier
  ```

- **[ESLint & Prettier]**

  - ESLint

    ```
    $ npx eslint --init
    // .eslintrc.json 파일 생성됨
    // package.json 모듈 생성됨
    ```

    ```
        How would you like to use ESLint?
        => To check syntax, find problems, and enforce code style
        What type of modules does your project use?
        => Javascript modules (import/export)
        Which framework does yout project use?
        => React
        Does your project use Typescript?
        => No
        How would you like to define a style for your project?
        => Use a popular style guide
        Where does yout code run? (Press <space> to select, <a> to toggle all, <i> to invert selection)
        => Browser, Node 둘 다 선택(spacebar 를 누르면 둘 다 선택됩니다.)
        Which style guide do you want to follow?
        => Airbnb: https://github.com/airbnb/javascript
        What format do you want your config file to be in?
        => JSON
        Would you like to install them now with npm?
        => Yes
    ```

    ````
      // ... package.json
      "devDependencies": {
          "eslint": "^6.6.0",
          "eslint-config-airbnb": "18.2.0",
          "eslint-plugin-import": "^2.21.2",
          "eslint-plugin-jsx-a11y": "^6.3.0",
          "eslint-plugin-react": "^7.20.0",
          "eslint-plugin-react-hooks": "4.0.0",
      },
      ```

    ````

  - Prettier

    1. 설치 <br>

       ```
       $ npm install --save-dev --save-exact prettier
       ```

    2. ESLint와 Prettier 규칙 충돌을 피하고 Prettier오류를 Lint에러로 보기 위해 아래 두가지 설치 <br>

       ```
       $ npm i -D eslint-config-prettier
       $ npm i -D eslint-plugin-prettier
       ```

       - eslint-config-prettier : <br>
         불필요하거나 prettier와 출동일 일어나는 모든 ESLint의 rules를 무시. <br>
       - eslint-polugin-prettier : <br>
         Prettier를 ESLint의 오류로 나타나게 해주는 패키지. 즉, prettier규칙이 ESLint규칙으로 추가 된다고 볼수 있기 때분에 ESLint 하나만 실행해도 문법검사와 formatting을 함께 실행 시킬 수 있다.

    3. 생성된 .eslintrc.json 파일 수정

       ```
       {
           "env": {
               "browser": true,
               "es2021": true,
               "node": true
           },
           "extends": [
               "plugin:react/recommended",
               "airbnb",
               "plugin:prettier/recommended",        // 새로추가
               "plugin:react/jsx-runtime"            // 새로추가, 안하면 에러남
           ],
           "overrides": [
           ],
           "parserOptions": {
               "ecmaVersion": "latest",
               "sourceType": "module"
           },
           "plugins": [
               "react"
           ],
           "rules": {
           }
       }

       ```

    4. .prettierrc.json 파일 생성 (프로젝트 최상단)

       ````
       {
           "tabWidth": 2,
           "semi": true,
           "singleQuote": true,
           "trailingComma": "all",
           "printWidth": 80
       }
           ```

       ````

    5. 패키지 및 설정값 설명

       - ESLint <br>
         eslint-config-airbnb : airbnb 코딩규칙을 사용(리액트 코딩규칙 포함)<br>
         eslint-config-prettier : prettier와 충돌을 일으키는 ESLint 규칙들을 비활성화 시키는 config<br>
         eslint-plugin-prettier : Prettier에서 인식하는 코드상의 포맷 오류를 ESLint 오류로 출력<br>
         eslint-plugin-react : React에 관한 린트설정을 지원<br>
         eslint-plugin-react-hooks : React Hooks의 규칙을 강제하도록 하는 플러그인<br>
         eslint-plugin-jsx-a11y : JSX 내의 접근성 문제에 대해 즉각적인 AST 린팅 피드백을 제공<br>
         eslint-plugin-import : ES2015+의 import/export 구문을 지원하도록 함<br>
         <br>

       - Prettier <br>
         singleQuote : single 쿼테이션 사용 여부 <br>
         semi : 세미콜론 사용 여부 <br>
         useTabs : 탭 사용 여부 <br>
         tabWidth : 탭 너비 <br>
         trailingComma : 여러 줄을 사용할 때, 후행 콤마 사용 방식 <br>
         printWidth : 줄 바꿈 할 폭 길이 <br>
         arrowParens : 화살표 함수 괄호 사용 방식<br>

    6. 실행시 에러 <br>
       ESLint 실행 : 설정해놓은 ESLint 규칙에 어긋나는 에러 console에 띄워줌 <br>

       ```
       $ npx eslint ./src/App.js
       ```

       Prettier 실행 : 설정해놓은 Prettier 규칙에 맞게 포메팅됨(수정됨)

       ```
       $ npx prettier --write ./src/App.js
       ```

#### \* [개념]()

ESLint : EcmaScript + Lint. 자바스크립트 문법을 잡아주는것<br>
Prettier : 코드 스타일을 잡아주는 코드 포맷터<br>
aitbnb : ESLint 로 가장 많이 쓰는 것으로 airbnb에서 정의한 자바스트립트 규칙<br>

<br>
[참고]  
https://wookgu.tistory.com/31
