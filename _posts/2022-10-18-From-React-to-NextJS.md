---
layout: single
title: "From React to Next.js"
categories: Front-end
tag: Next
author_profile: false
sidebar:
  nav: "docs"
# search: false
toc: true
---

**[공지사항]** 잘못된 정보나 오타에 피드백 주시면 감사하겠습니다.:)
{: .notice--info}

# 🔎 개요

현재 회사에서 웹 프론트엔드 프레임워크 중 하나인 AngularJS를 사용하고 있다. AngularJS는 업데이트 종료를 선언하였고, 이에 따라 AngularJS 코드들을 ReactJS로 리펙토링하고 싶어졌다.
또한, ReactJS로 개발을 할 때에 도움을 주는 NextJS를 배워보고자 한다.

# React에서 NextJS로

1. React를 사용한 index.html 파일이 있다고 가정한다.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>
       
    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
          const app = document.getElementById("app")

          function Header({ title }) {
           return <h1>{title ? title : "Default title"}</h1>
          }

          function HomePage() {
           const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"]

           const [likes, setLikes] = React.useState(0)

           function handleClick() {
            setLikes(likes + 1)
           }

           return (
            <div>
             <Header title="Develop. Preview. Ship. 🚀" />
             <ul>
              {names.map((name) => (
               <li key={name}>{name}</li>
              ))}
             </ul>

             <button onClick={handleClick}>Like ({likes})</button>
            </div>
           )
          }

          ReactDOM.render(<HomePage />, app)
    </script>
  </body>
</html>
```

2. package.json 파일 생성 후, 파일 내에 {}를 작성한다.

```json
// package.json
{}
```

3. 터미널에 `$npm install react react-dom next`를 입력한다.

```bash
$ npm install react react-dom next
```

4. index.html 파일에서 불필요하게 된 코드들을 삭제 및 js 혹은 jsx로 변환

   - react와 react-dom 스크립트(NPM을 사용해 react와 react-dom 스크립트를 설치)
   - `<html>`과 `<body>` 태그(Next.js가 생성)
   - 상호작용하는 app element와 `ReactDom.render()` method
   - Babel 스크립트(Next.js는 JSX를 유효한 JS 브라우저가 이해할 수 있도록 컴파일러를 보유)
   - `<script type="text/jsx">`
   - `React.useState(0)` 함수

```js
import { useState } from "react";

function Header({ title }) {
  return <h1>{title ? title : "Default title"}</h1>;
}

export default function HomePage() {
  const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];
  const [likes, setLikes] = useState(0);

  function handleClick() {
    setLikes(likes + 1);
  }

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>

      <button onClick={handleClick}>Like ({likes})</button>
    </div>
  );
}
```

5. index.js 파일을 pags 이름의 폴더 생성 후 그 안에 위치시킨다.
6. index.js 파일에 `export default`를 메인 리액터 컴포넌트 앞에 붙인다.

```js
// ...
  export default function HomePage() {
  //  ...
```

7. package.json 파일에 다음 내용을 추가한다.

```json
"scripts": {
    "dev": "next dev"
},

```

## 실행

1. 터미널에 실행 명령을 한다.

```bash
$ npm run dev
```

2. localhost:3000 에서 확인한다.

---

출처

- [Next.js 공식 홈페이지](https://nextjs.org/)
