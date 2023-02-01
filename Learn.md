![](https://camo.githubusercontent.com/f21f1fa29dfe5e1d0772b0efe2f43eca2f6dc14f2fede8d9cbef4a3a8210c91d/68747470733a2f2f6173736574732e76657263656c2e636f6d2f696d6167652f75706c6f61642f76313636323133303535392f6e6578746a732f49636f6e5f6c696768745f6261636b67726f756e642e706e67)

## Next.js

- [Foundations](#Foundations)
  - [About Next.js](#1-about-nextjs)
  - [From JavaScript to React](#2-from-javascript-to-react)
  - [From React to Next.js](#3-from-react-to-nextjs)
  - [How Next.js Works](#4-how-nextjs-works)
- [Create Your First App](#create-your-first-app)
  - [Create a Next.js App](#1-create-a-nextjs-app)
  - [Navigate Between Pages](#2-navigate-between-pages)
  - [Assets, Metadata, and CSS](#3-assets-metadata-and-css)
  - [Pre-rendering and Data Fetching](#4-pre-rendering-and-data-fetching)
  - [Dynamic Routes](#5-dynamic-routes)
  - [API Routes](#6-api-routes)
  - [Deploying Your Next.js App](#7-deploying-your-nextjs-app)
- [Search Engine Optimization](#search-engine-optimization)
  - [Introduction to SEO](#1-introduction-to-seo)
  - [Crawling and Indexing](#2-crawling-and-indexing)
  - [Rendering and Ranking](#3-rendering-and-ranking)
  - [Performanca & Core Web Vitals](#4-performanca--core-web-vitals)
  - [Improving your Core Web Vitals](#5-improving-your-core-web-vitals)
  - [Monitoring your Core Web Vitals](#6-monitoring-your-core-web-vitals)
- [Excel](#excel)
  - [TypeScript](#1-typescript)

## Foundations

### 1. About Next.js

#### 1) Introduction

#### 2) What is Next.js

### 2. From JavaScript to React

#### 1) Rendering User Interfaces

#### Rendering User Interfaces

리액트가 어떻게 동작하는지 이해하기 위해서는 먼저 어떻게 브라우저가 (UI를 생성하기 위한) 당신의 코드를 해석하는지에 대한 기본적인 이해가 필요합니다.

사용자가 웹페이지에 방문했을 때, 서버는 아래에 보이는 것과 같은 HTML 파일을 브라우저에게 반환합니다.

<img src="https://nextjs.org/static/images/learn/foundations/html-to-dom.png" height="500" width="1000"/>

브라우저는 HTML을 읽은 후 DOM(Document Object Model)을 구성합니다.

#### What is the DOM?

DOM은 HTML elements를 표현하는 객체입니다. 이것은 당신의 코드와 UI 사이의 다리로서 동작하고 부모, 자식 관계로 이루어진 트리 구조를 가집니다.

<img src="https://nextjs.org/static/images/learn/foundations/dom-to-ui.png" height="500" width="1000"/>

당신은 사용자의 이벤트를 등록하기 위해 DOM Method들과 JavaScript와 같은 프로그래밍 언어를 사용할수 있고, UI 내의 특정한 요소들을 선택, 추가, 수정, 삭제하여 DOM을 조작할 수 있습니다. DOM 조작은 구체적인 요소들을 선택할 수 있을 뿐만 아니라 그들의 스타일과 내용을 바꿀 수 있습니다.

다음 섹션에서 어떻게 JavaScript와 DOM Method를 사용하는지 알아보도록 하겠습니다.

#### 2) Updating the UI with JavaScript and DOM Methods

#### Updating the UI with JavaScript and DOM Methods

JavaScript와 DOM Method를 사용해서 어떻게 당신의프로젝트에 `h1` 태그를 추가할 수 있는지 알아보도록 하자.

먼저, 에디터를 열고 `index.html` 파일을 생성하세요. 그리고 HTML 파일 내부에 아래와 같이 입력하세요.

```html
<!-- index.html -->
<html>
  <body>
    <div></div>
  </body>
</html>
```

그런 다음 추후에 해당 요소를 선택할 수 있게 `div` 태그에 id를 부여합니다.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>
  </body>
</html>
```

HTML 파일 내부에서 JavaScript를 사용할 수 있게 `script` 태그를 추가합니다.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>
    <script type="text/javascript"></script>
  </body>
</html>
```

이제 `script` 태그 안에서 `div` 태그를 id 선택자로 선택할 수 있는 `getElementById` method를 사용할 수 있습니다.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>

    <script type="text/javascript">
      const app = document.getElementById("app");
    </script>
  </body>
</html>
```

또한 `h` 태그를 만들기 위해서도 DOM method를 사용할 수 있습니다.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>

    <script type="text/javascript">
      // Select the div element with 'app' id
      const app = document.getElementById("app");

      // Create a new H1 element
      const header = document.createElement("h1");

      // Create a new text node for the H1 element
      const headerContent = document.createTextNode(
        "Develop. Preview. Ship. 🚀"
      );

      // Append the text to the H1 element
      header.appendChild(headerContent);

      // Place the H1 element inside the div
      app.appendChild(header);
    </script>
  </body>
</html>
```

올바르게 동작하는 것을 확인하기 위해 HTML 파일을 브라우저에서 열어보면 `h1` 태그로 둘러싸인 **Develop. Preview. Ship. 🚀** 를 볼 수 있습니다.

#### HTML vs the DOM

만약 브라우저의 개발자 도구 안에서 DOM 요소들을 보게 된다면, DOM이 `h1` 요소를 포함하고 있는 것을 알아차릴 수 있습니다. 해당 페이지의 DOM은 원본 코드와 다릅니다. 다시 말해, 당신이 생성한 원본 HTML 파일과 다릅니다.

이것은 HTML은 단지 **초기 페이지의 컨텐츠만을 표현**하기 때문입니다. 반면 DOM은 **JavaScript에 의해서 바뀐 변경된 페이지의 컨텐츠를 표현**합니다.

일반 JavaScript로 DOM을 업데이트하는 것은 매우 강력하지만 장황합니다.

단지 `h1` 태그 안에 text만을 추가하기 위해서 아래의 모든 코드를 적어야합니다.

```html
<!-- index.html -->
<script type="text/javascript">
  const app = document.getElementById("app");
  const header = document.createElement("h1");
  const headerContent = document.createTextNode("Develop. Preview. Ship. 🚀");
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
```

프로젝트나 팀의 크기가 커짐에 따라 이런 방식으로 애플리케이션을 빌드하는 것은 매우 어려워질 수 있습니다. 이러한 생각을 가지고 많은 개발자들은 어떻게 컴퓨터가 작동해야 하는지를 컴퓨터에게 알려주기 위해 많은 시간을 보냈습니다.

하지만 당신이 보여주고 싶은 것을 설명하고 컴퓨터가 DOM을 업데이트 하는 방법을 알게 하는 것이 좋지 않을까요?

#### Imperative vs Declarative Programming

위 코드는 명령형 프로그래밍의 좋은 예입니다. 당신은 어떻게 UI가 업데이트 되어야 하는지에 대한 과정을 적습니다.

하지만 UI를 구성하는 것에 관해서는 개발 프로세스를 빠르게 만들 수 있기 때문에 선언적인 접근이 선호됩니다. DOM method를 적는 것 대신, 개발자가 보여주고 싶은 것을 선언할 수 있다면 더욱 도움이 될 수 있습니다.(위 예시의 경우, 몇가지 단어가 포함된 `h1` 태그).

다시 말해, **명령형 프로그래밍**은 피자 만드는 방법을 하나하나 요리사가 지시하는 것과 같습니다. **선언형 프로그래밍**은 피자를 만드는 데 필요한 과정에 대해서는 생각하지 않고 그저 피자를 주문하는 것과 같습니다.

#### React: A declarative UI library

개발자로서 당신은 리액트에게 UI에 일어나길 원하는 것을 말할 수 있습니다. 그리고 리액트는 개발자를 대신하여 DOM을 업데이트하는 과정을 알아낼 것입니다.

다음에는 어떻게 React를 시작하는지에 대해서 알아볼 예정입니다.

#### 3) Getting Started with React

#### Getting Started with React

리액트를 사용하기 위해서 당신은 [unpkg.com](https://unpkg.com/)라는 외부 웹사이트에서 두 개의 리액트 script를 받아야합니다.

- **react** 는 리액트의 중심이 되는 라이브러리입니다.
- **react-dom** 은 DOM과 함께 리액트를 사용할 수 있게 만드는 DOM 명세에 관한 메서드를 제공합니다.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>

    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>

    <script type="text/javascript">
      const app = document.getElementById("app");
    </script>
  </body>
</html>
```

일반 JavaScript로 DOM을 직접 조작하는 대신, `ReactDOM.render()` 메서드를 통해 `#app` 요소 안에 우리의 `h1` 타이틀을 렌더링시키라고 React에게 지시할 수 있습니다.

```html
<!-- index.html -->
<html>
  <body>
    <div id="app"></div>

    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>

    <script type="text/javascript">
      const app = document.getElementById("app");
      ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app);
    </script>
  </body>
</html>
```

하지만 만약 이 코드를 브라우저에 실행시키려고 하려면 문법 에러가 발생하게 될 것입니다.

<img src="https://nextjs.org/static/images/learn/foundations/error.png" />

이 에러는 `<h1>...</h1>` 이 JavaScript에 유효하지 않은 문법이기 때문에 발생합니다. 이 코드는 JSX입니다.

#### What is JSX?

JSX는 친숙한 HTML과 비슷한 문법으로 당신의 UI를 설명할 수 있게 만들어주는 JavaScript를 위한 문법적인 확장입니다. JSX의 훌륭한 점은 [세 가지의 JSX 규칙](https://beta.reactjs.org/learn/writing-markup-with-jsx#the-rules-of-jsx) 을 따르는 것 외에는 HTML과 JavaScript의 어떤 새로운 심볼이나 문법을 배울 필요가 없다는 점입니다.

브라우저는 JSX를이해할 수 없다는 것을 기억하세요. 그렇기 때문에 당신은 JSX를 일반 JavaScript로 변환하기 위해 [Babel](https://babeljs.io/)과 같은 JavaScript 컴파일러가 필요합니다.

#### Adding Babel to your project

프로젝트에 Babel을 추가하기 위해서 `index.html` 파일 안에 아래와 같은 `script` 를 복사하여 붙여넣기 하세요.

```html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```

추가적으로, 스크립트 유형을 `type=text/jsx` 로 바꿔주어 변환되어야 하는 코드를 Babel에게 알려줄 필요가 있습니다.

```html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <!-- Babel Script -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
      const app = document.getElementById('app');
      ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app);
    </script>
  </body>
</html>
```

이제 당신의 코드가 브라우저에서 정확하게 돌아가고 있는 것을 확인할 수 있습니다.

방금 작성한 **선언적인** React 코드를 비교하면 다음과 같습니다.

```html
<script type="text/jsx">
  const app = document.getElementById("app")
  ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app)
</script>
```

이전 섹션에서 작성한 명령적인 JavaScript 코드

```html
<script type="text/javascript">
  const app = document.getElementById("app");
  const header = document.createElement("h1");
  const headerContent = document.createTextNode("Develop. Preview. Ship. 🚀");
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
```

당신은 React를 사용하여 수많은 반복적인 코드를 줄일 수 있는 방법을 확인할 수 있습니다.

> **Note**: React를 사용하기 위해서 React가 어떻게 UI를 업데이트 하는지 정확하게 알 필요는 없습니다. 하지만 더 배우고 싶다면 React 공식 문서의 [UI trees](https://beta.reactjs.org/learn/preserving-and-resetting-state#the-ui-tree) 와 [render method](https://beta.reactjs.org/apis/react-dom/render) 섹션을 살펴보시길 바랍니다.

#### 4) Essential JavaScript for React

#### 리액트를 하기 위한 필수 요소 자바스크립트

자바스크립트와 리액트를 동시에 배울 수 있지만 자바스크립트를 익숙하게 할 수 있는 건 리액트를 더 쉽게 만듭니다.

다음 섹션에서 자바스크립트 관점에서의 리액트 중요 개념을 소개할 것입니다.

- [함수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Functions)와 [화살표 함수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- [객체](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object)
- [배열과 배열 메서드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [구조 분해 할당](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- [템플릿 리터럴](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Template_literals)
- [삼항 연산자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)
- [ES 모듈 가져오기 및 내보내기](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Modules)

이 과정에서는 자바스크립트에 대한 깊은 개념을 다루지는 않지만 , 최신 버전의 자바스크립트 개념을 알고 있으면 좋습니다. 아직 자바스크립트에 대해 능숙하지 않더라도 , 리액트를 시작하는 것에 대해 두려워하지 마세요!

#### 5) React Core Concepts

#### 리액트의 핵심 개념

리액트를 시작하기에 앞서 익숙해져야 할 3가지 핵심 개념이 있습니다.

- 컴포넌트
- Props
- 상태

다음 섹션에서는 위에 개념들에 대해서 살펴보고 계속 학습할 수 있는 자료를 제공할 것입니다.

#### 6) Building UI with Components

#### UI 구축 with 컴포넌트

유저 인터페이스(UI)는 컴포넌트라고 불리는 더 작은 조각으로 나눌 수 있습니다.

컴포넌트는 독립적이고 재사용 가능한 코드 스니펫을 가능하게 합니다. 만약에 컴포넌트를 레고 조각으로 생각한다면 각각의 조각을 결합하여 더 큰 구조물을 만들 수 있습니다. 만약에 UI 한 부분을 업데이트해야 한다면 특정 컴포넌트 또는 조각을 업데이트 할 수 있습니다.

![](https://nextjs.org/static/images/learn/foundations/components.png)

이러한 방식은 코드를 더 유지 보수할 수 있게 만들고 , 어플리케이션을 건들지 않고 추가 , 수정 , 삭제를 가능하게 합니다.

**컴포넌트 만들기**

리액트에서 컴포넌트는 함수입니다. `script` 태그 안에 작성하면 됩니다.

```html
<script type="text/jsx">
  const app = document.getElementById("app")


  function header() {
  }

  ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app)
</script>
```

컴포넌트는 ui 요소를 반환하고 , `return`문 안에 JSX를 작성할 수 있습니다.

```html
<script type="text/jsx">
  const app = document.getElementById("app")

  function header() {
     return (<h1>Develop. Preview. Ship. 🚀</h1>)
   }

  ReactDOM.render(, app)
</script>
```

컴포넌트를 DOM에 렌더링 하기 위해 `ReactDOM.render()` 메서드에 첫번째 인자로 전달할 수 있습니다.

```html
<script type="text/jsx">

  const app = document.getElementById("app")

  function header() {
     return (<h1>Develop. Preview. Ship. 🚀</h1>)
   }


   ReactDOM.render(header, app)
</script>
```

하지만 , 브라우저 위에서 위 코드를 돌린다면 에러가 발생합니다. 이 작업을 수행하려면 아래의 2가지 작업을 실행해야 합니다.

첫번째 , React 컴포넌트는 HTML와 자바스크립트 코드와 구분하기 위해 대문자로 표시해야 합니다.

```js
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}

// Capitalize the React Component
ReactDOM.render(Header, app);
```

두번째 , React 컴포넌트는 HTML 태그와 같이 괄호 안에서 사용합니다.

```js
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}

ReactDOM.render(<Header />, app);
```

**중첩 컴포넌트**

보통 어플리케이션은 한 개의 컴포넌트보다 더 많은 정보를 담고 있습니다. 일반 HTML처럼 React 컴포넌트는 서로 중첩이 가능합니다.

예시로 `HomePage` 컴포넌트를 만들어보겠습니다.

```js
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}
function HomePage() {
  return <div></div>;
}

ReactDOM.render(<Header />, app);
```

새로 만든 `HomePage` 컴포넌트안에 `Header` 컴포넌트를 중첩시킵니다.

```js
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}

function HomePage() {
  return (
    <div>
      {/* Nesting the Header component */}
      <Header />
    </div>
  );
}

ReactDOM.render(<Header />, app);
```

**컴포넌트 트리**

![](https://nextjs.org/static/images/learn/foundations/component-tree.png)

예를 들어 , 최상위 컴포넌트인 `HomePage` 컴포넌트는 `Header` , `Article` , `Footer` 컴포넌트를 가질 수 있습니다. 이러한 각각의 컴포넌트는 자신의 자식 컴포넌트를 가질 수 있습니다. 예시로 `Header` 컴포넌트는 `Logo` , `Title` , `Nav` , `Link` 컴포넌트를 자식으로 갖고 있습니다.

이런 방식은 app 안에서 다양하게 재사용 가능하게 합니다.

프로젝에서 `HomePage` 컴포넌트가 최상위 컴포넌트라면 `ReactDOM.render()` 메서드에 전달하세요.

```js
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}

function HomePage() {
  return (
    <div>
      <Header />
    </div>
  );
}

ReactDOM.render(<HomePage />, app);
```

다음 섹션에서는 , **props**에 대해서 얘기하고 어떻게 컴포넌트 사이에서 데이터를 전달하는지 알아보도록 하겠습니다.

#### 7) Displaying Data with Props

지금까지는 `<Header />` 컴포넌트를 재사용할 경우 같은 내용을 보여줬다.

```jsx
function Header() {
  return <h1>Develop. Preview. Ship. 🚀</h1>;
}

function HomePage() {
  return (
    <div>
      <Header />
      <Header />
    </div>
  );
}
```

하지만 다른 내용을 넘겨주고 싶거나 외부 소스에서 데이터를 가져와 어떤 정보를 넘겨줘야 할지 사전에 알지 못하는 경우에는 어떻게 해야할까?

일반적인 HTML 요소는 해당 요소의 동작을 변경하는 정보를 전달하기 위해 사용할 수 있는 속성을 가지고 있다. 예를 들어 `<img>` 의 `src` 속성을 변경하면 표시되는 이미지가 변경된다. `<a>` 태그의 `href` 속성을 변경하면 링크의 대상이 변경된다.

동일한 방식을 사용하여 우리는 정보의 일부를 리액트 컴포넌트에 속성으로 전달할 수 있으며 이를 props라고 한다.

![image](https://user-images.githubusercontent.com/95066223/204819353-b86ebfdd-4de1-4b38-aed4-874d266b2146.png)

자바스크립트 함수와 비슷하게 컴포넌트의 동작이나 화면에 렌더링 될 때 보여지는 내용을 변경하는 인자(혹은 props)를 받도록 컴포넌트를 설계할 수 있다. 그리고 이러한 props를 부모 컴포넌트에서 자식 컴포넌트로 전달할 수 있다.

> 참고 : 리액트에서 데이터는 컴포넌트 트리 아래로 흐르며 이를 단방향 데이터 흐름이라고 한다. 다음 섹션에서 다룰 State는 부모에서 자식 컴포넌트로 전달된다.

### Using props

우리는 HTML 속성을 전달하는 것과 비슷한 방식으로 `HomePage` 컴포넌트에서 `Header` 컴포넌트로 원하는대로 변경할 수 있는 `title` 속성을 넘길 수 있다.

```jsx
// function Header() {
//   return <h1>Develop. Preview. Ship. 🚀</h1>
// }

function HomePage() {
  return (
    <div>
      <Header title="React 💙" />
    </div>
  );
}

// ReactDOM.render(<HomePage />, app)
```

그리고 자식 요소인 `Header` 는 이러한 props들을 함수의 첫 번째 매개변수로 받아들일 수 있다.

```jsx
function Header(props) {
//   return <h1>Develop. Preview. Ship. 🚀</h1>
// }

// function HomePage() {
//   return (
//     <div>
//       <Header title="React 💙" />
//     </div>
//   )
// }

// ReactDOM.render(<HomePage />, app)
```

만약 props를 `console.log()` 로 확인해보면 props가 title 속성을 가지고 있는 객체라는 것을 알 수 있다.

```jsx
function Header(props) {
    console.log(props) // { title: "React 💙" }
//   return <h1>React 💙</h1>
// }

// function HomePage() {
//   return (
//     <div>
//       <Header title="React 💙" />
//     </div>
//   )
// }

// ReactDOM.render(<HomePage />, app)
```

props가 객체이므로 우리는 객체 비구조화를 사용하여 함수 매개변수 내의 props의 값을 명시적으로 지정할 수 있다.

```jsx
function Header({ title }) {
    console.log(title) // "React 💙"
//  return <h1>React 💙</h1>
// }

// function HomePage() {
//   return (
//     <div>
//       <Header title="React 💙" />
//     </div>
//   )
// }

// ReactDOM.render(<HomePage />, app)
```

이제 우리는 `<h1>` 태그의 내용을 title 변수를 사용하여 변경할 수 있다.

```jsx
function Header({ title }) {
  console.log(title);
  return <h1>title</h1>;
}
```

하지만 브라우저에서 프로젝트를 열게 되면 우리는 ‘title’ 이라는 실제 단어만을 나타내고 있는 것을 볼 수 있다. 이는 리액트가 우리가 일반 텍스트 문자열을 DOM에 렌더링하기를 원했다고 생각하기 때문이다.

우리는 title이 자바스크립트 변수라는 것을 리액트에 표시할 수 있는 방법이 필요하다.

**Using Variables in JSX**

정의한 변수를 사용하기 위해서 일반 자바스크립트를 JSX 마크업 내에 직접 작성할 수 있도록 해주는 특수 JSX 구문인 중괄호를 사용할 수 있다.

```jsx
// function Header({title}) {
//  console.log(title)
return <h1>{title}</h1>;
// }
```

중괄호를 JSX의 영역에서 자바스크립트 영역으로 넘어가는 방법이라고 생각할 수 있다. 중괄호 안에서는 어떠한 자바스크립트 표현( 단일 값으로 평가되는 것)도 추가 가능하다. 아래는 그 예시이다.

1. Dot notation(점 표기법)을 사용한 객체 속성 접근

   ```jsx
   function Header(props) {
     return <h1>{props.title}</h1>;
   }
   ```

2. A **template literal**

   ```jsx
   function Header({ title }) {
     return <h1>{`Cool ${title}`}</h1>;
   }
   ```

3. 함수의 반환값

   ```jsx
   function createTitle(title) {
     if (title) {
       return title;
     } else {
       return "Default title";
     }
   }

   function Header({ title }) {
     return <h1>{createTitle(title)}</h1>;
   }
   ```

4. 삼항 연산자

   ```jsx
   function Header({ title }) {
     return <h1>{title ? title : "Default Title"}</h1>;
   }
   ```

이제 우리는 title props에 어떠한 문자열도 전달할 수 있으며 삼항 연산자를 이용하여 기본값을 할당하는 방법을 이용하면 title prop을 전달하지 않아도 된다.

```jsx
function Header({ title }) {
  return <h1>{title ? title : "Default title"}</h1>;
}

function Page() {
  return (
    <div>
      <Header />
    </div>
  );
}
```

이제 우리는 title만 변경하면 애플리케이션의 다른 부분에서 재사용할 수 있는 generic title prop을 사용할 수 있다.

**Iterating through lists**

데이터를 목록으로 보여주는 것은 일반적이다. 우리는 배열 메소드를 사용하여 데이터를 조작하고 스타일은 동일하지만 정보가 다른 UI 요소를 생성 할 수 있다.

> 참고 : 리액트는 데이터를 가져오는 것에 대한 언급이 없습니다. 즉 우리의 필요에 따라 가장 적합한 방법을 선택할 수 있습니다. 이후에 Next.js에서 데이터를 가져오는 옵션에 대해 설명할 것입니다. 하지만 지금은 단순한 배열을 사용하여 데이터를 나타낼 수 있습니다.

`HomePage` 컴포넌트에 이름으로 된 배열을 추가하겠습니다.

```jsx
function HomePage() {
  const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
    </div>
  );
}
```

우리는 `array.map()`을 사용하여 배열을 반복하고 화살표 함수를 사용하여 이름을 리스트 아이템에 매핑할 수 있다.

```jsx
function HomePage() {
  const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```

어떻게 중괄호를 사용하여 자바스크립트와 JSX의 영역을 넘나드는지 주목해야 한다.

만약 위의 코드를 실행한다면 리액트는 `key` prop이 없다는 경고를 표시한다. 이는 리액트가 DOM에서 업데이트할 요소를 알 수 있도록 배열에서 리스트를 고유하게 식별할 수 있는 무언가가 필요하기 때문이다. 현재 배열에서 각각의 항목들은 고유하므로 사용할 수는 있지만 id와 같이 고유한 값이 보장되는 것을 키로 사용하는 것이 좋다.

```jsx
function HomePage() {
  const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```

다음 섹션에서는 state와 리액트에서 유저의 이벤트를 어떻게 감지하는지에 대해 배운다.

#### 8) Adding Interactivity with State

리액트를 통해 상태 및 이벤트 핸들러와의 상호 작용을 추가하는 방법에 대해 알아보자.

예를 들어 `HomePage` 컴포넌트에 버튼을 하나 생성해보자. 먼저 버튼 요소를 return() 문 안에 추가한다.

```jsx
function HomePage() {
  const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>

      <button>Like</button>
    </div>
  );
}
```

**Listening to Events**

버튼을 클릭했을 때 어떤 작업을 수행하게 하기 위해서 우리는 `onClick` 이벤트를 사용할 수 있다.

```jsx
function HomePage() {
  // ...
  return (
    <div>
      {/* ... */}
      <button onClick={}>Like</button>
    </div>
  );
}
```

리액트에서 이벤트의 이름은 camelCase로 작성한다. `onClick` 이벤트는 유저의 상호 작용에 응답하기 위해 사용할 수 있는 여러 이벤트 중 하나이다. 예를 들어 input fields를 위해 `onChange` 를 사용하거나 `form` 을 위해 `onSubmit` 을 사용할 수 있다.

**Handling Events**

이벤트가 트리거 될 때마다 이벤트를 ‘handle’ 하는 함수를 정의할 수 있다. return 문 전에 `handleClick` 이라는 함수를 생성한다.

```jsx
function HomePage() {
  // ...

  function handleClick() {
    console.log("increment like count")
  }

  return (
    <div>
      {/* ... */}
      <button onClick={}>Like</button>
    </div>
     )
   }
```

그러면 `onClick` 이벤트가 트리거 되었을 때 `handleClick` 함수를 호출할 수 있다.

```jsx
function HomePage() {
  //    ...
  function handleClick() {
    console.log("increment like count");
  }

  return (
    <div>
      {/* ... */}
      <button onClick={handleClick}>Like</button>
    </div>
  );
}
```

**State and Hooks**

리액트는 hooks이라고 불리는 함수가 있다. Hooks를 사용하면 state와 같은 로직을 컴포넌트에 추가할 수 있다. state는 시간이 지남에 따라 변경되는 UI 정보로 간주할 수 있으며 일반적으로 유저의 상호작용에 의해 트리거된다.

![image](https://user-images.githubusercontent.com/95066223/204819545-c2b56b26-4388-4bac-86ed-78e111068deb.png)

우리는 state를 사용하여 사용자가 좋아요 버튼을 클릭한 횟수를 저장하고 증가시킬 수 있다. `useState()` 는 state를 관리하는 리액트 훅이다.

```jsx
function HomePage() {
  React.useState();
}
```

`useState()` 는 배열을 반환하며 배열 비구조화를 사용하여 컴포넌트 내의 해당 배열 값에 접근하여 사용할 수 있다.

```jsx
function HomePage() {
  const [] = React.useState();

  // ...
}
```

배열의 첫번째 값은 상태값이며 어떠한 이름을 지어도 되지만 서술적인 이름을 지정하는 것이 좋다.

```jsx
function HomePage() {
  const [likes] = React.useState();

  // ...
}
```

배열의 두번째 값은 값을 업데이트할 수 있는 함수이다. 우리는 해당 함수의 이름을 자유롭게 지을 수 있지만 일반적으로 set 뒤에 업데이트 중인 상태 변수의 이름을 추가한다.

```jsx
function HomePage() {
  const [likes, setLikes] = React.useState();

  // ...
}
```

`likes`의 초기값을 0으로 설정해줄 수도 있다.

```jsx
function HomePage() {
  const [likes, setLikes] = React.useState(0);
}
```

그러면 컴포넌트 내부의 상태 변수를 사용하여 초기 상태인지 확인할 수 있다.

```jsx
function HomePage() {
  // ...
  const [likes, setLikes] = React.useState(0);

  return (
    // ...
    <button onClick={handleClick}>Like({likes})</button>
  );
}
```

마지막으로 `HomePage` 컴포넌트 안에서 상태 업데이트 함수인 `setLikes` 추가할 수 있다. 이전에 정의한 `handleClick()` 안에 추가했다.

```jsx
function HomePage() {
  // ...
  const [likes, setLikes] = React.useState(0);

  function handleClick() {
    setLikes(likes + 1);
  }

  return (
    <div>
      {/* ... */}
      <button onClick={handleClick}>Likes ({likes})</button>
    </div>
  );
}
```

버튼을 클릭하면 `handleClick()` 함수가 실행되며 해당 함수는 현재 좋아요 수에 1을 더한 값을 단일 인수로 가지는 `setLikes` 를 호출한다.

> 참고 : 첫 번째 함수 매개 변수로 구성 요소에 전달되는 props와 달리 상태는 컴포넌트 안에서 초기화되고 저장된다. 상태 정보를 자식 컴포넌트에 props로 전달할 수 있지만 상태 업데이트를 위한 로직은 처음 상태가 생성된 컴포넌트 내에서 유지되어야 한다.

Managing State

위 내용은 상태에 대한 소개일 뿐이며 리액트 애플리케이션에서의 상태 관리와 데이터 흐름에 대해서는 배울 내용이 훨씬 많다. 해당 내용에 대해 더 알아보기 위해서는 리액트 공식 문서의 [Adding Interactivity](https://beta.reactjs.org/learn/adding-interactivity), [Managing State](https://beta.reactjs.org/learn/managing-state) 섹션을 참고해라.

#### 9) How to continue learning React

방금 리액트의 필수적인 개념인 컴포넌트, props, 상태에 대해 알아보았다. 해당 내용에 대해 강력한 기반을 갖추는 것은 리액트 애플리케이션을 구축하는 것을 시작하는 데 도움이 될 것이다. 해당 내용들에 대해 자신감을 가졌다면 아래와 같은 다른 리액트의 주제들도 확인하면 좋다.

- [How React handles renders](https://beta.reactjs.org/learn/render-and-commit) and [how to use refs](https://beta.reactjs.org/learn/referencing-values-with-refs)

리액트에서 렌더링을 다루는 방법과 ref를 사용하는 방법

- [How to manage state](https://beta.reactjs.org/learn/managing-state)

  상태를 다루는 방법

- [How to use context for deeply nested data](https://beta.reactjs.org/learn/passing-data-deeply-with-context)

  깊이 중첩된 데이터를 위해 context를 사용하는 방법

- [How to use React API hooks](https://beta.reactjs.org/reference) such as `useEffect()`

  `useEffect()`와 같은 리액트 API 훅 사용 방법

**React Resources**

시간이 지나며 개발자들을 위해 리액트를 가르쳐 주는 강의, 영상, 문서들이 많이 만들어졌다. 학습 스타일에 맞는 자료를 추천하기는 어렵지만 중요한 참고 자료 중 하나는 해당 주제를 연습하는 데 도움이 되는 sandbox가 포함된 리액트 공식 문서이다.

리액트를 배우는 데 있어 가장 좋은 방법은 직접 구축해보는 것이다. 기존에 존재하는 웹 사이트에 `<script>`와 지금까지 배운 것들을 이용하여 작은 컴포넌트를 추가하는 것을 시작으로 리액트를 점차적으로 늘려나갈 수 있다. 하지만 많은 개발자들은 사용자와 개발자의 경험에 있어서 리액트가 전체 프론트엔드 프로젝트를 작성할 수 있을 정도록 가치가 있다는 것을 알게 되었다.

**From React to Next.js**

리액트는 UI를 구축하는데 탁월하지만 그 UI를 완전히 작동하는 확장 가능한 애플리케이션으로 독립적으로 구축하는 데 약간의 작업이 필요하다. 좋은 소식은 Next.js가 대부분의 설정 및 구성을 처리하고 React 응용 프로그램을 빌드한느 데 도움이 되는 추가 기능을 가지고 있다는 것이다.

다음으로는 예제를 React에서 Next.js로 마이그레이션하고 Next.js의 작동 방식에 대해 설명하고 고급 Next.js 기능을 학습하는 데 도움이 되는 몇 가지 웹 개발 개념을 소개한다.

### 3. From React to Next.js

#### 1) Introduction

#### 2) Getting Started with Next.js

#### 3) Next Steps

### 4. How Next.js Works

#### 1) Introduction

Next.js의 심화 내용을 배우기 전에 어떻게 Next.js가 동작하는 방식에 대한 기본적이 이해가 있다면 좋습니다.

이 과정의 시작 부분에서 React가 애플리케이션을 build하는 다양한 방식이 있고 어떻게 애플리케이션을 구조화하고 구축하는지에 대해 이야기 했습니다. Next.js는 애플리케이션을 구조화할 수 있는 프레임워크와 개발 과정과 애플리케이션 모두 더욱 빠르게 만드는 데 도움이 되는 최적화를 제공합니다.

다음 섹션에서는 아래의 보여주는 서로 다른 공간에서 애플리케이션의 코드에 어떤 일이 발생하는지를 알아볼 것입니다.

- 코드가 작동하는 곳의 환경 : **Development vs. Production**
- 코드가 작동할 때의 시점 : **Build Time vs. Runtime**
- 어디에서 rendering이 발생하는가 : **Client vs. Server**

이제 Next.js가 작동하는 동안 뒤에서 벌어지는 여러가지 process에 대해 논의하고 개념들을 깊게 공부해봅시다!

#### 2) From Development to Production

#### Development and Production Environments

환경을 코드가 동작하는 Context로 생각할 수 있습니다.

개발을 하는 동안 local machine에서 애플리케이션을 빌드하고 실행합니다. 프로덕션 환경으로 이동하는건 애플리케이션이 배포되고 유저들이 사용할 수 있도록 만드는 과정입니다.

#### How this applies to Next.js

Next.js는 애플리케이션의 development와 production 환경을 위한 여러 기능을 제공합니다. 예를 들어,

- 개발 환경(Development)에서 Next.js는 애플리케이션 build에 대해 최적화된 경험을 제공합니다. Next.js는 [TypeScript](https://nextjs.org/docs/basic-features/typescript), [ESLint integration](https://nextjs.org/docs/basic-features/eslint), [Fast Refresh](https://nextjs.org/docs/basic-features/fast-refresh) 등과 같이 **Developer Experience(개발자 경험)** 을 향상시키는데 목적을 둔 기능들을 함께 제공합니다.
- 배포 환경(Production)에서 Next.js는 최종 사용자와 애플리케이션을 사용하는 경험을 최적화합니다. Next.js는 성능과 접근성을 높이기 위해 코드를 변환하는 데 목적을 둡니다.

각 환경마다 목표과 고려사항들이 다르기 때문에 애플리케이션을 development 환경에서 production 환경으로 옮기기 위해서는 완료되어야 되는 것들이 많습니다. 예를 들어, 애플리케이션의 코드는 [컴파일](https://nextjs.org/learn/foundations/how-nextjs-works/compiling), [번들링](https://nextjs.org/learn/foundations/how-nextjs-works/bundling), [축소](https://nextjs.org/learn/foundations/how-nextjs-works/minifying) 및 [코드 분할](https://nextjs.org/learn/foundations/how-nextjs-works/code-splitting)이 필요합니다.

#### The Next.js Compiler

Next.js는 수많은 코드 변환과 인프라 설정을 처리하여 더욱 수비게 애플리케이션을 production 환경으로 전환시켜줍니다.

이것은 Next.js가 저수준 언어인 Rust로 만들어져 compilation, minification, bundling 등에 사용할 수 있는 플랫폼인 SWC라는 컴파일러를 가지고 있기 때문에 가능합니다.

#### 3) Compiling

개발자들은 JSX, TypeScript 그리고 현대적인 JavaScript 같이 더욱 개발자 친숙한 언어들로 코드를 작성합니다. 이런 변화는 개발자들의 효율성과 자신감을 높여줬지만 브라우저가 이해할 수 있게 JavaScript로 compile 해줄 필요가 있습니다.

Compiling은 한 언어로 된 를 다른 언어 또는 해당 언어의 다른 버전으로 바꿔주는 과정을 의미합니다.

<img src="https://nextjs.org/static/images/learn/foundations/compiling.png" />

Next.js에서 **Compliation** 은 당신의 코드를 수정하거나 애플리케이션 배포를 위한 build의 일부 과정 동안 발생합니다.

#### 4) Minifying

개발자는 가독성을 높이는 코드를 작성합니다. 이러한 코드는 주석, 공백, 들여쓰기, 여러 줄 등의 코드를 동작시키는데 필요하지 않은 추가적인 정보들을 포함할 지도 모릅니다.

<img src="https://nextjs.org/static/images/learn/foundations/minifying.png" />

Minification(최소화) 코드 기능의 변화 없이 주석, 코드 포매팅과 같은 불필요한 코드를 제거하는 과정입니다. 파일 크기를 줄여 애플리케이션의 성능을 개선시키는 것이 Minification의 목표입니다.

Next.js에서 JavaScript와 CSS 파일은 배포 환경에서 자동적으로 최소화시킵니다.

#### 5) Bundling

#### What is Bundling?

개발자들은 애플리케이션을 더 큰 애플리케이션을 구축하는 데 사용할 수 있는 module, components, function으로 분리합니다. 이러한 내부 모듈과 외부 패키지들을 내보내고 가져오게 되면 비로소 파일 종속성을 가진 복잡한 웹이 만들어집니다.

<img src="https://nextjs.org/static/images/learn/foundations/bundling.png" />

번들링은 유저가 웹 페이지를 방문할 때 파일에 대한 수많은 요청을 줄이기 위해 웹의 의존성들을 해결하고 파일이나 모듈을 브라우저의 최적화된 번들로 병합(또는 패키징)하는 과정을 말합니다.

#### 6) Code Splitting

개발자들은 보통 각기 다른 URL에서 접근할 수 있게 만들기 위해 여러 개의 페이지로 애플리케이션을 분리합니다. 그리고 이 각각의 페이지는 애플리케이션의 유일한 **entry point** 가 됩니다.

<img src="https://nextjs.org/static/images/learn/foundations/code-splitting.png" />

Next.js는 코드 스플리팅을 기본적으로 지원합니다. `pages/` 디렉토리 안의 각 파일은 build단계 동안 자동적으로 JavaScript 번들로 분리됩니다.

추가사항:

- 페이지들 간 공유되는 코드는 페이지 이동 간에 같은 코드를 다시 다운로드 받지 않기 위해 또다른 bundle로 분리됩니다.
- 페이지 초기 로드 후, Next.js는 이동 가능한 다른 페이지의 코드를 [pre-loading](https://nextjs.org/docs/api-reference/next/link) 할 수 있습니다.
- [Dynamic imports](https://nextjs.org/docs/advanced-features/dynamic-import) 는 초기에 로드된 코드를 명시적으로 분리하는 또 다른 방법입니다.

#### 7) Build Time vs. Runtime

**Build Time**(or build step)은 배포를 위해 애플리케이션의 코드를 준비하는 일련의 과정에 붙혀진 이름입니다.

애플리케이션을 build 할 때, Next.js는 당신의 코드를 [서버](https://nextjs.org/learn/foundations/how-nextjs-works/client-and-server)에 배포하고 사용자들이 이용할 준비가 된 프로덕션에 최적화된 파일로 변경할 것입니다. 이 파일을 다음과 같은 것을 포함합니다.

- 정적으로 생성된 페이지의 HTML 파일
- [서버](https://nextjs.org/learn/foundations/how-nextjs-works/client-and-server)에서 페이지를 [렌더링](https://nextjs.org/learn/foundations/how-nextjs-works/rendering) 하기 위한 JavaScript 코드
- [클라이언트](https://nextjs.org/learn/foundations/how-nextjs-works/client-and-server)에서 동적으로 만드는 페이지를 위한 JavaScript 코드
- CSS 파일

**Runtime**(or request time)은 애플리케이션이 빌드와 배포가 된 후 사용자의 요청에 대한 응답으로 애플리케이션이 실행하는 기간을 의미합니다.

다음으로 클라이언트, 서버 그리고 렌더링에 대해서 이야기 해보도록 하겠습니다.

#### 8) Client and Server

웹 애플리케이션의 맥락에서 **Client**는 애플리케이션 코드를 위해 서버에 요청을 보내는 사용자 기기의 브라우저를 말합니다. 그리고 서버로부터 받은 응답을 사용자가 상호 작용할 수 있는 인터페이스로 바꿉니다.

<img src="https://nextjs.org/static/images/learn/foundations/client-server.png" />

**Server** 는 애플리케이션의 코드를 저장하고, Client로부터 요청을 받고, 몇가지의 연산을 진행하고, 적절한 응답을 보내주는 데이터 센터의 컴퓨터를 말합니다.

#### 9) Rendering

#### 렌더링이란 무엇인가?

리액트에서 UI를 표현하기 위해서 쓴 HTML 표현은 변환하는 작업을 거쳐야 합니다.
이 과정을 렌더링이라고 부릅니다.

렌더링은 서버 또는 클라이언트에서 발생할 수 있습니다. 렌더링은 빌드시간에 일어날 수도 있고 모든 요청마다 일어날 수 있습니다.

Next.js에서는 3가지 렌더링 메서드를 이용할 수 있습니다. **SSR(Server-Side Rendering)** , **SSG(Static Site Generation)** 그리고 **CSR(Client-Side Rendering)** 이 있습니다.

**Pre-Rendering**

SSR과 SSG는 Pre-rendering을 한다고 알려져 있습니다. 왜냐하면 클라이언트에서 결과를 보여주기 전에 외부 데이터를 패칭해서 React 구성 요소를 HTML로 변환하기 때문입니다.

**CSR(Client-Side Rendering) vs Pre-rendering**
일반적인 리액트 앱에서 , 브라우저는 UI를 구성하기 위해 서버로부터 빈 HTML과 JavaScript를 받습니다. 이것은 **CSR**이라고 불리는데 최초 렌더링 할때 유저의 device에서 일어나기 때문입니다.

![](https://nextjs.org/static/images/learn/foundations/client-side-rendering.png)

> **참고** : 만일 Next.js 앱에서 CSR 방식을 선택한다면 React `useEffect`를 사용하거나 [useSWR](https://swr.vercel.app/ko)과 같은 데이터 fetching hook을 사용할 수 있습니다.

반대로 Next.js는 기본적으로 모든 페이지를 **사전 렌더링합니다.** Pre-rendering은 유저 device에서 JavaScript에 의해 모두 수행되는 대신 서버에서 미리 생성됨을 의미합니다.

CSR(Client-Side-rendering)은 렌더링이 끝날때까지 유저는 빈 페이지를 볼 것 입니다. 반대로 Pre-rendering은 유저가 완성된 HTML을 볼 수 있습니다.

![](https://nextjs.org/static/images/learn/foundations/pre-rendering.png)

아래는 Pre-rendering하는 2가지 방식에 대해서 얘기해보겠습니다.

**Server-Side Rendering**

SSR(Server-Side Rendering)에서는 각 요청에 대해 서버에서 HTML 페이지를 만들어줍니다. 생성된 HTML과 , JSON data는 JavaScript에 의해 interactive한 페이지를 만들기 위해 client에게 보내집니다.

Client에서 HTML은 non-interactive 페이지로 빠르게 보여지기 위해 사용된다. 반면에 React는 JSON 데이터와 JavaScript를 interactive한 컴포넌트를 만들기 위해 사용합니다. ( 예) 버튼에 event handler를 붙이기 ) 이 과정을 hydration 이라고 부릅니다.

Next.js에서 [getServerSideProps](https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props)를 사용하여 SSR을 할 수 있습니다.

> **참고** : React18과 Next 12는 **React server components** 의 알파 버전이 도입되었습니다. Server components는 완벽하게 서버에서 렌더되고 , 자바스크립트에 의해 Client-Side에서 요구되지 않습니다. 또한 , Server components는 개발자들에게 서버에서 일부 logic을 허용하고 , Client에게 결과만 보냅니다. 이러한 방식은 클라이언트로 전송되는 번들 크기가 줄고 클라이언트 측 렌더링 성능이 향상됩니다. 여기서 [React server components](https://reactjs.org/blog/2020/12/21/data-fetching-with-react-server-components.html)에 대해 더 알아볼 수 있습니다.

**Static Site Generation**

SSG에서는 SSR과 달리 서버에서 HTML이 생성됩니다. 그리고 내용은 어플리케이션이 배포될 때 빌드 타임에 한번만 생성됩니다. 생성된 HTML은 [CDN](https://nextjs.org/learn/foundations/how-nextjs-works/cdns-and-edge)에 저장되고 매 요청마다 재사용됩니다.

Next.js에서는 [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching/get-static-props)를 사용하여 정적인 페이지를 만듭니다.

> **참고**: [ISR](https://nextjs.org/docs/basic-features/data-fetching/incremental-static-regeneration)은 사이트를 빌드 한 이후에 정적인 페이지를 업데이트하고 생성할 수 있습니다. 이것은 데이터가 변했다면 전체 페이지를 다시 빌드하지 않아도 되는 것을 의미합니다.

Next.js의 장점은 최적의 렌더링 방법을 페이지 마다 정할 수 있습니다. ( SSG , SSR , CSR ) 렌더링 방법을 더 배우려면 [data fetching 문서](https://nextjs.org/docs/basic-features/data-fetching/overview)를 참고해주세요!

다음 챕터에서는 , 배포 후 코드를 저장하거나 실행할 수 있는 위치에 대해서 설명하겠습니다.

#### 10) CDNs and the Edge

#### 네트워크란 무엇인가?

아래 내용은 애플리케이션 코드가 저장되고 네트워크에 배포된 후 실행되는 위치에 대한 정보를 제공합니다.

네트워크를 자원을 공유 가능한 연결된 컴퓨터 ( 또는 서버 )라고 생각할 수 있습니다. Next.js는 **origin servers** , **CDN** , 그리고 **Edge**에 분산시킬 수 있습니다. 각각이 무엇인지 아래에서 살펴보겠습니다.

**Origin servers**

서버는 어플리케이션 코드의 원본 버전을 저장하고 운영할 수 있는 주된 컴퓨터로 알고 있습니다.

Origin server는 다른 어플리케이션 코드 공간 ( CDN servers , Edge servers )과 구분하기 위해 origin 이라는 용어를 사용합니다.

Origin server가 request를 받을때 , response를 보내기 전에 계산을 수행합니다. 이 작업의 결과는 CDN으로 이동할 수 있습니다.

**CDN ( Content Delivery Network )**

CDN은 전세계의 여러 위치에 정적인 컨텐츠( ex . HTML , image files)를 저장하고 클라이언트와 서버 사이에 배치됩니다. 새로운 요청이 왔을때 유저는 cach된 결과를 가까운 CDN에서 받을 수 있습니다.

![](https://nextjs.org/static/images/learn/foundations/cdn.png)

매 요청마다 계산이 일어나지 않기 때문에 origin은 부하가 줄어듭니다. 그리고 지리적으로 가깝기 때문에 유저에게 더 빠른 response를 제공합니다.

Next.js에서는 사전 렌더링을 미리 수행할 수 있으므로 CDN은 작업의 정적 결과를 저장하는 데 적합하고 빠르게 전달합니다.

**The Edge**

Edge는 사용자에게 가장 가까운 네트워크 둘레( or Edge )에 일반화된 개념입니다. CDN은 네트워크 둘레에 정적인 컨텐츠를 저장하기 때문에 Edge에 일부분입니다.

CDN과 유사하게 Edge 서버는 전세계 여러 위치에 분산되어 있습니다. 그러나 정적 컨텐츠를 저장하는 CDN과 달리 Edge 서버는 코드를 실행할 수 있습니다.

이것은 **캐싱**과 **코드 실행** 모두 사용자에게 더 가까운 Edge에서 수행할 수 있음을 의미합니다.

Edge에서 코드를 실행하면 전통적으로 클라이언트 , 서버 측에서 수행됐던 일부 작업을 Edge로 이동할 수 있습니다(ex. [Next js](https://vercel.com/features/edge-functions) ). 이것은 클라이언트에게 보내는 코드의 양이 줄고 사용자의 request가 서버로 다시 돌아갈 필요가 없기 때문에 어플리케이션을 더 우수하게 만듭니다.

Next.js 에서는 [Middleware](https://nextjs.org/docs/advanced-features/middleware)에서 Edge 코드를 실행할 수 있고 , 곧 [React Server Component](https://nextjs.org/docs/advanced-features/react-18/overview#react-server-components-alpha)로 코드를 실행할 수 있습니다.

**추가 자료**

- [https://vercel.com/docs/concepts/edge-network/overview?utm_source=next-site&utm_medium=learnpages&utm_campaign=next-website](https://vercel.com/docs/concepts/edge-network/overview?utm_source=next-site&utm_medium=learnpages&utm_campaign=next-website)

#### 11) Next Steps

#### Next Steps

Next.js 기초 강의를 마친것을 축하드립니다.

Next.js를 계속 배우려면 주요 기능을 소개하는 자습서를 활용하여 첫번째 [Next.js 앱](https://nextjs.org/learn/basics/create-nextjs-app?utm_source=next-site&utm_medium=homepage-cta&utm_campaign=next-website)을 만들어보세요.

[문서](https://nextjs.org/docs/getting-started)를 확인하고 광범위한 [예제 목록](https://nextjs.org/examples)을 탐색할 수 있습니다.

**Join the conversation**

질문이 있다면 , [디스코드](https://discord.gg/bUG2bvbtHy)나 [github Discusstions](https://github.com/vercel/next.js/discussions)에 와서 물어보는 것을 환영합니다!

## Create Your First App

### 1 Create a Next.js App

#### 1) Introduction

리액트로 완전한 웹 애플리케이션을 구축하기 위해서는 고려해야할 몇가지 중요한 세부사항들이 있습니다.

- 코드는 웹팩과 같은 번들러로 번들되어야 하며 바벨과 같은 컴파일러를 사용하여 변환되어야 합니다.
- 코드 분할과 같은 생산 최적화를 해야합니다.
- 성능과 SEO를 위해 일부 페이지를 정적으로 pre-render 하고 싶을 수 있습니다. 서버 사이드 렌더링 또는 클라이언트 사이드 렌더링을 하고 싶을 수 있습니다.
- 리액트액을 데이터 저장소와 연결하기 위해 서버 측 코드를 작성해야 할 수도 있습니다.

프레임워크는 이러한 문제를 해결할 수 있습니다. 그러나 프레임워크는 적절한 수준의 추상화를 가져야 합니다. 그렇지 않을 경우 유용하지 않을 것입니다. 또한 코드를 작성하는 동안 여러분과 여러분의 팀이 놀라운 경험을 할 수 있도록 보장하는 좋은 “Developer Experience(개발자 경험)”을 갖추어야 합니다.

**Next.js : The React Framework**

이제 리액트 프레임워크인 Next.js에 대해 이야기해 봅시다. Next.js는 위의 모든 문제들에 대한 해결책을 제시합니다. 그러나 가장 중요한 점은 리액트 애플리케이션을 구축할 때 여러분과 여러분의 팀이 아주 성공적인 경험을 할 수 있을 것이라는 점입니다.

Next.js는 동급 최고의 개발자 경험을 목표로 하며 다음과 같은 많은 내장 기능을 제공합니다.

- 직관적인 페이지 기반 라우팅 시스템(dynamic routes 포함)
- 페이지 단위로 지원되는 SSR, SSG가 모두 가능한 pre-rendering
- 페이지 로드 속도 향상을 위한 자동 코드 분할
- 최적화된 prefetching을 통한 클라이언트 측 라우팅
- Built-in CSS 와 Sass 지원, CSS-in-JS 라이브러리를 지원
- 빠른 refresh를 지원하는 개발환경
- 서버리스 함수를 사용한 API endpoints를 구축하기 위한 API routes
- 완전한 확장가능성

Next.js는 수많은 세계 최대 브랜드들을 포함한 수만 개의 생산용 웹 사이트와 웹 애플리케이션에서 사용됩니다.

**And This Tutorial**

이 무료 과정은 Next.js를 시작하는 방법을 안내합니다. 이 튜토리얼에서 우리는 간단한 blog app을 만들어보면서 Next.js의 기초를 배울 것입니다.

**[https://next-learn-starter.vercel.app](https://next-learn-starter.vercel.app/)** ([source](https://github.com/vercel/next-learn/tree/master/basics/demo))

> 해당 튜토리얼은 JavaScript와 React대한 기본 지식이 있다는 가정하에 설명하고 있습니다. 리액트 코드를 작성해본 적이 없다면 리액트의 공식 튜토리얼을 먼저 진행해주세요.

튜토리얼 대신 문서를 찾는다면 Next.js의 문서에서 찾을 수 있습니다.

**Join the Conversation**

만약 Next.js나 해당 코스와 관련된 질문이 있으시다면 디스코드에 있는 우리의 커뮤니티에 와서 질문해주세요.

시작합니다!

#### 2) Setup

**Setup**

먼저 개발 환경이 준비되었는지 확인해봐야 합니다.

- Node.js가 설치되어 있지 않다면 [여기서 설치해 주세요.](https://nodejs.org/en/) Node.js 10.13 이후의 버전이 필요합니다.
- 해당 튜토리얼에서는 자체 텍스트 편집기와 터미널 앱을 사용하게 됩니다.

> 만약 윈도우 사용자라면 [downloading Git for Windows](https://gitforwindows.org/)을 다운로드하고 해당 튜토리얼에서 UNIX 관련 명령을 지원하는 Git Bash를 사용하는 것이 좋습니다. [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/install-win10)를 사용해도 좋습니다.

**Create a Next.js app**

Next.js 앱을 만들기 위해서는 터미널을 열고 앱을 만들 디렉토리에 가서 아래의 명령어를 실행해주세요.

```bash
npx create-next-app@latest nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/learn-starter"
```

> 위의 코드는 Next.js 앱을 부팅하는 create-next-app이라는 도구를 사용합니다. —example 플래그를 통해 이 템플릿을 사용할 수 있습니다.
> 해당 기능이 작동하지 않는다면 [이 페이지](https://github.com/vercel/next-learn/blob/master/basics/errors/install.md)에 가서 확인해주세요.

**Run the development server**

여러분은 이제 `nextjs-blog`라는 새로운 디렉토리를 확인할 수 있을 것입니다. `cd` 명령어를 통해 들어가 봅시다.

```bash
cd nextjs-blog
```

그 후 아래의 명령어를 따라해주세요.

```bash
npm run dev
```

이를 통해 여러분은 Next.js 앱의 개발 서버를 3000번 포트에서 시작할 수 있습니다.

해당 기능이 작동하는지 확인하기 위해 브라우저에서 [http://localhost:3000](http://localhost:3000)을 열어주세요.

#### 3) Welcome to Next.js

[http://localhost:3000](http://localhost:3000)에 접근하면 아래와 같은 페이지를 확인하실 수 있습니다. 아래 페이지는 Next.js에 대한 유용한 정보를 보여주는 시작 템플릿 페이지입니다.

![image](https://user-images.githubusercontent.com/95066223/206178836-30554cc9-01af-45fb-8d51-3355e0833e2a.png)

> Help is available : 막히면 [GitHub Discussions](https://github.com/vercel/next.js/discussions)에 있는 커뮤니티에 방문해주세요.

이제 이 페이지를 편집해봅시다.

#### 4) Editing the Page

시작 페이지를 편집해봅시다.

- Next.js 개발 서버가 실행 중인지 확인해주세요.
- 텍스트 편집기에서 `pages/index.js` 파일을 열어주세요.
- `<h1>` 태그 안에 있는 “Welcome to”라는 글자를 찾아서 “Learn”으로 변경해주세요.
- 파일을 저장해주세요.

파일을 저장하면 브라우저가 새로운 글자를 가진 페이지로 자동으로 업데이트 될 것입니다.

![image](https://user-images.githubusercontent.com/95066223/206178790-e63c27bd-3303-4462-b136-d2e5383eddc4.png)

Next.js의 개발 서버는 [Fast Refresh](https://nextjs.org/docs/basic-features/fast-refresh)가 가능합니다. 파일의 변경사항이 있으면 Next.js는 거의 즉시 자동으로 변경사항을 브라우저에 적용합니다. 새로고침을 할 필요가 없습니다! 이 기능은 앱을 빠르게 반복할 수 있도록 도와줍니다.

**Next Up: Creating Pages**

아주 잘했습니다. 첫 번째 시간은 여기까지입니다.

다음 시간에는 더 많은 페이지를 만들어보고 페이지들 간에 이동하는 법에 대해 배울 것입니다.

> 개발 서버를 계속해서 작동시켜주세요. 재시작 하고 싶으시다면 Ctrl + c를 입력하면 종료됩니다.

### 2. Navigate Between Pages

#### 1) Introduction

지금까지 Next.js app 에 하나의 페이지만 있다. 웹사이트들과 웹 어플리케이션들은 일반적으로 다수의 다른 페이지들을 가진다.
application에 더 많은 페이지들을 추가하는 방법을 알아보자.

**What You`ll learn in This Lesson**

이 단원에서 할것:

- 통합 file system routing을 사용하여 새로운 페이지 만들기
- client-side navigation과 페이지들을 잇는 `Link` compoenent 사용법 배우기
- code splitting 과 prefetching을 위한 built-in 지원에 대하여 배우기

> 만약 Next.js routing 에 대한 자세한 문서를 찾는다면 여기를 봐라. routing documentation (차후 링크 필요)

#### 2) Setup

이전 단원부터 계속 진행중이라면 이 페이지를 넘어가도 된다. 아래의 버튼을 클릭해서 다음 페이지로 이동(버튼 없음)

**Download Starter Code(Optional)**

만약 이전 단원부터 진행중이지 않다면 이 단원 아래에 있는 starter code로 다운로드, 설치 그리고 실행할 수 있다. 이 코드는 이전 단원의 결과와 동일한 'nextjs-blog' 디렉토리를 설정한다.

다시 말하지만 이전 단원을 마무리 했다면 이것은 필요치 않다.

```bash
npx create-next-app@latest nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/navigate-between-pages-starter"
```

그런 다음 command output의 명령에 따른다.(`cd` directory 하고 development server 시작)

#### 3) Pages in Next.js

**Pages in Next.js**

Next.js에선 페이지는 `pages` directory에 있는 파일로 부터 exported 된 React Component 이다.

페이지들은 파일이름을 기반으로 된 route와 연결된다. 예를 들어, development에선:

- `pages/index.js` 는 `/` route 와 연결되어있다.
- `pages/posts/first-post.js`는 `/posts/first-post` route 와 연결되어있다.
- 우리는 이미 `pages/index.js` 를 가지고 있어서 `pages/posts/first-post.js` 를 만들고 어떻게 작동하는지 보자.

**Create a New Page**

`pages` 아래에 `posts` directory를 만든다.
아래의 컨텐츠와 함께 `posts` directory안에 `first-post.js` 파일을 만든다.

```js
export default function FirstPost() {
  return <h1>First Post</h1>;
}
```

component는 다른이름을 가질 수 있지만 `default` export를 반드시 해야한다.

지금, development server 가 실행되는지 확인하고 http://localhost:3000/posts/first-post 를 방문하자. 다음 페이지를 볼 수 있다.

![image](https://nextjs.org/static/images/learn/navigate-between-pages/first-post.png)

Next.js에서 다른 페이지를 만들수 있는 방법이다.

간단히 `pages` directory 아래에 JS file을 만들면, 파일의 path가 URL path 가 된다.

어떻게 보면, HTML 또는 PHP 파일들을 사용하여 웹사이트를 구축하는 것과 비슷하다. HTML을 작성하는 대신 JSX를 작성하고 React component를 사용한다.

새롭게 추가된 페이지에 링크를 추가하여 홈페이지로 부터 이동이 가능하도록 하자.

#### 4) Link Component

웹페이지에 페이지들 사이를 연결할때 `<a>` HTML tag를 사용한다.

Next.js는 application에선 `Link` Component `nest/link`를 사용하여 페이지들을 연결 할 수 있다. `<Link>`는 client-side navigation을 할 수 있고, navigation 동작을 통해 더 잘 제어하는 props를 사용할 수 있다.

**Using `<Link>`**

첫번째, `pages/index.js`을 열고, 최상단에 `Link` component from `next/link`를 import 하는 라인을 추가해라.

```js
import Link from "next/link";
```

그리고 나서 아래와 같이 생긴 `h1` tag 를 찾아라:

```js
<h1 className="title">
  Welcome to <a href="https://nextjs.org">Next.js!</a>
</h1>
```

그리고 아래와 같이 변경해라:

```js
<h1 className="title">
  Read <Link href="/posts/first-post">this page!</Link>
</h1>
```

다음, `pages/posts/first-post.js` 열고 아래와 같이 컨텐츠를 변경해라:

```js
import Link from "next/link";

export default function FirstPost() {
  return (
    <>
      <h1>First Post</h1>
      <h2>
        <Link href="/">Back to home</Link>
      </h2>
    </>
  );
}
```

볼 수 있듯이, `Link` component 는 `<a>` tag 들을 사용하는 것과 비슷하지만 `<a href="…">`을 사용하는 대신 `<Link href="…">`를 사용한다.

> Note: Next.js 12.2 버전 이전에는 `<a>` tag를 `<Link>` component를 감싸는 것이 필수였지만 12.2 이상부터는 필수가 아니다.

작동하는지 확인하자. 각 페이지에 링크가 있고, 뒤와 앞으로 이동 할 수 있다.

![image](https://nextjs.org/static/images/learn/navigate-between-pages/links.gif)

#### 5) Client-Side Navigation

`Link` component는 같은 Next.js app 의 두개의 페이지 사이에서 clint-side navigation 할 수 있게 한다.

client-side navation의 의미는 javascript를 사용하여 브라우저가 수행하는 기본적인 navigation 보다 빠른 페이지의 transition(전환)을 일으키는 것을 말한다.

이것을 간단히 증명할 수 있는 간단한 방법:

- 브라우저의 개발 툴을 사용하여 `<html>`의 `background` CSS property를 `yellow`로 바꾼다.
- 두 사이를 링크를 클릭하여 뒤 와 앞으로 이동한다.
- 페이지 전환사이에 노란색 뒷배경이 지속되는 것을 볼 수 있다.

이것은 브라우저가 전체 페이지를 load하지 않고 client-side navigation이 작동하는 것을 보여준다.

![image](https://nextjs.org/static/images/learn/navigate-between-pages/client-side.gif)

만약 `<Link href="…">` 대신 `<a href="…">`을 사용했다면, 브라우저는 full refresh를 하기에 백그라운드 색은 링크 클릭시 지워진다.

**Code splitting and prefetching**

Next.js는 code splitting이 자동적이고, 각 페이지는 그 페이지가 필요할 시에만 로드된다. 홈페이지가 render 되었을 때, 다른 페이지들의 코드는 초기에 전달되지 않는 것을 의미한다.

이 것은 몇백개의 페이지들을 가지고 있어도 홈페이지 로드는 빠르다는 것을 증명한다.

요청한 페이지의 코드만 로딩하는 것은 페이지들이 분리되는 것을 의미한다.
만약 특정 페이지가 error가 나도 나머지 application은 동작한다.

게다가, Next.js의 production build에서는 `Link` compoenents 는 browser의 viewport 안에서 나타날때 마다, Next.js는 자동적으로 백그라운드에서 연결된 페이지들의 코드를 prefetch 한다.
링크를 클릭할때까지 대상 페이지의 코드는 백그라운드에서 로드될 준비를 하고 있고, 페이지 전환은 거의 즉시 된다.

**Summary**

Next.js는 code splitting, client-side navigation, 그리고 prefetching(in production)에 의해 최고의 퍼포먼스를 위한 자동적 최적화를 한다.

`pages` 아래의 파일과 같은 routes를 만들고 내장된 `Link` compoenent를 사용한다. 라우팅 라이브러리들은 필수가 아니다.

` in the API reference for next/link` 에서 `Link` component, `in the routing documentation.`에서 routing을 더 학습 할수 있다.

> Note: 만약 Next.js app 바깥의 외부 페이지 링크가 필요하다면 `<Link>` 없이 `<a>` tag를 사용하면 된다.

### 3. Assets, Metadata, and CSS

#### 1) Introduction

우리가 만든 두 번째 페이즈는 현재 스타일링이 되어있지 않습니다. 페이지에 CSS를 이용해 스타일링을 추가해봅시다!
Next.js는 [CSS](https://nextjs.org/docs/basic-features/built-in-css-support) 와 [Sass](https://nextjs.org/docs/basic-features/built-in-css-support#sass-support) 가 내장되어 있습니다. 이번에는 CSS를 사용할 예정입니다.
이번 강의에서는 Next.js가 이미지 같은 정적 assets과 `<title>` 태그와 같은 페이지의 메타 데이터를 어떻게 다루는지 이야기해 볼 예정입니다.

**What You’ll Learn in This Lesson**

이번 강의에서 배우게 될 내용

- Next.js에 [정적 파일](https://nextjs.org/docs/basic-features/static-file-serving 들을 추가하는 방법
- 각 페이지의 `<head>` 태그 내부를 커스텀하는 방법
- [CSS Modules](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css) 를 사용해서 스타일이 지정된 재사용 가능한 리액트 컴포넌트를 만드는 방법
- `pages/_app.js` 경로에 [global CSS](https://nextjs.org/docs/basic-features/built-in-css-support#adding-a-global-stylesheet)를 추가하는 방
- Next.js에서 스타일링을 하기 위한 몇가지 유용한 팁들

**사전 지식**

- 기본적인 CSS 관련 지식. 이번 강의는 CSS 기초를 설명하는 것이 아닌 Next.js 애플리케이션에서 CSS를 추가하는 방법에 대해서 알아볼 예정입니다.

> 만약 Next.js 스타일링에 대한 자세한 문서를 보고 싶다면, [여기](https://nextjs.org/docs/basic-features/built-in-css-support)를 살펴보세요!

#### 2) Setup

이전 강의부터 계속해서 진행하고 있다면 이 페이지는 넘어가도 됩니다.

**Download Starter Code (Optional)**

만약 이전 강의를 듣지 않았다면, 아래와 같이 코드를 다운받고 실행할 수 있습니다. 이것은 이전 강의와 동일한 내용의 `nextjs-blog` 디렉토리를 설정합니다.
다시 말하지만, 이전 강의를 완료했다면 이 과정을 할 필요가 없습니다.

> $ npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/assets-metadata-css-starter"

설치한 다음 해당 디렉토리로 이동하여 개발 서버를 시작합니다.

#### 3) Assets

**Assets**

Next.js는 이미지와 같은 **static assets** 를 최상위 `public` 디렉토리 아래에서 제공합니다. `public` 폴더 안에 파일들을 `pages` 폴더와 비슷하게 애플리케이션의 root로부터 참조될 수 있습니다.
`public` 폴더는 `robots.txt`, Google SIte Verification 그리고 다른 static assets에도 유용합니다. [Static File Serving](https://nextjs.org/docs/basic-features/static-file-serving)(정적 파일 제공)에 대해서 더 알아보려면 문서를 참고하세요.

**Download Your Profile Picture**

먼저, 프로필 사진을 검색해봅시다.

- Jpg 확장자를 가진 프로필 사진을 다운로드하세요.(또는 [이 파일](https://github.com/vercel/next-learn/blob/master/basics/basics-final/public/images/profile.jpg)을 이용하세요)
- `public` 폴더 안에 `images` 폴더를 만드세요.
- `public/images` 폴더 안에 `profile.jpg` 파일을 저장하세요.
- 이미지의 크기는 약 400 x 400입니다.
- [`public`](https://nextjs.org/docs/basic-features/static-file-serving) 폴더 아래에 존재하는 사용하지 않을 SVG logo를 지울 수 있습니다.

하지만, 이것은 아래 사항을 명시적으로 다뤄줘야 한다는 것을 의미합니다.

- 이미지가 서로 다른 화면 크기에 대응하는지 확인
- 써드파티 툴이나 라이브러리로 최적화되는 이미지인지 확인
- viewport에 들어갔을 때 이미지를 로딩

**Image Component and Image Optimization**

[`next/image`](https://nextjs.org/docs/api-reference/next/image) 는 현대적인 웹을 위해 진화된 `<img>` 태그의 확장입니다.

또한 Next.js는 기본적으로 이미지 최적화를 지원합니다. 이것은 브라우저가 지원하는 경우 resizing, optimizing와 [WebP](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Image_types#webp) 와 같은 현대적인 이미지 포맷를 사용할 수 있습니다. 이러한 기능은 작은 viewport에 큰 이미지가 올라가는 것을 피할 수 있습니다. 또한 Next.js는 자동적으로 향후의 이미지 포맷에 채택하고 해당 이미지 포맷을 지원하는 브라우저에게 제공할 수 있습니다.

자동 이미지 최적화는 어떠한 이미지 파일에도 작동합니다. 이미지가 CMS와 같은 외부 데이터 소스에서 호스팅 될지라도 최적화될 수 있습니다.

**Using the Image Component**

build time에 이미지를 최적화하는 대신에 Next.js는 유저가 요청할 때 이미지 최적화를 진행합니다. 정적 사이트 생성기 또는 정적 솔루션과 달리 10개의 이미지든 1000만개의 이미지를 적재하더라도 build time이 늘어나지 않습니다.

이미지는 기본적으로 지연 로드됩니다. 즉, 표시 영역 외부의 이미지에 대해 페이지 속도가 저하되지 않습니다. 이미지는 화면의 스크롤에 따라 로드됩니다.

이미지는 항상 Google이 [search ranking](https://developers.google.com/search/blog/2020/05/evaluating-page-experience)에 사용하는 [Core Web Vital](https://web.dev/vitals/#core-web-vitals) [Cumulative Layout Shift(누적 레이아웃 이동)](https://web.dev/cls/)을 피하는 방식으로 렌더링됩니다.

여기 [`next/image`](https://nextjs.org/docs/api-reference/next/image)를 사용해 프로필 사진을 보여주는 예시가 있습니다. 넓이와 높이 속성은 이미지의 종횡비가 동일한 원하는 렌더링 사이즈가 되어야 합니다.

> Note: 추후에 "Polishing Layout"에서 이 컴포넌트를 사용할 것이므로 아직 복사할 필요가 없습니다.

```javascript
import Image from "next/image";

const YourComponent = () => (
  <Image
    src="/images/profile.jpg" // Route of the image file
    height={144} // Desired size with correct aspect ratio
    width={144} // Desired size with correct aspect ratio
    alt="Your Name"
  />
);
```

> - 자동 이미지 최적화를 더 살펴보고 싶다면 [여기](https://nextjs.org/docs/basic-features/image-optimization)를 확인하세요.
>
> - `Image` 컴포넌트에 대해 더 살펴보고 싶다면 [여기](https://nextjs.org/docs/api-reference/next/image)를 확인하세요.

#### 4) Metadata

**Metadata**

`<title>` 태그와 같은 페이지 메타 데이터를 수정하려면 어떻게 해야 할까요?

`<title>` 은 `<head>` 태그의 일부분입니다. Next.js 페이지에서 `<head>` 태그를 수정하는 방법에 대해서 알아보도록 하겠습니다.

`page/index.js` 파일을 열고 아래 코드를 찾아보세요.

```react
<Head>
  <title>Create Next App</title>
  <link rel="icon" href="/favicon.ico" />
</Head>
```

소문자 `<head>` 대신 `<Head>`를 사용한 것을 주의하세요. `<Head>` 는 Next.js에 내장된 리액트 컴포넌트입니다. 이 컴포넌트는 페이지의 `<head>`를 수정할 수 있게 해줍니다.

`<Head>` 컴포넌트는 [`next/head`](https://nextjs.org/docs/api-reference/next/head) 모듈에서 불러올 수 있습니다.

**Adding `Head` to `first-post.js`**

`/posts/first-post` 경로에 `<title>`을 추가하지 않았습니다. 한번 추가해봅시다.

`pages/posts/first-post.js` 파일을 열고 [`next/head`](https://nextjs.org/docs/api-reference/next/head) 모듈에서 `<Head>` 컴포넌트를 불러오세요.

```react
import Head from 'next/head';
```

그런 다음, `<Head>` 컴포넌트를 포함한 `<FirstPost>` 컴포넌트를 export 하도록 변경하세요. 지금은 `<title>` 태그만 추가하도록 하겠습니다.

```react
export default function FirstPost() {
  return (
    <>
      <Head>
        <title>First Post</title>
      </Head>
      <h1>First Post</h1>
      <h2>
        <Link href="/">← Back to home</Link>
      </h2>
    </>
  );
}
```

http://localhost:3000/posts/first-post에 접근하세요. 이제 브라우저 탭은 "First Post"를 표시됩니다. 브라우저의 개발자 도구를 사용하면 `<head>` 태그에 `<title>` 태그가 추가된 것을 확인할 수 있습니다.

> - Head Component에 대해서 더 살펴보고 싶다면 [여기](https://nextjs.org/docs/api-reference/next/head)를 확인하세요.
> - 만약 `<lang>` 속성을 추가하는 것처럼 `<html>` 태그를 커스텀하고 싶다면 `pages/_document.js` 파일을 만들어서 이용할 수 있습니다. 자세한 사항을 [여기](https://nextjs.org/docs/advanced-features/custom-document)를 확인하세요.

#### 5) Third-Party JavaScript

**Third-Party JavaScript**

Third-Party JavaScript란 외부 소스에서 추가된 모든 스크립트를 나타냅니다. 일반적으로 분석, 광고 및 고객 지원 위젯과 같이 처음부터 작성할 필요가 없는 최신 기능을 사이트에 도입하기 위해 Third-Party script가 포함됩니다.

**Adding Third-Party JavaScript**

Next.js 페이지에서 Third-Party script를 추가하는 방법에 대해서 알아보겠습니다.

`page/posts/first-post.js` 파일을 열고 아래 코드를 찾아보세요.

```react
<Head>
  <title>First Post</title>
</Head>
```

메타데이터 외에도 가능한 한 빨리 로드하고 실행해야 하는 스크립트는 일반적으로 `<head>`페이지 내에 추가됩니다. 일반 HTML `<script>`요소를 사용하면 다음과 같이 외부 스크립트가 추가됩니다.

```react
<Head>
  <title>First Post</title>
  <script src="https://connect.facebook.net/en_US/sdk.js" />
</Head>
```

이 스크립트에는 Facebook 소셜 플러그인 및 기타 기능을 소개하는 데 일반적으로 사용되는 [Facebook SDK ](https://developers.facebook.com/docs/javascript/quickstart) 가 포함되어 있습니다. 이 접근 방식은 작동하지만 이 방식으로 스크립트를 포함하면 동일한 페이지에서 가져온 다른 JavaScript 코드와 관련하여 언제 로드될지 명확하게 알 수 없습니다. 특정 스크립트가 렌더링을 차단하고 페이지 콘텐츠 로드를 지연시킬 수 있는 경우 성능에 상당한 영향을 미칠 수 있습니다.

**Using the Script Component**

[`next/script`](https://nextjs.org/docs/api-reference/next/script)HTML `<script>`요소의 확장이며 추가 스크립트를 가져와 실행할 때 최적화를 진행합니다.

같은 파일 시작 부분에 아래와 같이 입력합니다.

```react
import Script from 'next/script';
```

이제 `FirstPost` 컴포넌트는 `Script` 컴포넌트를 사용하는 방식으로 바꿔줍니다.

```react
export default function FirstPost() {
  return (
    <>
      <Head>
        <title>First Post</title>
      </Head>
      <Script
        src="https://connect.facebook.net/en_US/sdk.js"
        strategy="lazyOnload"
        onLoad={() =>
          console.log(`script loaded correctly, window.FB has been populated`)
        }
      />
      <h1>First Post</h1>
      <h2>
        <Link href="/">← Back to home</Link>
      </h2>
    </>
  );
}
```

`Script` 컴포넌트에 정의된 몇가지 추가적인 속성이 있습니다.

- `strategy`는 third-party script가 로드되야 하는 시기를 조절합니다. `lazyOnload` 값은 특정 스크립트를 브라우저 idle time동안 지연 로딩되도록 Next.js에게 말해줍니다.
- `onLoad` 는 스크립트 로딩이 끝난 직후 자바스크립트 코드를 실행하는 데 사용합니다. 위 예시에서는 스크립트가 올바르게 로드되었음을 콘솔에 보여주는 메세지를 출력하고 있습니다.

http://localhost:3000/posts/first-post에 접근하세요. 개발자 도구를 사용하면 `Console` 창에 위 메세지가 나온 것을 확인할 수 있습니다. 추가적으로 스크립트가 전역 변수를 채웠는지 확인하기 위해 `window.FB`를 실행할 수 있습니다.

**참고:** Facebook SDK는 제3자 스크립트를 애플리케이션에 효과적인 방식으로 추가하는 방법을 보여주기 위한 고안된 예제로만 사용되었습니다. 이제 Next.js에 third-party functionality를 포함하는 기본 사항을 이해했으므로 `FirstPost`계속하기 전에 스크립트 구성 요소를 제거할 수 있습니다.

> - Script 컴포넌트에 대해 더 살펴보고 싶다면 [여기](https://nextjs.org/docs/basic-features/script)를 확인하세요.

#### 6) CSS Styling

**CSS styling**에 대해서 얘기해보자

index 페이지([http://localhost:3000](http://localhost:3000/))가 이미 styling이 되어 있다는 것을 볼 수 있습니다. 만약 파일 구조를 본다면 , `style` 전역 스타일시트(`global.css`)와 CSS 모듈 (`Home.module.css` )이라는 두 개의 CSS 파일이 있는 폴더가 표시됩니다.

프로젝트에 해당 파일이 없으면 여기에서 시작 코드를 다운로드 할 수 있습니다.

```
npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/assets-metadata-css-starter"
```

**CSS Modules**

[CSS 모듈](https://nextjs.org/docs/basic-features/built-in-css-support)은 unique한 class 이름을 자동적으로 만들고 컴포넌트 level에서 CSS 범위를 로컬로 지정할 수 있습니다. 이것은 다양한 파일에서 클래스 이름의 충돌이 날 것을 걱정하지 않아도 됩니다.

CSS 모듈 외에도 다음과 같은 다양한 방법으로 Next.js 애플리케이션의 스타일을 지정할 수 있습니다.

- Sass는 `.css` 와 `.scss`를 import를 허용합니다.
- PostCSS 라이브러리는 Tailwind CSS와 같습니다.
- CSS-in-JS 라이브러리의 예 ) [styled-jsx](https://github.com/vercel/styled-jsx) , [styled-components](https://github.com/vercel/next.js/tree/canary/examples/with-styled-components) ,[ emotion](https://github.com/vercel/next.js/tree/canary/examples/with-emotion)

이번 챕터에서는 , Next.js에서의 [CSS Modules](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css)과 [Sass](https://nextjs.org/docs/basic-features/built-in-css-support#sass-support)에 대해서 배워보겠습니다.

#### 7) Layout Component

첫째로 , 모든 페이지에 표시되는 **Layout** 컴포넌트를 만들어보자 !

- `Components` 폴더의 최상위에 만듭니다.
- 아래를 따라서 Components 안쪽에 `layout.js` 라는 파일을 만듭니다.

```javascript
export default function Layout({ children }) {
  return <div>{children}</div>;
}
```

그리고 `pages/posts/first-post.js` 파일을 열고 `Layout` 컴포넌트를 import 해서 컴포넌트 가장 바깥쪽에 넣습니다.

```javascript
import Head from "next/head";
import Link from "next/link";
import Layout from "../../components/layout";

export default function FirstPost() {
  return (
    <Layout>
      <Head>
        <title>First Post</title>
      </Head>
      <h1>First Post</h1>
      <h2>
        <Link href="/">← Back to home</Link>
      </h2>
    </Layout>
  );
}
```

#### Adding CSS

`Layout` 컴포넌트에 몇가지의 styles을 추가하겠습니다. [CSS Modules](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css)을 활용하여 리액트 컴포넌트 파일 안에 CSS를 import 할 수 있습니다.

아래의 내용을 `components/layout.module.css` 파일에 작성합니다.

```javascript
.container {
  max-width: 36rem;
  padding: 0 1rem;
  margin: 3rem auto 6rem;
}
```

> 중요 : [CSS Modules](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css)을 사용하기 위해서는 CSS 파일이름을 꼭 `/module.css`로 만듭니다.

`components/layout.js` 안쪽에 `container` 클래스를 사용하기 위해서 필요한 것이 있습니다.

- CSS 파일을 import하고 `styles` 라는 이름을 할당합니다.
- `className`으로 `styles.container`를 사용하세요.

아래 내용을 따라서 `components/layout.js` 파일을 바꿔보세요.

```javascript
import styles from "./layout.module.css";

export default function Layout({ children }) {
  return <div className={styles.container}>{children}</div>;
}
```

[http://localhost:3000/posts/first-post](http://localhost:3000/posts/first-post)에 가보면 , 텍스트가 중앙 container 안쪽에 작성되어 있는 것을 확인할 수 있습니다.

![](https://nextjs.org/static/images/learn/assets-metadata-css/layout.png)

#### Automatically Generates Unique Class Names

지금 브라우저 devtools안에 HTML을 보면 , `Layout` 컴포넌트에 의해 렌더링 된 `div`를 확인할 수 있고 `layout_container_...`라는 class name을 가진 것을 볼 수 있습니다.

![](https://nextjs.org/static/images/learn/assets-metadata-css/devtools.png)

[CSS Modules](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css)은 고유한 class names를 자동적으로 생성합니다. CSS Modules을 사용하는 한 class name 충돌을 걱정할 필요가 없습니다.

게다가 , Next.js는 [CSS Modules](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css) 또한 code splitting 을 합니다. 각 페이지에 최소한의 CSS가 로드되도록 합니다. 그 결과 번들 크기는 더욱 작아집니다.

CSS Modules은 빌드 시 JavaScript 번들에서 추출되며 생성된`.css` 파일은 Next.js에 의해 자동적으로 로드됩니다.

#### 8) Global Styles

#### Global Styles

[CSS modules](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css) 컴포넌트 level에서 유용한 style 입니다. 그러나 **모든 페이지**에 일부 CSS가 로드되는 것을 원한다면 Next.js는 이것 또한 지원하고 있습니다.

어플리케이션에 [global CSS](https://nextjs.org/docs/basic-features/built-in-css-support#adding-a-global-stylesheet)를 로드하는 방법은 아래 내용을 따라서 `pages/_app.js` 파일을 만드세요.

```javascript
export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />;
}
```

`_app.js` 의 default export는 애플리케이션의 모든 페이지를 래핑하는 최상위 수준의 React 컴포넌트입니다. App 컴포넌트는 페이지간에 이동할때 state를 유지할 수 있고 global stlyes 또한 여기서 할 수 있습니다.

[`_app.js` 파일에 대해 더 배워보자](https://nextjs.org/docs/advanced-features/custom-app)

#### Restart the Development Server

**중요** : `pages/_app.js` 를 추가할 때 개발 서버를 재시작 해야합니다. `Ctrl + c` 를 눌러서 서버를 중지시키고 시작하세요.

```
npm run dev
```

#### Adding Global CSS

Next.js에서 [`pages/_app.js`](https://nextjs.org/docs/advanced-features/custom-app)에서 [global CSS](https://nextjs.org/learn/basics/assets-metadata-css/global-styles) 파일을 import 해서 사용할 수 있습니다. 모든 곳에서 global CSS를 import 할 수는 없습니다.

[global CSS](https://nextjs.org/learn/basics/assets-metadata-css/global-styles)가 페이지의 모든 요소에 영향을 끼치기 때문에 `pages/_app.js` 밖에서 import 할 수 없습니다.

만약에 homepage에서 `/posts/first-post` 페이지로 이동해야 한다면 , homepage에 global styles은 의도적이지 않게 `/posts/first-post` 에 영향을 끼칠 것 입니다.

전역 CSS 파일을 어디에나 배치하고 아무 이름이나 사용할 수 있습니다. 아래 내용을 따라 수행해보겠습니다.

- 최상위에 styles 폴더를 만들고 `global.css` 파일을 추가합니다.
- `styles/global.css` 안에 CSS를 추가하세요. 이 코드는 몇몇 스타일을 초기화하고 a 태그의 color를 변경합니다.

```css
html,
body {
  padding: 0;
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen, Ubuntu,
    Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
  line-height: 1.6;
  font-size: 18px;
}

* {
  box-sizing: border-box;
}

a {
  color: #0070f3;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

img {
  max-width: 100%;
  display: block;
}
```

마침내 `pages/_app.js` 파일 안쪽에 사전에 만든 CSS를 import 하세요.

```javascript
// `pages/_app.js`
import "../styles/global.css";

export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />;
}
```

[http://localhost:3000/posts/first-post](http://localhost:3000/posts/first-post)에 접근하면 , style이 적용된 것을 볼 수 있을 것 입니다. `_app.js `에서 import된 모든 스타일은 전역적으로 적용될 것입니다.

![](https://nextjs.org/static/images/learn/assets-metadata-css/global-styles.png)

> 만약에 동작하지 않는다면 개발 서버를 재시작해서 `pages/_app.js` 파일을 업데이트하세요!

#### 9) Polishing Layout

#### Polishing Layout

지금까지는 [CSS Modules](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css)과 같은 개념을 설명하기 위해 최소한의 React 및 CSS 코드만 추가했습니다. 다음 레슨인 [data fetching](https://nextjs.org/docs/basic-features/data-fetching/overview)에 대해 배우기 전에 페이지를 스타일링 해보겠습니다.

#### Update `components/layout.module.css`

첫째로 , `components/layout.module.css`를 열고 아래 내용을 따라서 레이아웃 및 프로필 사진에 대한 세련된 스타일링으로 변경하세요.

```css
.container {
  max-width: 36rem;
  padding: 0 1rem;
  margin: 3rem auto 6rem;
}

.header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.backToHome {
  margin: 3rem 0 0;
}
```

#### Create `styles/utils.module.css`

두번째로 , CSS utility 클래스 집합을 만드는 것은 여러 컴포넌트에서 재사용 가능합니다.

아래 내용을 따라서 `styles/utils.module.css` 라고 불리는 새로운 CSS 파일을 추가합니다.

```css
.heading2Xl {
  font-size: 2.5rem;
  line-height: 1.2;
  font-weight: 800;
  letter-spacing: -0.05rem;
  margin: 1rem 0;
}

.headingXl {
  font-size: 2rem;
  line-height: 1.3;
  font-weight: 800;
  letter-spacing: -0.05rem;
  margin: 1rem 0;
}

.headingLg {
  font-size: 1.5rem;
  line-height: 1.4;
  margin: 1rem 0;
}

.headingMd {
  font-size: 1.2rem;
  line-height: 1.5;
}

.borderCircle {
  border-radius: 9999px;
}

.colorInherit {
  color: inherit;
}

.padding1px {
  padding-top: 1px;
}

.list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.listItem {
  margin: 0 0 1.25rem;
}

.lightText {
  color: #666;
}
```

> `global.css` 파일에서 사용하더라도 Utility 클래스는 어플리케이션 전체에서 재사용 가능합니다. Utility 클래스는 메서드(e.g. global styles , CSS modules , Sass , etc)가 아니라 CSS 선택자를 작성하는 접근 방식으로 나타냅니다. Utility-first CSS에 대해서 자세히 알아보세요.

#### Update components/layout.js

셋째로 , `components/layout.js` 파일을 열고 아래의 내용을 따라 `Your name` 을 실제 이름으로 변경하세요.

```jsx
import Head from "next/head";
import Image from "next/image";
import styles from "./layout.module.css";
import utilStyles from "../styles/utils.module.css";
import Link from "next/link";

const name = "Your Name";
export const siteTitle = "Next.js Sample Website";

export default function Layout({ children, home }) {
  return (
    <div className={styles.container}>
      <Head>
        <link rel="icon" href="/favicon.ico" />
        <meta
          name="description"
          content="Learn how to build a personal website using Next.js"
        />
        <meta
          property="og:image"
          content={`https://og-image.vercel.app/${encodeURI(
            siteTitle
          )}.png?theme=light&md=0&fontSize=75px&images=https%3A%2F%2Fassets.vercel.com%2Fimage%2Fupload%2Ffront%2Fassets%2Fdesign%2Fnextjs-black-logo.svg`}
        />
        <meta name="og:title" content={siteTitle} />
        <meta name="twitter:card" content="summary_large_image" />
      </Head>
      <header className={styles.header}>
        {home ? (
          <>
            <Image
              priority
              src="/images/profile.jpg"
              className={utilStyles.borderCircle}
              height={144}
              width={144}
              alt=""
            />
            <h1 className={utilStyles.heading2Xl}>{name}</h1>
          </>
        ) : (
          <>
            <Link href="/">
              <Image
                priority
                src="/images/profile.jpg"
                className={utilStyles.borderCircle}
                height={108}
                width={108}
                alt=""
              />
            </Link>
            <h2 className={utilStyles.headingLg}>
              <Link href="/" className={utilStyles.colorInherit}>
                {name}
              </Link>
            </h2>
          </>
        )}
      </header>
      <main>{children}</main>
      {!home && (
        <div className={styles.backToHome}>
          <Link href="/">← Back to home</Link>
        </div>
      )}
    </div>
  );
}
```

새로운 기능은 다음과 같습니다.

- 페이지 내용을 묘사하기 위해 사용된 [meta 태그](https://en.wikipedia.org/wiki/Meta_element)( 예. og:image )
- Boolean 값인 `home ` prop은 이미지와 타이틀의 사이즈 조정
- `home `이 false면 하단의 '홈으로 돌아가기' 링크
- `next/image` 로 추가된 이미지는 [priority](https://nextjs.org/docs/api-reference/next/image#priority) 속성으로 preloaded 된다.

#### Update `pages/index.js`

마침내 , homepage를 업데이트합니다.

`pages/index.js` 를 열고 아래 내용으로 바꿉니다.

```jsx
import Head from "next/head";
import Layout, { siteTitle } from "../components/layout";
import utilStyles from "../styles/utils.module.css";

export default function Home() {
  return (
    <Layout home>
      <Head>
        <title>{siteTitle}</title>
      </Head>
      <section className={utilStyles.headingMd}>
        <p>[Your Self Introduction]</p>
        <p>
          (This is a sample website - you’ll be building a site like this on{" "}
          <a href="https://nextjs.org/learn">our Next.js tutorial</a>.)
        </p>
      </section>
    </Layout>
  );
}
```

다음은 작성자 프로필의 예입니다.

![](https://nextjs.org/static/images/learn/assets-metadata-css/example.png)

우리는 layout 코드를 세련되게 바꿨고 우리는 data fetching 레슨을 준비해야 합니다.

이 강의를 마무리하기 전에 다음 페이지에서 Next.js의 CSS 지원과 관련된 몇 가지 유용한 기술에 대해 이야기해 보겠습니다.

#### 10) Styling Tips

다음은 도움이 될 수 있는 몇가지 스타일링 팁이 있습니다.

```
우리가 만든 앱을 변경시키지 않고 아래 섹션을 따라 읽을 수 있습니다.
```

#### Using `clsx` library to toggle classes

[`clsx` ](https://www.npmjs.com/package/clsx)는 클래스 이름을 쉽게 전환할 수 있는 간단한 라이브러리 입니다. `npm install clsx` or `yarn add clsx` 를 사용하여 설치 할 수 있습니다.

자세한 내용은 [설명서](https://github.com/lukeed/clsx)를 참조하세요. 기본 사용법은 다음과 같습니다.

- `type` 이 `success` or `error` 인 `Alert` 컴포넌트를 만드는 것을 원한다고 가정해봅니다.
- 만일 `success`라면 text가 green이고 `error` 라면 text가 red입니다.

아래의 CSS module(`alert.module.css`)을 만들어 봅니다.

```css
.success {
  color: green;
}
.error {
  color: red;
}
```

그리고 `clsx`를 사용합니다.

```jsx
import styles from "./alert.module.css";
import clsx from "clsx";

export default function Alert({ children, type }) {
  return (
    <div
      className={cn({
        [styles.success]: type === "success",
        [styles.error]: type === "error",
      })}
    >
      {children}
    </div>
  );
}
```

#### Customizing PostCSS Config

#### 환경 설정 없이 바로 사용할 수 있는 Next.js는 [PostCSS](https://postcss.org/)를 사용하여 CSS를 컴파일합니다.

PostCSS config를 customize 하기 위해 `postcss.config.js` 파일을 최상위에 만들 수 있습니다. 이는 [Tailwind CSS](https://tailwindcss.com/)와 같은 라이브러리를 사용하는 경우에 유용합니다.

다음은 [Tailwind CSS](https://tailwindcss.com/)를 추가하는 단계입니다. 먼저 패키지를 설치합니다.

```bash
npm install -D tailwindcss autoprefixer postcss
```

그리고 [postcss.config.js](https://nextjs.org/docs/advanced-features/customizing-postcss-config#customizing-plugins)를 만듭니다.

```javascript
// postcss.config.js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};
```

`tailwind.config.js`에 configuring content sources 옵션을 명시하는 것을 추천합니다.

```javascript
// tailwind.config.js
module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
    // For the best performance and to avoid false positives,
    // be as specific as possible with your content configuration.
  ],
};
```

> PostCSS configuration을 custom하는 것에 대해 더 알고 싶다면 PostCSS 공식문서를 확인하세요.

> Tailwind CSS를 쉽게 시작하기 위해 [example](https://github.com/vercel/next.js/tree/canary/examples/with-tailwindcss)을 확인하세요.

#### Using Sass

Next.js는 `.scss` and `.sass` extensions 둘 다 [Sass](https://nextjs.org/docs/basic-features/built-in-css-support#sass-support)를 import 해야합니다. [CSS 모듈](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css) 및 `.module.scss` or `.module.sass` extension을 통해 컴포넌트 level에서 Sass를 사용할 수 있습니다.

Next.js의 내장 Sass 지원을 사용하기 전에 아래와 같이 [`sass`](https://github.com/sass/sass) 를 설치해야합니다.

```bash
npm install -D sass
```

Next.js에 내장되어 있는 CSS Support and CSS Modules을 더 배우고 싶다면 [CSS 문서](https://nextjs.org/docs/basic-features/built-in-css-support)를 확인해주세요.

### 4. Pre-rendering and Data Fetching

#### 1) Introduction

우리는 블로그 페이지를 만들었지만(여기에 [결과가 있습니다](https://next-learn-starter.vercel.app/)) 블로그 내용을 아직 추가하지 못했습니다. 이번 과정에서 우리는 어떻게 외부의 블로그 데이터를 우리의 앱 안으로 들고 와야 할지에 대해 배울 예정입니다. 우리는 파일 시스템에 블로그 내용을 저장할 예정이지만 콘텐츠는 어디에 저장되어 있어도 상관없습니다.(e.g. database 혹은 Headless CMS)

**What You’ll Learn In This Lesson**

이번 과정에서 우리가 배울 내용은 아래와 같습니다:

- Next.js의 [pre-rendering](https://nextjs.org/docs/basic-features/pages#pre-rendering)의 특징
- 두 가지 형태의 pre-rendering:  [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)과 [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)
- [데이터가 있는](https://nextjs.org/docs/basic-features/pages#static-generation-with-data) Static Generation과 [데이터가 없는](https://nextjs.org/docs/basic-features/pages#static-generation-without-data) Static Generation
- [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation) 와 index page에 외부 블로그 데이터를 가져오는 방법
- [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation) 와 관련된 몇가지 유용한 정보

만약 이전 과정부터 이어서 듣고 있다면 이 페이지는 넘어가도 좋습니다. 아래 버튼을 눌러 다음 페이지로 이동해주세요.

#### 2) Setup

만약 이전 과정부터 이어서 듣고 있다면 이 페이지는 넘어가도 좋습니다. 아래 버튼을 눌러 다음 페이지로 이동해주세요.

**Download Starter Code(Optional)**

만약 이전 과정을 듣지 않았다면 아래에 있는 starter code를 다운받고 설치해서 실행해주세요. `nextjs-blog` 폴더는 이전 수업을 잘 들었다면 결과로 가지고 있을 코드입니다.

다시한번 말하지만 지금 하는 작업은 이전 과정을 완료했다면 불필요한 작업입니다.

```bash
npx create-next-app@latest nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/data-fetching-starter"
```

아래의 지시를 따라주세요. (`cd` 명령어를 통해 폴더로 들어가 개발 서버를 시작해주세요.)

그리고 아래의 파일들 또한 업데이트해주세요.

- `public/images/profile.jpg` 에 여러분의 사진을 넣어주세요. (추천: 400px width/height).
- `components/layout.js` 에 있는 `const name = '[Your Name]'` 에 여러분의 이름을 적어주세요.
- `pages/index.js` 에 있는 `<p>[Your Self Introduction]</p>` 에 자기소개를 적어주세요.

#### 3) Pre-Rendering

**Pre-rendering**

[Data fetching](https://nextjs.org/docs/basic-features/data-fetching)에 대해서 이야기 하기 전에 Next.js의 가장 중요한 개념 중에 하나인 [Pre-rendering](https://nextjs.org/docs/basic-features/pages#pre-rendering)에 대해 이야기 해봅시다.

기본적으로 Next.js는 모든 페이지를 사전에 렌더링합니다. 즉 클라이언트 사이드에서 JavaScript가 모든 것을 하는 대신에 Next.js는 사전에 각각의 페이지를 위한 HTML을 생성한다는 뜻입니다. Pre-rendering은 더 좋은 성능과 SEO를 가집니다.

각각의 생성된 HTML은 페이지를 구성하는데 필요한 최소한의 JavaScript로 구성되어 있습니다. 브라우저에 의해 페이지가 로드되면 JavaScript 코드는 실행되며 페이지 전체에 상호작용을 할 수 있도록 만들어줍니다.(이 과정을 hydration이라고 합니다.)

**Check That Pre-rendering Is Happening**

아래와 같은 단계를 통해 pre-rendring이 일어났는지 확인할 수 있습니다.

1. 브라우저에 JavaScript를 비활성화로 설정해주세요. ([Here's how in Chrome](https://developer.chrome.com/docs/devtools/javascript/disable/))
2. [이 페이지](https://next-learn-starter.vercel.app/) 접근에 시도해보세요.(튜토리얼의 최종 결과물입니다.)

여러분은 여러분의 앱이 JavaScript 없이도 렌더링되는 것을 확인할 수 있을 것입니다. Next.js는 정적인 HTML을 사전에 렌더링하므로 JavaScript 실행 없이도 앱의 UI가 화면에 보이는 것을 확인할 수 있습니다.

> 참고 : 위 과정에서 `localhost`에 접속해서 시도해볼수도 있습니다. 하지만 Javascript가 비활성화 되어 있을 경우 CSS는 확인되지 않습니다.

만약 여러분의 앱이 순수한 React.js로 구성되어 있다면(Next.js 없이) pre-rendering은 일어나지 않을 것입니다. 그리고 JavaScript를 비활성화 한다면 여러분의 앱에서는 아무것도 볼 수 없을 것입니다.

예를 들어:

- 브라우저에서 JavaScript를 활성화하고 [이 페이지](https://create-react-template.vercel.app/)를 확인해보세요. 이 페이지는 [Create React App](https://create-react-app.dev/)으로 구축된 순수한 React.js 앱입니다.
- 이제 JavaScript를 비활성화하고 [동일한 페이지](https://create-react-template.vercel.app/)에 다시 접속해보세요.
- 더 이상 앱을 볼 수 없고 대신에 “앱을 실행하려면 JavaScript를 활성화해주세요.”라는 문구를 보실 수 있을 것입니다. 이는 해당 앱이 정적 HTML로 pre-rendering되지 않기 때문입니다.

**Summary: Pre-rendering vs No Pre-rendering**

다음은 그림으로 요약한 것입니다.

![image](https://user-images.githubusercontent.com/95066223/207740356-5c05f70f-7693-41ee-8163-c741d0dcac31.png)
![image](https://user-images.githubusercontent.com/95066223/207740407-304887cd-8ae1-4f8f-bbff-ba537d6b8866.png)

다음으로는 Next.js에서 pre-rendering의 두가지 형태에 대해서 이야기해봅시다.

#### 4) Two Forms of Pre-rendering

Next.js는 [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended) 과 [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)이라는 두 가지 형태의 pre-rendering이 있습니다. 둘의 차이점은 페이지를 위한 HTML을 언제 생성하는 지 입니다.

- [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)은 빌드 타임에 HTML을 생성하는 pre-rendering 메서드입니다. 사전에 생성된 HTML은 매 요청마다 재 요청됩니다.
- [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)은 매 요청 전에 HTML을 생성하는 pre-rendering 메서드입니다.

![image](https://user-images.githubusercontent.com/95066223/207740464-a6eeae30-d57f-45ba-96a5-f649a7d7e619.png)

![image](https://user-images.githubusercontent.com/95066223/207740491-d3242de7-66ba-4685-983b-4f6e909ede99.png)

> 개발모드(npm run dev 혹은 yarn dev 실행 시)에서는 모든 요청에 대해 페이지가 [pre-rendered](https://nextjs.org/docs/basic-features/pages#pre-rendering)됩니다. 이는 Static Generation에도 적용되며 이는 개발을 더 편하게 만들어줍니다. Production으로 이동 시 [Static Generation](https://nextjs.org/docs/basic-features/data-fetching/get-static-props#runs-on-every-request-in-development)은 모든 요청마다 일어나는 게 아니라 빌드 타임에 한번만 실행됩니다.

**Per-page Basis**

중요한 것은 Next.js를 사용하면 각 페이지에 사용할 사전 렌더링 형태를 선택할 수 있다는 점입니다. [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)을 대부분의 페이지에 사용하고 [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)을 다른 페이지에 사용하면 “hybrid” Next.js 앱을 만들 수 있습니다.

![image](https://user-images.githubusercontent.com/95066223/207740544-77702aa1-692f-491e-ae53-3fe8d0204f9f.png)

**When to Use [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended) v.s. [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)**

가능하다면 [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)(데이터의 유무에 상관없이)을 사용하는 것을 추천드립니다. 왜냐하면 여러분의 페이지는 한 번 빌드된 후 CDN에 의해 제공되므로 모든 요청에 대해 서버가 페이지를 렌더링하는 것보다 훨씬 더 빠르기 때문입니다.

[Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)은 다음을 포함한 여러 유형의 페이지에 사용할 수 있습니다.

- 마케팅 페이지
- 블로그 게시물
- E-commerce 제품 목록
- 도움말 및 설명서

“사용자 요청에 앞서 이 페이지를 미리 렌더링할 수 있습니까?”라고 자문해야 합니다. 만약 질문의 답이 예라면 [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)을 선택해야 합니다.

반면에 만약 사용자의 요청 전에 페이지를 사전 렌더링할 수 없다면 [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)은 좋은 선택이 아닙니다. 아마 여러분의 페이지는 데이터를 빈번하게 업데이트하여 보여주고 페이지의 내용은 매 요청마다 바뀔 것입니다.

이 경우에는 [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)을 사용할 수 있습니다. 좀 더 느릴 수 있지만 사전에 렌더링된 페이지는 항상 업데이트 될 것입니다. 혹은 프리 렌더링은 건너뛰고 클라이언트 측 자바스크립트를 사용하여 자주 업데이트되는 데이터를 채울 수 있습니다.

**We’ll Focus in Static Generation**

이 과정에서는 [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)에 집중해서 이야기해 볼 것입니다. 다음 페이지에서는 데이터가 있을 때와 없을 때의 [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)에 대해 이야기 해 볼 예정입니다.

#### 5) Static Generation with and without Data

[Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)은 데이터가 있을 때와 없을 때 모두 구현 가능합니다.

지금까지 우리가 만든 모든 페이지는 외부 데이터를 가지고 올 필요가 없었습니다. 이 페이지들은 production을 위해 앱을 빌드할 때 자동으로 정적으로 생성될 것입니다.

![image](https://user-images.githubusercontent.com/95066223/207740591-8d4aa399-2da6-44c2-939a-162b6cf6f689.png)

하지만 일부 페이지의 경우 먼저 외부 데이터를 가져오지 않고서는 HTML을 렌더링할 수 없습니다. 아마 파일시스템에 접근하거나 외부 API를 가져오거나 빌드 시 데이터베이스 쿼리를 작성해야 할 수 있습니다. Next.js는 이 경우([데이터가 포함된 Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-with-data) )를 즉시 지원합니다.

![image](https://user-images.githubusercontent.com/95066223/207740618-44eedd7b-48cb-4795-884c-55d839c539df.png)

**Static Generation with Data using `getStaticProps`**

어떻게 동작하는 걸까요? Next.js에서는 페이지 컴포넌트를 내보낼 때 getStaticProps라는 비동기 함수도 내보낼 수 있습니다. 이 과정을 진행한다면 아래와 같은 과정이 진행됩니다.

- 프로덕션에서 빌드 타임에 StaticProps를 실행합니다.
- 함수 내부에서 외부 데이터를 가져와 페이지에 props로 보낼 수 있습니다.

```jsx
export default function Home(props) { ... }

export async function getStaticProps() {
  // Get external data from the file system, API, DB, etc.
  const data = ...

  // The value of the `props` key will be
  //  passed to the `Home` component
  return {
    props: ...
  }
}
```

기본적으로 `[getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)`를 사용하면 Next.js에게 다음과 같이 전달할 수 있습니다.. “이 페이지에는 몇 가지 데이터 종속성이 있습니다. 따라서 빌드 시 이 페이지를 pre-render 할 때 먼저 그 문제를 해결하십시오!”

> 참고: 개발 모드에서는 `[getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)`가 각 요청에 대해 대신 실행됩니다.

**Let’s Use `getStaticProps`**

사용하는 것을 배우면 더 쉽게 이해할 수 있을 것입니다. 그럼 다음페이지에서는 [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)를 사용하여 블로그를 구현해보겠습니다.

#### 6) Blog Data

**Creating a simple blog architecture**

블로그 포스터들은 로컬 마크다운 파일들로 어플리케이션 디렉토리에 저장될 것이고, 파일 시스템에서 데이터를 읽을 것이다.
이 섹션에서, 파일 시스템으로부터 마크다운 데이터를 읽는 블로그를 만드는 단계를 살펴보자.

**Creating the markdown files**
루트 폴더에 `posts`라는 top-level 디렉토리를 만든다. `posts` 안에서 두개 파일을 만든다: `pre-rendering.md`, `ssg-ssr.md`
`posts/pre-rendering.md` 에 아래 코드를 복사하자.

```markdown
---
title: "Two Forms of Pre-rendering"
date: "2020-01-01"
---

Next.js has two forms of pre-rendering: **Static Generation** and **Server-side Rendering**. The difference is in **when** it generates the HTML for a page.

- **Static Generation** is the pre-rendering method that generates the HTML at **build time**. The pre-rendered HTML is then _reused_ on each request.
- **Server-side Rendering** is the pre-rendering method that generates the HTML on **each request**.

Importantly, Next.js lets you **choose** which pre-rendering form to use for each page. You can create a "hybrid" Next.js app by using Static Generation for most pages and using Server-side Rendering for others.
```

`posts/ssg-ssr.md`에 아래 코드를 복사하자

```markdown
---
title: "When to Use Static Generation v.s. Server-side Rendering"
date: "2020-01-02"
---

We recommend using **Static Generation** (with and without data) whenever possible because your page can be built once and served by CDN, which makes it much faster than having a server render the page on every request.

You can use Static Generation for many types of pages, including:

- Marketing pages
- Blog posts
- E-commerce product listings
- Help and documentation

You should ask yourself: "Can I pre-render this page **ahead** of a user's request?" If the answer is yes, then you should choose Static Generation.

On the other hand, Static Generation is **not** a good idea if you cannot pre-render a page ahead of a user's request. Maybe your page shows frequently updated data, and the page content changes on every request.

In that case, you can use **Server-Side Rendering**. It will be slower, but the pre-rendered page will always be up-to-date. Or you can skip pre-rendering and use client-side JavaScript to populate data.
```

> `title` 과 `date`과 상단에 포함된 metadata 섹션을 가진 마크다운 파일이란걸 알 수 있을 것이다. 이것을 [gray-matter](https://github.com/jonschlinkert/gray-matter) 라이브러리를 사용해서 parse할 수 있는 [YAML](https://ko.wikipedia.org/wiki/YAML) Front Matter이라고 부른다.

**Installing gray-matter**

각각의 마크다운 파일에서 metadata 를 parse 하는 [gray-matter](https://github.com/jonschlinkert/gray-matter) 를 install하자.

```zsh
npm install gray-matter
```

**Creating the utility function to read the file system**

다음으로, file system에서 parsing data 를 위한 utility function 을 만들자. utility function 을 사용해서 다음을 수행한다.

- 각 markdown 파일을 parse해서 `title`, `date`, 파일 이름을 얻는다.(파일이름은 post URL에 `id` 로 사용된다)
- index page에 날짜로 정렬한 data를 리스트한다.

root 디렉토리에 `lib` 이라는 top-level 디렉토리를 만든다. `lib` 디렉토리 안에 `posts.js`라는 파일을 만들고 아래 코드를 복사해서 붙여넣자:

```js
import fs from "fs";
import path from "path";
import matter from "gray-matter";

const postsDirectory = path.join(process.cwd(), "posts");

export function getSortedPostsData() {
  // Get file names under /posts
  const fileNames = fs.readdirSync(postsDirectory);
  const allPostsData = fileNames.map((fileName) => {
    // Remove ".md" from file name to get id
    const id = fileName.replace(/\.md$/, "");

    // Read markdown file as string
    const fullPath = path.join(postsDirectory, fileName);
    const fileContents = fs.readFileSync(fullPath, "utf8");

    // Use gray-matter to parse the post metadata section
    const matterResult = matter(fileContents);

    // Combine the data with the id
    return {
      id,
      ...matterResult.data,
    };
  });
  // Sort posts by date
  return allPostsData.sort((a, b) => {
    if (a.date < b.date) {
      return 1;
    } else {
      return -1;
    }
  });
}
```

> Note:
> learn Next.js 위해 코드의 실행부분을 이해할 필요는 없다. 함수는 블로그 예제 함수적으로 만드는 것이다. 그러나 만약 더 알고 싶다면:
>
> - `fs`는 file system에서 파일들을 읽을 수 있는 Node.js module 이다.
> - `path`는 file paths를 다루는 Node.js module이다.
> - `matter`는 각 마크다운 파일에서 metadata를 parse 하는 라이브러리다.
> - Next.js 에서 `lib` 폴더는 `pages` 폴더처럼 배정되어있는 폴더가 아니고, 어떤것이든 이름으로 만들 수 있다. 보통 컨벤션은 `lib` 또는 `utils` 을 사용한다1.

**Fetching the blog data**

블로그 데이터는 parse 했고, index page에 추가해야 한다. `getStaticProps()`라는 Next.js data fetching method를 사용하여 할 수 있다. 다음 섹션에서는 `getStaticProps()` 실행하는 방법을 배운다.
![image](https://nextjs.org/static/images/learn/data-fetching/index-page.png)

#### 7) Implement getStaticProps

**Pre-rendering in Next.js**

Next.js는 pre-rendering의 투가지 폼을 가지고 있다: Static Generation, Server-side Rendering.
다른점은 HTML 페이지들이 생성 되는 때이다.

- Static Generation은 build 타임에 HTML을 생성하는 pre-rendering method 이다. pre-rendered HTML은 각 요청 시 다시 사용한다.
- Server-side Rendering 은 각 요청때마다 HTML을 만드는 pre-rendering method 이다.

중요한건, Next.js는 각 페이지마다 사용할 pre-redering form을 선택할 수 있다. 대부분의 페이지에 Static Generation 사용하고, 남은 페이지에 Server-side Rendering 을 사용해서 "hybrid" Next.js app 을 만들 수 있다.

**Using Static Generation (`getStaticProps()`)**

`getSortedPostsData`를 import하고, `pages/index.js`에서 `getStaticProps`을 사용한다.
에디터에서 `pages/index.js`을 열고, 아래 코드를 exported `Home` component 위에 추가하자.

```js
import { getSortedPostsData } from "../lib/posts";

export async function getStaticProps() {
  const allPostsData = getSortedPostsData();
  return {
    props: {
      allPostsData,
    },
  };
}
```

`getStaticProps`에 `props` object안에 `allPostsData`를 리턴함으로서, 블로그 포스트들은 `Home` component에 props처럼 넘길수 있다. 블로그 포스트들을 아래와 같이 접근할 수 있다.

```js
export default function Home ({ allPostsData }) { ... }
```

블로그 포스트들을 표시하기 위해, `Home` component는 업데이트 하여, 자기 소개가 있는 section 아래 데이터가 있는 다른 `<section>` tag는 추가해보자. props가 `()` 에서 `({allPostsData})`로 변경되는 것도 잊지말자.

```js
export default function Home({ allPostsData }) {
  return (
    <Layout home>
      {/* Keep the existing code here */}

      {/* Add this <section> tag below the existing <section> tag */}
      <section className={`${utilStyles.headingMd} ${utilStyles.padding1px}`}>
        <h2 className={utilStyles.headingLg}>Blog</h2>
        <ul className={utilStyles.list}>
          {allPostsData.map(({ id, date, title }) => (
            <li className={utilStyles.listItem} key={id}>
              {title}
              <br />
              {id}
              <br />
              {date}
            </li>
          ))}
        </ul>
      </section>
    </Layout>
  );
}
```

만약 http://localhost:3000에 접속하면 블로그 데이터를 볼수 있을 것이다.

![image](https://nextjs.org/static/images/learn/data-fetching/blog-data.png)

축하한다. 성공적으로 외부 데이터를 패치하고, 데이터와 함께 index 페이지를 pre-rendered 했다.

![image](https://nextjs.org/static/images/learn/data-fetching/index-page.png)

다음페이지에서 `getStaticProps`을 사용하는 팁들에 대하여 애기해보자.

#### 8) getStaticProps Details

`getStaticProps`에 대해 알아야하는 필수 정보들이 여기 있다.

**Fetch External API or Query Database**

`lib/posts.js`에서, file system에서 data를 fetch하는 `getSortedPostsData`를 실행했다.

```js
export async function getSortedPostsData() {
  // Instead of the file system,
  // fetch post data from an external API endpoint
  const res = await fetch("..");
  return res.json();
}
```

> Note: Next.js는 클라이언트와 서버 둘다에서 `fetch()`를 polyfill 한다. 이것을 import 할 필요 없다.

database를 직접적으로 query 할수도 있다.

```js
import someDatabaseSDK from 'someDatabaseSDK'

const databaseClient = someDatabaseSDK.createClient(...)

export async function getSortedPostsData() {
  // Instead of the file system,
  // fetch post data from a database
  return databaseClient.query('SELECT posts...')
}
```

이것은 `getStaticProps`가 오직 server-side에서 실행되기 때문에 가능하다. client-side에서는 절대 실행되지 않는다. 브라우저에 JS bundle이 포함되어 있지 않다.
이것의 의미는 브라우저로 보내지 않고도 직접적으로 database 쿼리들과 같은 코드들을 사용할 수 있다.

**Development vs. Production**

- development(`npm run dev` 또는 `yarn dev`) 에서는 `getStaticProps`는 모든 요청에 실행된다.
- production에서는 `getStaticProps`는 build time에서만 실행된다. 그러나 이 행위는 `getStaticPaths`에 의해 리턴된 `fallback` [key](https://nextjs.org/docs/api-reference/data-fetching/get-static-paths#fallback-false)을 사용하여 향상 될 수 있다.

그 이유는 빌드 타임에 실행되기 때문에 query parameters나 HTTP header 와 같은 요청 시간에 사용가능한 데이터는 사용하는 것이 가능하지 않다.

**Only Allowed in a Page**

`getStaticProps`는 오직 페이지에서만 export할 수 있다. 페이지가 아닌 파일에서는 export 할 수 없다.

이 제한의 이유중 하나는 페이지가 렌더 되기전에 React에 필요한 모든 데이터가 필수이기 때문이다.

**What If I Need to Fetch Data at Request Time?**

[Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)이 빌드타임에 한번 일어난 이후에, 자주 업데이트되거나 모든 유저의 요청에 변하는 데이터는 알맞지 않다.

변하는 데이터와 같은 곳의 경우에는 [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)을 사용할 수 있다.
다음 섹션에서 server-side rendering에 대하여 학습하자.

#### 9) Fetching Data at Request Time

만약 빌드 타임 대신 리퀘스트 타임에 데이터 fetch가 필요하다면 [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)을 사용해 볼 수 있다:

![image](https://nextjs.org/static/images/learn/data-fetching/server-side-rendering-with-data.png)

[Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)을 사용하기 위해, 페이지에서 [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation) 대신 [getServerSideProps](https://nextjs.org/docs/basic-features/data-fetching#getserversideprops-server-side-rendering)을 export 해야한다.

**Using `getServerSideProps`**
[getServerSideProps](https://nextjs.org/docs/basic-features/data-fetching#getserversideprops-server-side-rendering)을 위한 코드이다. 블로그 예제에서는 필요치 않아서, 이것을 실행하지는 않는다.

```js
export async function getServerSideProps(context) {
  return {
    props: {
      // props for your component
    },
  };
}
```

`getServerSideProps`를 요청 시간에 호출되기 때문에, 이것의 파라미터 {`context`}에는 요청별 특수한 파라미터가 포함되어 있다.

요청 시간에 데이터가 반드시 fetch가 되는 페이지를 pre-rendering하는 경우에만 `getServerSideProps`을 사용해야한다.
첫번째 바이트까지의 시간([TTFB](https://web.dev/time-to-first-byte/))은 `getStaticProps`보다 느린데, 모든 리퀘스트에 서버는 결과를 계산해야하고, 결과는 별도의 설정없이는 CDN에 의해 캐쉬되지 않기 때문이다.

**Client-side Rendering**
pre-render data가 필요없다면, 다음 전략을 사용할수도 있다.([Client-side Rendering](https://nextjs.org/docs/basic-features/data-fetching#fetching-data-on-the-client-side))

- 외부 데이터가 필수적이지 않은 페이지들의 부분들을 고정적으로 생성한다(pre-render)
- page가 로드될때, javascript을 사용하는 클라이언트로 부터 외부 데이터를 fetch하고 나머지 부분들을 채운다.

![image](https://nextjs.org/static/images/learn/data-fetching/client-side-rendering.png)

이런 접근 방식은 사용자 대쉬보드 페이지, 예제들에 적합하다. 그 이유는 대쉬보드는 개인적이고, 사용자별 페이지 이고, SEO가 적절하지 않고, pre-render 될 필요가 없는 페이지 이기 때문이다.
이런 데이터는 자주 업데이트 되어서, 요청시간에 데이터 fetching이 필수이다.

**SWR**
Next.js 팀은 SWR이라고 부르는 data fetching에 필요한 React hook을 만들었다. 클라이언트 사이드에서 데이터 패칭을 한다면 강력 추천힌디/
caching, revalidation, focus tracking, 일정 간격 refetching 등을 제어할 수 있다. 여기서 자세한 것은 다루지 않으나, 다음은 사용 예이다.

```js
import useSWR from "swr";

function Profile() {
  const { data, error } = useSWR("/api/user", fetch);

  if (error) return <div>failed to load</div>;
  if (!data) return <div>loading...</div>;
  return <div>hello {data.name}!</div>;
}
```

[SWR documentation](https://swr.vercel.app/ko) 을 더 학습하기 위해 확인해라.

**That’s It!**
다음 학습에서는 dynamic routes 를 사용하여 각 블로그 게시물을 위한 페이지들을 만들자.

> [Data Fetching documentation](https://nextjs.org/docs/basic-features/data-fetching) 에서 [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)와 [getServerSideProps](https://nextjs.org/docs/basic-features/data-fetching#getserversideprops-server-side-rendering)에 대하여 더 깊은 정보를 얻을 수 있다.

### 5. Dynamic Routes

#### 1) Introduction

블로그 데이터로 index 페이지를 채웠지만 아직 개별 블로그 페이지를 만들지 않았습니다( [원하는 결과](https://next-learn-starter.vercel.app/) 는 다음과 같습니다 ). 우리는 이러한 페이지의 URL이 블로그 데이터에 의존하기를 원합니다. 다시 말해, [dynamic routes(동적 경로)](https://nextjs.org/docs/routing/dynamic-routes) 를 사용해야 합니다 .

**What You’ll Learn in This Lesson**

이번 강의에서 배울 내용

- [`dynamic routes`](https://nextjs.org/learn/basics/dynamic-routes)를 이용하는 [`getStaticPaths`](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticpaths-static-generation) 를 사용해서 정적인 페이지를 만드는 방법
- [`getStaticProps`](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticprops-static-generation)를 통해 각각의 블로그 포스트에 맞는 데이터를 가져오기 위해 작성하는 방법
- [`remark`](https://github.com/remarkjs/remark)를 사용해 마크다운을 렌더링하는 방법
- date 문자열을 이쁘게 출력하는 방법
- [`dynamic routes`](https://nextjs.org/learn/basics/dynamic-routes) 가 있는 페이지에 연결하는 방법
- [`dynamic routes`](https://nextjs.org/learn/basics/dynamic-routes)에 관한 몇가지 유용한 정보

#### 2) Setup

이전 강의부터 계속해서 진행하고 있다면 이 페이지는 넘어가도 됩니다.

**Download Starter Code (Optional)**

만약 이전 강의를 듣지 않았다면, 아래와 같이 코드를 다운받고 실행할 수 있습니다. 이것은 이전 강의와 동일한 내용의 `nextjs-blog` 디렉토리를 설정합니다.
다시 말하지만, 이전 강의를 완료했다면 이 과정을 할 필요가 없습니다.

> $ npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/assets-metadata-css-starter"

설치한 다음 해당 디렉토리로 이동하여 개발 서버를 시작합니다.

#### 3) Page Path Depends on External Data

이전 강의에서는 **페이지의 콘텐츠** 가 외부 데이터에 의존하는 경우를 다루었습니다. 인덱스 페이지를 렌더링하는 데 필요한 데이터를 [`getStaticProps`](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)를 통해 가져오곤 했습니다 

이번 강의에서는 페이지의 경로가 외부 데이터에 의존하는 경우에 대해서 다뤄보겠습니다. Next.js는 외부 데이터에 의존하는 경로를 가진 페이지를 정적으로 생성하는 것을 가능하게 해줍니다. 이것은 Next.js 내에서 동적 URL이 가능하도록 만들어줍니다.

<img src="https://nextjs.org/static/images/learn/dynamic-routes/page-path-external-data.png" />

#### How to Statically Generate Pages with Dynamic Routes

우리의 경우 블로그 게시물에 대한 [동적 경로](https://nextjs.org/docs/routing/dynamic-routes)를 만드려고 합니다.

- 우리는 각 게시물이  `/posts/<id>` 경로를 갖기를 원합니다. 여기서 `<id>`는 최상위 `posts`디렉토리 아래의 마크다운 파일 이름입니다.
- 우리는 `ssg-ssr.md`, `pre-rendering.md`가 있으므로 경로가 `/posts/ssg-ssr`과 `/posts/pre-rendering` 가 되었으면 합니다

#### Overview of the Steps

다음 단계에서 이 모든 것을 할 수 있지만 다음 페이지에서 해볼 것이니 아직 할 필요는 없습니다. 

먼저 `/pages/posts` 아래에 `[id].js`라고 불리는 페이지는 만들겠습니다. `[]` 로 감싸진 경로는 Next.js가 안의 [동적 경로](https://nextjs.org/docs/routing/dynamic-routes)입니다. 

`pages/posts/[id].js` 안에서 이전에 만들었던 다른 페이지들과 동일하게 페이지를 렌더링하는 코드를 작성합니다.

```react
import Layout from '../../components/layout';

export default function Post() {
  return <Layout>...</Layout>;
}
```

자 이제 여기서 새로운 것이 등장합니다. 우리는 [`getStaticPaths`](https://nextjs.org/docs/basic-features/data-fetching#getstaticpaths-static-generation) 라고 불리는 비동기 함수를 내보낼 것입니다. 이 함수에서는 `id`가 될 수 있는 배열을 반환해야만 합니다.

```react
import Layout from '../../components/layout';

export default function Post() {
  return <Layout>...</Layout>;
}

export async function getStaticPaths() {
  // Return a list of possible value for id
}
```

그리고 마지막으로  [`getStaticProps`](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation) 를 다시 한 번 수행할 필요가 있습니다 - 이 시간 동안 주어진 `id`를 가지고 블로그 게시물에 필요한 데이터를 받아옵니다. 파일 이름이 `[id].js` 이기 때문에   [`getStaticProps`](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation) 는 `id` 를 포함한 `params`를 전달받습니다. 

```react
import Layout from '../../components/layout';

export default function Post() {
  return <Layout>...</Layout>;
}

export async function getStaticPaths() {
  // Return a list of possible value for id
}

export async function getStaticProps({ params }) {
  // Fetch necessary data for the blog post using params.id
}
```

방금 이야기한 내용을 그림으로 보여주면 아래와 같습니다.

<img src="https://nextjs.org/static/images/learn/dynamic-routes/how-to-dynamic-routes.png" />

#### 4) Implement getStaticPaths

먼저, 파일을 세팅하겠습니다.

- `pages/posts` 폴더 내부에 `[id].js` 로 파일을 생성하세요.
- 또한 `pages/posts` 폴더 내부에  더이상 사용하지 않을  `first-post.js` 를 제거하세요.

그런 다음 에디터를 열어 아래 코드를 붙여넣으세요. `...` 으로 된 부분은 추후에 채워넣을 것입니다.

```react
import Layout from '../../components/layout';

export default function Post() {
  return <Layout>...</Layout>;
}
```

그런 다음, `lib/posts.js` 파일을 열고 하단의 `getAllPostIds` 함수를 추가하세요. 이 함수는 `posts` 폴더 내에서 `.md`를 포함한 파일 이름 배열을 반환해줄 것입니다.

```react
export function getAllPostIds() {
  const fileNames = fs.readdirSync(postsDirectory);

  // Returns an array that looks like this:
  // [
  //   {
  //     params: {
  //       id: 'ssg-ssr'
  //     }
  //   },
  //   {
  //     params: {
  //       id: 'pre-rendering'
  //     }
  //   }
  // ]
  return fileNames.map((fileName) => {
    return {
      params: {
        id: fileName.replace(/\.md$/, ''),
      },
    };
  });
}
```

**중요** : 반환된 목록은 단순한 문자열 배열이 아니라 위 주석처럼 보이는 객체 배열이어야 합니다 .  각 개체에는 `params` 키가 있어야 하며 파일 이름에 `id`사용하기 때문에 `id` 키가 있는 개체를 포함 해야 합니다. 그렇지 않으면 `getStaticPaths`는 정상적으로 동작하지 않습니다.

마지막으로 `getAllPostIds`를 가져와 [`getStaticPaths`](https://nextjs.org/docs/basic-features/data-fetching#getstaticpaths-static-generation) 내부에서 사용합니다. `pages/posts/[id].js` 를 열고 아래의 코드를 붙여넣습니다.

```react
import { getAllPostIds } from '../../lib/posts';

export async function getStaticPaths() {
  const paths = getAllPostIds();
  return {
    paths,
    fallback: false,
  };
}
```

- `paths`는 `pages/posts/[id].js` 에 정의된 `params`를 포함한  `getAllPostIds`가 반환하는 알려진 경로 배열을 반환합니다.  보다 자세한 내용은 [여기](https://nextjs.org/docs/basic-features/data-fetching/overview#the-paths-key-required)를 참고하세요.
-  [`fallback: false` ](https://nextjs.org/docs/basic-features/data-fetching/overview#fallback-false)는 당장은 무시하셔도 됩니다. 추후에 자세히 학습할 예정입니다.

거의 다 했지만 [`getStaticProps`](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation) 수행해야할 필요가 있습니다. 다음 장에서 진행하겠습니다!

#### 5) Implement getStaticProps

우리는 주어진 `id`를 가진 페이지를 렌더링하기 위한 필수 데이터를 가져와야할 필요가 있습니다.

그렇게 하기 위해 `lib/posts.js` 안에 아래의 `getPostData` 함수를 추가해줍니다. 이 함수는 `id`에 기반하여 게시물 데이터를 반환해줄 것입니다.

```react
export function getPostData(id) {
  const fullPath = path.join(postsDirectory, `${id}.md`);
  const fileContents = fs.readFileSync(fullPath, 'utf8');

  // Use gray-matter to parse the post metadata section
  const matterResult = matter(fileContents);

  // Combine the data with the id
  return {
    id,
    ...matterResult.data,
  };
}
```

그런 다음 `pages/posts/[id].js`를 열고 해당 라인을 변경합니다.

```react
import { getAllPostIds } from '../../lib/posts';
```

```react
import { getAllPostIds, getPostData } from '../../lib/posts';

export async function getStaticProps({ params }) {
  const postData = getPostData(params.id);
  return {
    props: {
      postData,
    },
  };
}
```

현재 게시글 페이지는 게시글 데이터를 받아오기 위해 `getStaticProps` 함수 내에서 `getPostData` 함수를 사용하고 있고 이는 `props`로 반환될 것입니다.

자, `Post` 컴포넌트를 `postData`를 사용하도록 바꿔봅시다. `pages/posts/[id].js` 안에서 `Post` 컴포넌트를 아래와 같이 변경해줍니다.

```react
export default function Post({ postData }) {
  return (
    <Layout>
      {postData.title}
      <br />
      {postData.id}
      <br />
      {postData.date}
    </Layout>
  );
}
```

아래 사이트에서 결과를 확인해보세요.

- http://localhost:3000/posts/ssg-ssr
- http://localhost:3000/posts/pre-rendering

여러분은 각각의 페이지에서 블로그 데이터를 확인할 수 있어야 합니다.

<img src="https://nextjs.org/static/images/learn/dynamic-routes/blog-data-post-page.png" />

훌륭합니다. 우리는 성공적으로 [동적 경로](https://nextjs.org/docs/routing/dynamic-routes)를 생성했습니다.

#### Something Wrong?

만약 오류가 발생했다면 코드를 정확히 입력했는지 확인해보세요.

- `pages/posts/[id].js`를 [이것](https://github.com/vercel/next-learn/blob/master/basics/dynamic-routes-step-1/pages/posts/%5Bid%5D.js)과 같아야 합니다.
- `lib/posts.js` 는 [이것](https://github.com/vercel/next-learn/blob/master/basics/dynamic-routes-step-1/lib/posts.js)과 같아야 합니다.
- 여전히 오류가 발생한다면, 다른 코드가 [이것](https://github.com/vercel/next-learn/tree/master/basics/dynamic-routes-step-1)과 같아야 합니다.

그래도 안된다면  [GitHub Discussions](https://github.com/vercel/next.js/discussions) 커뮤니티에 말해주세요. 다른 사람들이 볼 수 있도록 코드를 GitHub에 푸시하고 링크할 수 있다면 도움이 될 것입니다.

다시 말해, 우리가 수행한 것을 그림으로 요약하면 아래와 같습니다.

<img src="https://nextjs.org/static/images/learn/dynamic-routes/how-to-dynamic-routes.png" />

우리는 여전히 마크다운 컨텐츠를 블로그에 보여주고 있지 않습니다. 다음 장에서 해봅시다.



#### 6) Render Markdown

마크다운 컨텐츠를 렌더하기 위해서는 `remark` 라이브러리를 사용해야합니다. 우선 , 설치를 진행합니다.

```bash
npm install remark remark-html
```

그리고 `lib/posts.js`를 열고 파일 최상위에 아래를 imports 합니다.

```javascript
import { remark } from "remark";
import html from "remark-html";
```

`remark`를 사용하기 위해서 같은 파일에 `getPostData()` 함수를 update 합니다.

```javascript
export async function getPostData(id) {
  const fullPath = path.join(postsDirectory, `${id}.md`);
  const fileContents = fs.readFileSync(fullPath, "utf8");

  // Use gray-matter to parse the post metadata section
  const matterResult = matter(fileContents);

  // Use remark to convert markdown into HTML string
  const processedContent = await remark()
    .use(html)
    .process(matterResult.content);
  const contentHtml = processedContent.toString();

  // Combine the data with the id and contentHtml
  return {
    id,
    contentHtml,
    ...matterResult.data,
  };
}
```

> **중요** : 우리는 `remark`에 `await`을 사용하기 위해 getPostData에 **async **키워드를 사용해야 합니다. 비동기로 data를 fetch하기 위해 `async/await`이 필요합니다.

`pages/posts/[id].js` 에 [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticprops-static-generation)안에 `getPostData`를 부를때 `await`을 사용합니다.

```javascript
export async function getStaticProps({ params }) {
  // Add the "await" keyword like this:
  const postData = await getPostData(params.id);

  return {
    props: {
      postData,
    },
  };
}
```

마침내 , [`dangerouslySetInnerHTML` ](https://reactjs.org/docs/dom-elements.html#dangerouslysetinnerhtml)을 사용하여 `pages/posts/[id].js` 에 `contentHtml`을 렌더하여 Post 컴포넌트를 업데이트 할 수 있습니다.

```javascript
export default function Post({ postData }) {
  return (
    <Layout>
      {postData.title}
      <br />
      {postData.id}
      <br />
      {postData.date}
      <br />
      <div dangerouslySetInnerHTML={{ __html: postData.contentHtml }} />
    </Layout>
  );
}
```

다음 페이지를 다시 방문하세요 :

- [http://localhost:3000/posts/ssg-ssr](http://localhost:3000/posts/ssg-ssr)
- [http://localhost:3000/posts/pre-rendering](http://localhost:3000/posts/pre-rendering)

이제 블로그 컨텐츠가 표시됩니다.

![](https://nextjs.org/static/images/learn/dynamic-routes/markdown.png)

거의 끝났고 다음 페이지를 다듬어 보겠습니다.

#### 7) Polishing the Post Page

#### Polishing the Post Page

**Post 페이지에 `title` 추가하기**

`pages/posts/[id].js` 안에서 `title` 태그를 추가해보세요. `next/head`를 파일 최상위에 import 하고 Post 컴포넌트에 `title` 태그를 추가합니다.

```javascript
// Add this import
import Head from "next/head";

export default function Post({ postData }) {
  return (
    <Layout>
      {/* Add this <Head> tag */}
      <Head>
        <title>{postData.title}</title>
      </Head>

      {/* Keep the existing code here */}
    </Layout>
  );
}
```

**날짜 포맷팅**

날짜를 포맷하기 위해 , [`date-fns`](https://date-fns.org/) 라이브러리를 사용할 것입니다. 먼저 아래를 따라 설치합니다.

```bash
npm install date-fns
```

`components/date.js` 파일을 만들고 아래를 따라서 Date 컴포넌트의 내용을 추가합니다.

```javascript
import { parseISO, format } from "date-fns";

export default function Date({ dateString }) {
  const date = parseISO(dateString);
  return <time dateTime={dateString}>{format(date, "LLLL d, yyyy")}</time>;
}
```

> **참고** : [date-fns](https://date-fns.org/v2.16.1/docs/format) 웹사이트에서 `format()` string 옵션과 관련된 다양한 것들을 볼 수 있습니다.

이제 `pages/posts/[id].js` 파일을 열고 `Date` 컴포넌트를 최상위에 import하고 `{postData.date}`를 사용합니다.

```javascript
// Add this import
import Date from "../../components/date";

export default function Post({ postData }) {
  return (
    <Layout>
      {/* Keep the existing code here */}

      {/* Replace {postData.date} with this */}
      <Date dateString={postData.date} />

      {/* Keep the existing code here */}
    </Layout>
  );
}
```

만약에 [http://localhost:3000/posts/pre-rendering](http://localhost:3000/posts/pre-rendering) 위 사이트에 접근한다면 , **January 1, 2020** 로 쓰여진 날짜를 볼 수 있습니다.

**Adding CSS**

마지막으로 , `styles/utils.module.css` 파일을 사용하여 CSS를 추가합니다. 아래의 코드를 따라서 Post 컴포넌트에 CSS파일을 import 합니다.

```javascript
// Add this import at the top of the file
import utilStyles from "../../styles/utils.module.css";

export default function Post({ postData }) {
  return (
    <Layout>
      <Head>
        <title>{postData.title}</title>
      </Head>
      <article>
        <h1 className={utilStyles.headingXl}>{postData.title}</h1>
        <div className={utilStyles.lightText}>
          <Date dateString={postData.date} />
        </div>
        <div dangerouslySetInnerHTML={{ __html: postData.contentHtml }} />
      </article>
    </Layout>
  );
}
```

만약에 [http://localhost:3000/posts/pre-rendering](http://localhost:3000/posts/pre-rendering)에 접근한다면 , 페이지는 아래와 같이 더 나아 보일 것입니다.

![](https://nextjs.org/static/images/learn/dynamic-routes/post-page-css.png)

다음에 index 페이지를 업데이트하고 끝내겠습니다.

#### 8) Polishing the Index Page

다음에 index 페이지를 업데이트를 해보겠습니다. 우리는 [Link](https://nextjs.org/docs/api-reference/next/link) 컴포넌트를 사용해서 각 포스트 페이지에 link를 추가해야합니다.

`pages/index.js` 페이지를 열고 아래와 같이 [Link](https://nextjs.org/docs/api-reference/next/link)와 Date 컴포넌트를 최상위에 import 합니다.

```javascript
import Link from "next/link";
import Date from "../components/date";
```

그리고 같은 파일 하단에 `li` 태그를 아래와 같이 대체합니다.

```jsx
<li className={utilStyles.listItem} key={id}>
  <Link href={`/posts/${id}`}>{title}</Link>
  <br />
  <small className={utilStyles.lightText}>
    <Date dateString={date} />
  </small>
</li>
```

만약에 http://localhost:3000 으로 이동한다면 각각의 아티클은 link를 가집니다.

![](https://nextjs.org/static/images/learn/dynamic-routes/links.png)

> 만약 무언가 작동하지 않는다면 , [이것](https://github.com/vercel/next-learn/blob/master/basics/api-routes-starter/pages/posts/%5Bid%5D.js)과 같은지 확인하세요 !

끝으로 강의를 마무리하기 전에 다음페이지에서 [dynamic routes](https://nextjs.org/docs/routing/dynamic-routes)에 대해서 몇가지 팁을 알아보겠습니다.

#### 9) Dynamic Routes Details

여기에 [dynamic routes](https://nextjs.org/docs/routing/dynamic-routes)에 대해서 알아야 할 필수 정보들이 있습니다.

**Fetch External API or Query Database**

[getStaticProps](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticprops-static-generation) , [getStaticPaths](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticpaths-static-generation)는 모든 data source들을 fetch 할 수 있습니다. 예를 들어 , `getAllPostId` ( getStaticPaths가 사용된 )는 외부의 API endpoint로 부터 fetch 할 수 있습니다.

```javascript
export async function getAllPostIds() {
  // Instead of the file system,
  // fetch post data from an external API endpoint
  const res = await fetch("..");
  const posts = await res.json();
  return posts.map((post) => {
    return {
      params: {
        id: post.id,
      },
    };
  });
}
```

**Development vs Production**

- development ( `npm run dev` or `yarn dev`)에서 [getStaticPaths](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticpaths-static-generation)는 매 요청마다 실행된다.
- production에서는 [getStaticPaths](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticpaths-static-generation)는 빌드 타임에 실행됩니다.

**Fallback**

getStaticPaths에서 `fallback : false`는 어떤 의미일까요?

만약에 [fallback이 false](https://nextjs.org/docs/basic-features/data-fetching/overview#fallback-false)이면 , 모든 paths는 [getStaticPaths](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticpaths-static-generation)에 의해서 반환되지 않고 404페이지를 만듭니다.

만약에 [fallback이 true](https://nextjs.org/docs/basic-features/data-fetching/overview#fallback-true)이면 , getStaticProps의 동작은 변합니다.

- getStaticPaths는 build time에 HTML을 반환할 것입니다.
- 빌드 시 생성되지 않은 경로는 **404** 페이지를 생성하지 않습니다. 대신 Next.js는 그런 경로에 대한 첫 번 째 요청에서 페이지의 'fallback' 버전을 제공합니다.
- background에서 Next.js는 정적으로 요청 path를 생성할 것 입니다. 그 이후로 같은 페이지에 대한 요청은 빌드 시 미리 렌더링된 다른 페이지와 마찬가지로 생성된 페이지를 제공할 것입니다.

만약에 [fallback이 blocking](https://nextjs.org/docs/basic-features/data-fetching/overview#fallback-blocking)이면, 새로운 경로는 getStaticProps에서 server-side rendered 될 것이고 향후 캐쉬되어 paths당 한번만 발생합니다.

우리의 수업 범위에 넘어가짐나 , fallback : true와 fallback : blocking에 대해서 [fallback 문서](https://nextjs.org/docs/api-reference/data-fetching/get-static-paths#fallback-false)에서 더 배울 수 있습니다.

**Catch-all Routes**

Dynamic routes는 괄호안에서 ...을 활용하여 모든 경로를 포착하도록 동적 경로를 확장할 수 있습니다.

예를 들어

- `pages/posts/[...id].js` 는 `/posts/a` 뿐만 아니라 `/posts/a/b`, `/posts/a/b/c` 와 매치됩니다.

만약에 [getStaticPaths](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticpaths-static-generation)안에서 위와 같이 해야한다면 , id key를 갖는 배열을 반환 해야합니다.

```javascript
return [
  {
    params: {
      // Statically Generates /posts/a/b/c
      id: ["a", "b", "c"],
    },
  },
  //...
];
```

그리고 `params.id` 는 [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticprops-static-generation)안에서 배열일 것입니다.

```javascript
export async function getStaticProps({ params }) {
  // params.id will be like ['a', 'b', 'c']
}
```

[catch all routes documentation](https://nextjs.org/docs/routing/dynamic-routes#catch-all-routes)을 더 배우려면 여기서 확인하세요.

**Router**

만약에 Next.js router에 접근하는것을 원한다면 , [useRouter](https://nextjs.org/docs/api-reference/next/router#userouter) hook을 [next/router](https://nextjs.org/docs/api-reference/next/router)에서 import 할 수 있습니다.

**404 Pages**

[custom 404](https://nextjs.org/docs/advanced-features/custom-error-page#404-page) 페이지를 만들기 위해서는 pages/404.js를 만들어야합니다. 이 파일은 빌드 시간에 정적으로 생성됩니다.

```javascript
// pages/404.js
export default function Custom404() {
  return <h1>404 - Page Not Found</h1>;
}
```

자세한 내용은 [오류 페이지](https://nextjs.org/docs/advanced-features/custom-error-page)설명서를 참조하세요.

**More Examples**

[getStaticProps](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticprops-static-generation)와 [getStaticPaths](https://nextjs.org/docs/basic-features/data-fetching/overview#getstaticpaths-static-generation)를 설명하기 위해 몇가지 예제를 만들었습니다. 소스코드를 살펴보세요

- [Blog Starter using markdown files](https://github.com/vercel/next.js/tree/canary/examples/blog-starter) ([Demo](https://next-blog-starter.vercel.app/))
- [WordPress Example](https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress) ([Demo](https://next-blog-wordpress.vercel.app/))
- [DatoCMS Example](https://github.com/vercel/next.js/tree/canary/examples/cms-datocms) ([Demo](https://next-blog-datocms.vercel.app/))
- [TakeShape Example](https://github.com/vercel/next.js/tree/canary/examples/cms-takeshape) ([Demo](https://next-blog-takeshape.vercel.app/))
- [Sanity Example](https://github.com/vercel/next.js/tree/canary/examples/cms-sanity) ([Demo](https://next-blog-sanity.vercel.app/))

다음 수업에서는 Next.js에서 [API Routes](https://nextjs.org/docs/api-routes/introduction)에 대해서 얘기해보겠습니다.

### 6. API Routes

#### 1) Introduction

Next.js는 [API Routes](https://nextjs.org/docs/api-routes/introduction)를 지원하여 API 엔드포인트를 Node.js 서버리스 기능으로 쉽게 생성할 수 있습니다. 비록 우리의 블로그 앱에는 필요하지는 않지만 이번 과정에서는 해당 기능을 어떻게 사용할 수 있는지 간단하게 이야기해봅시다.

#### 2) Setup
  이전과정부터 계속해서 진행하고 있다면 해당 페이지는 건너 뛰어도 좋습니다. 아래의 버튼을 눌러 다음 페이지로 이동해 주세요. 

**Download Starter Code(Optional)** 

만약 이전 과정을 듣지 않았다면  아래에 있는 starter code를 다운받고 설치해서 실행해주세요. `nextjs-blog` 폴더는 이전 수업을 잘 들었다면 결과로 가지고 있을 코드입니다. 

다시한번 말하지만 지금 하는 작업은 이전 과정을 완료했다면 불필요한 작업입니다. 

```bash
npx create-next-app@latest nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/api-routes-starter"
```

아래의 지시를 따라주세요. (`cd` 명령어를 통해 폴더로 들어가 개발 서버를 시작해주세요.)

그리고 아래의 파일들 또한 업데이트해주세요. 

- `public/images/profile.jpg` 에 여러분의 사진을 넣어주세요. (추천: 400px width/height).
- `components/layout.js` 에 있는 `const name = '[Your Name]'` 에 여러분의 이름을 적어주세요.
- `pages/index.js` 에 있는  `<p>[Your Self Introduction]</p>` 에 자기소개를 적어주세요.

#### 3) Creating API Routes
  [API Routes](https://nextjs.org/docs/api-routes/introduction)는 Next.js 앱 안에서 API endpoint를 만들 수 있도록 해줍니다. 아래와 같은 형식으로 `page/api` 디렉토리 내에 함수를 만들어서 해당 과정을 수행할 수 있습니다. 

```tsx
// req = HTTP incoming message, res = HTTP server response
export default function handler(req, res) {
  // ...
}
```

> 위 코드의 request handler에 대해 더 알아보고 싶다면 [API Routes documentation](https://nextjs.org/docs/api-routes/introduction)을 살펴보세요.
> 

서버리스 함수(Lambdas로도 불린다)로 배포할 수 있습니다.
  **Creating a simple API endpoint**

한 번 시도해 봅시다. `pages/api` 폴더 안에 `hello.js`라는 파일을 만들어 아래의 코드를 작성해주세요. 

```tsx
export default function handler(req, res) {
  res.status(200).json({ text: 'Hello' });
}
```

이제 [http://localhost:3000/api/hello](http://localhost:3000/api/hello)에 접근해봅시다. 아마 `{ "text" : "Hello" }` 라고 나와있는 것을 볼 수 있을 것입니다. 

- `req` 는 [http.IncomingMessage](https://nodejs.org/api/http.html#http_class_http_incomingmessage)의 인스턴스와 일부 사전에 빌드된 [middlewares](https://nextjs.org/docs/api-routes/api-middlewares)입니다.
- `res`는 [http.ServerResponse](https://nodejs.org/api/http.html#http_class_http_serverresponse)의 인스턴스와 일부 [helper functions](https://nextjs.org/docs/api-routes/response-helpers)입니다.

이제 다 됐습니다. 이 과정을 마무리하기 전에 다음 페이지에서는 API Routes를 사용하기 위한 몇 가지 팁에 대해 알아보겠습니다.

#### 4) API Routes Details
  다음은 [API Routes](https://nextjs.org/docs/api-routes/introduction)와 관련하여 여러분이 필수적으로 알아야 할 몇가지 정보입니다. 

**Do Not Fetch an API Route from `getStaticProps` or `getStaticPaths`**

[getStaticProp](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)s 나 [getStaticPaths](https://nextjs.org/docs/basic-features/data-fetching#getstaticpaths-static-generation)를 사용할 경우 API Route로 데이터를 가져와서는 안됩니다. 대신 [getStaticProp](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)s 나 [getStaticPaths](https://nextjs.org/docs/basic-features/data-fetching#getstaticpaths-static-generation) (혹은 헬퍼 함수라고 부릅니다.) 를 서버측에서 바로 작성하여야 합니다.

그 이유는 다음과 같습니다. [getStaticProp](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)s 와 [getStaticPaths](https://nextjs.org/docs/basic-features/data-fetching#getstaticpaths-static-generation) 는 서버측에서만 동작하는 코드로 클라이언트 측에서는 동작하지 않습니다. 게다가 이 함수들은 브라우저를 위한 자바스크립트 번들에 포함되지 않습니다. 이는 직접 데이터베이스 쿼리와 같은 코드를 브라우저로 보내지 않고도 작성할 수 있다는 의미입니다. [Writing Server-Side code](https://nextjs.org/docs/basic-features/data-fetching/get-static-props#write-server-side-code-directly) 문서를 읽으면 더 자세한 내용을 알 수 있습니다. 

**A Good Use Case: Handling Form Input**

API Routes를 사용하는 좋은 예중에 하나는 form input을 다루는 것입니다. 예를 들어 페이지에 form을 만들어서 API Route로 `POST` 요청을 보낼 수 있습니다. 그리고 요청을 바로 데이터베이스에 저장할 수 있도록 코드를 작성할 수 있습니다. API Route 코드는 클라이언트 번들에 포함되지 않으므로 서버측 코드를 안전하게 작성할 수 있습니다. 

```tsx
export default function handler(req, res) {
  const email = req.body.email;
  // Then save email to your database, etc...
}
```

**Preview Mode**

[Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)은 데이터를 headless CMS로부터 받아올 때 유용합니다. 그러나 headless CMS에 초안을 작성하거나 해당 페이지에서 초안을 즉시 미리보기 하고 싶을 때는 적합하지 않습니다. 아마 여러분은 Next.js가 해당 페이지들을 빌드시가 아닌 요청 시에 렌더하고 게시된 내용 대신에 초안 내용을 가져오는 것을 원할 것입니다. 이 특정한 경우에만 Next.js가 Static Generation을 우회하기를 원할 것입니다. 

Next.js는 위와 같은 문제를 해결하고 [API Routes](https://nextjs.org/docs/api-routes/introduction)를 활용할 수 있는 **Preview Mode**라 불리는 특성을 가지고 있습니다. 해당 내용에 대해서 더 학습하고 싶다면 [Preview Mode](https://nextjs.org/docs/advanced-features/preview-mode)문서를 참고해보세요. 

**Dynamic API Routes**

API Routes는 일반적인 페이지에서 동적으로 사용할 수 있습니다. 해당 내용에 대해 더 학습하고 싶다면 [Dynamic API Routes](https://nextjs.org/docs/api-routes/dynamic-api-routes) 문서를 참고해보세요. 

**That’s It!**

이제 마지막 과정인 다음부분에서는 Next.js 앱을 배포하는 방법에 대해서 이야기해 볼 것입니다.

### 7. Deploying Your Next.js App

#### 1) Introduction
마지막 기본 학습으로 Next.js를 production 으로 배포할 것이다.

Next.js 제작자가 만든 플랫폼인 Vercel에 배포하는 방법을 배운다.
다른 배포 옵션에 대해서도 학습해보자.

>전제 조건:  Github 계정이 필요함.

**What You’ll Learn in This Lesson**

이 학습에서 배울것:
- Vercel에 배포하는 방법
- DPS workflow: Develop, Preview, Ship
- 자체 호스팅 제공자에 배포하는 방법

#### 2) Setup

이전 학습을 진행중이라면 이번 페이지는 건너띌수 있습니다. 

**Download Starter Code (Optional)**

이전 학습부터 진행중이지 않다면, 아래의 시작 코드로 다운로드, 설치, 코드를 실행할 수 있다. 이 것은 `nextjs-blog` 디렉토리에 이전 강의와 동일한 결과를 설정한다.
다시 말하지만 당신이 이전 학습을 했다면 필요하지 않다.

```bash
npx create-next-app@latest nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/basics-final"
```
command output의 지시를 따라가라.(`cd`로 디렉토리에 들어가서 development server를 시작한다.)

반드시 다음 파일들을 업데이트 해야한다.
- `public/images/profile.jpg` 사진(추천: 400px width/height)
- `components/layout.js` 파일 `const name = '[Your Name]'`에 이름
- `pages/index.js`파일 `<p>[Your Self Introduction]</p> `에 자신 소개

#### 3) Push to GitHub
배포 전에, 아직 하지 않았다면 Github에 Next.js app을 push하자. 이렇게 하면 배포하기가 더 쉬워진다.
- Github 계정에 `nextjs-blog` 새로운 저장소를 만든다.
- 저장소는 공개 또는 비공개 할 수 있다. REDEME 또는 다른 파일들을 초기화 할 필용 없다.
- 저장소 설정에 도움이 필요하다면 Github 가이드를 살펴봐라.

그런다음:
- 만약 Next.js app 로컬 git 저장소에 초기화를 하지 않았다면 지금 해라.
- github 저장소에 Next.js app을 push해라.

 Github에 푸쉬하기 위해선, 다음과 같은 command를 실행할 수 있다.(`<username>`을 당신의 github username으로 바꿔라)
```bash
git remote add origin https://github.com/<username>/nextjs-blog.git
git push -u origin main
```
Github 저장소가 준비되었다면 다음 페이지를 계속 진행한다.

#### 4) Deploy to Vercel

Next.js를 production으로 배포하기 가장 쉬운 방법은 Next.js 제작자들이 개발한 플랫폼인 Vercel을 사용하는 것이다.

Vercel은 headless content, commerce, 또는 database와 함께 통합하도록 구축된 static과 hybrid 어플리케이션들을 위한 serverless 플랫폼이다.
프론트엔드 팀이 develop, preview, 퍼포먼스가 기본인 즐거운 사용자의 경험을 ship 을 쉽게 할 수 있도록 한다.
무료로 시작할 수 있다 - 신용 카드가 필수이지 않다.

**Create a Vercel Account**

첫번째,  https://vercel.com/signup 에서 vercel 계정을 만든다. *Continue with Github*을 선택하고 회원가입 프로세스를 진행하자.

**Import your `nextjs-blog` repository**

회원가입을 했다면 Vercel에 `nextjs-blog` 저장소를 import한다. https://vercel.com/import/git 여기에서 진행 할 수 있다.

- *Vercel for GitHub* 을 설치하자. 모든 저장소에 접근 권한을 줄 수 있다.
- Vercel을 설치했다면 `nextjs-blog`을 import 하자.

다음의 설정들을 기본 값으로 설정했다면 다른것을 바꿀 필요는 없다.
Vercel이 자동으로 당신이 가진 next.js app을 감지하고 당신을 위해 최적화된 빌드 설정들을 선택한다.
- Project Name
- Root Directory 
- Build Command 
- Output Directory 
- Development Command

배포 시, next.js app은 build 되기 시작한다. 1분 안으로 끝날 것이다.

>*Help is available*: 배포가 실패된다면,  [GitHub Discussions](https://github.com/vercel/next.js/discussions) 에서 도움을 얻을 수 있다. 배포에 대해서 좀 더 학습하고 [documentation](https://nextjs.org/docs/deployment) 을 둘러보자.

완료되면, 배포 URL을 알 수 있다. 그 url 중 하나를 클릭하고 next.js start 페이지를 볼 수 있다.

축하한다! production으로 next.js app을 배포했다. 다음 페이지에선 vercel의 자세한 부분과 권장 workflow에 대해서 살펴보자.

#### 5) Next.js and Vercel

Vercel은 next.js 제작자들이 만들었고 next.js을 최고수준으로 지원한다. vercel에 next.js app을 배포한다면 기본적으로 아래와 같은 일이 일어난다.

- Static generation을 사용해서 페이지를 만들고 assets(JS, CSS, images, fonts, etc)을 자동으로 [vercel edge network](https://vercel.com/docs/concepts/edge-network/overview)로 부터 제공한다.
- Server-Side Rendering을 사용해서 페이지를 만들고, [API routes](https://nextjs.org/docs/api-routes/introduction) 은 자동으로 [Serverless Functions](https://vercel.com/docs/concepts/functions/serverless-functions?utm_source=next-site&utm_medium=learnpages&utm_campaign=next-website) 로 분리된다.

다음과 같이 Vercel은 더 많은 기능을들 가지고 있다:
- *Custom Domains*: vercel에 배포했다면, next.js app에 custom domain을 부여 할 수 있다. [문서](https://vercel.com/docs/concepts/projects/domains?utm_source=next-site&utm_medium=learnpages&utm_campaign=next-website)에서 살펴보자.
- *Environment Variables*: 환경 변수들을 설정 할 수 있다. [문서](https://vercel.com/docs/concepts/deployments/configure-a-build#environment-variables?utm_source=next-site&utm_medium=learnpages&utm_campaign=next-website)에서 살펴보자. 그런다음 next.js app에서 [환경 변수](https://nextjs.org/docs/basic-features/environment-variables#loading-environment-variables)들을 사용 할 수 있다.
- *Automatic HTTPS*: HTTPS을 기본(custom domain 포함)으로 활성화 되어 있고 별도의 설정이 필요없다. SSL 인증은 자동 갱신한다.

[Vercel documentation](https://vercel.com/docs?utm_source=next-site&utm_medium=learnpages&utm_campaign=next-website) 에서 더 자세히 학습할 수 있다.


**Preview Deployment for Every Push**

>다음 단계는 선택적이다. - 시도해 보거나 읽어 볼 수 있다.

Vercel에 배포한 후 , 다음을 시도 해 볼 수 있다.
- 새로운 브랜치를 만든다.
- 약간을 변경하고 github에 push한다.
- 새로운 pull request를 만든다.

pull request 페이지에 `vercel` bot 의 코멘트를 볼 수 있다.

이 코멘트에 있는 Preview URL을 클릭해보자. 당신이 방금 만든 변화된 것들을 볼 수 있어야한다.

pull request 를 열었을 때, vercel은 자동으로 해당 브랜치의 모든 push에 preview 배포를 만든다. 그 preview url은 항상 마지막 preveiw 배포가 기준이 된다.

협업자들에게 preview url을 공유 할 수 있고, 즉각적인 피드백을 얻을 수 있다.

만일 preview 배포가 좋아보인다면 `main`에 merge 한다. 이 때, vercel은 자동으로 production 배포를 만든다.

**Develop, Preview, Ship**
DPS라고 부르는 workflow을 살펴봤다 : Develop, Preview, Ship.

- Develop: Next.js 에 코드를 쓰고 hot reloading feature의 이점을 취하며 Next.js 개발 서버를 실행한다.
- Preview: Github 브랜치에 변경점들을 push 하고, vercel은 URL을 이용할 수 있는 preview 배포를 만든다. 피드백을 위해 preview URL을 공유할 수 있다. 코드 리뷰 외에도 배포된 preview에서 할 수 있다.
- Ship: pull request를 `main`에 merge하고 production으로 ship한다. 

Next.js app을 개발할 시 이 작업흐름을 강력하게 추천한다. - 이 것은 당신의 앱이 더 빠르게 반복하는데 도움이 된다.

#### 6) Other Hosting Options

Node.js를 지원하는 다른 호스팅 제공업체에서도 next.js는 배포될 수 있다.
지금까지 지침을 따랐다면, `package.json` 파일에 `build`와 `start` 스크립트가 있어야 한다.

```json
{
  "scripts": {
    "dev": "next",
    "build": "next build",
    "start": "next start"
  }
}
```

호스팅 제공업체에서 `build` 스크립트를 실행하면 production application이 `.next` 폴더에 빌드된다.

```bash
npm run build
```

빌드 후, `start` 스크립트을 hybrid 페이즈들을 지원하는 Node.js server에서 시작하면,  정적으로 생성되거나 server-side render 되는 페이지들, API route 들을 제공한다.

```bash
npm run start
```

>Tip: `"start": "next start -p $PORT"`로 업데이트하여 `PORT` 파라미터들을 허용하도록 `package.json` 파일애서 `start` 스크립트을 사용자화 할 수 있다.  

Next.js 배포에 대하여 궁금한점이 있으면 우리의 [커뮤니티](https://github.com/vercel/next.js/discussions)에서 물어볼 수 있다.


#### 7) Finally
모든 기초 학습을 마친것을 축하한다. 다음은 권장 단계이다.:

**Share Your Next.js App**
트위터에서 당신이 이 튜트리얼에서 앱을 빌드 한것을 공유하는 것이 좋다. 그렇다면 우리가 살펴 볼 수 있도록 @vercel에 멘션을 주길 바란다. 이 튜트리얼에 대한 피드백도 환영한다.

**Use TypeScript with Next.js**
타입스크립트를 사용한것을 좋아한다면  [how to use TypeScript with Next.js from here](https://nextjs.org/learn/excel/typescript)에서 학습할 수 있다.

**What to Learn Next**
더 학습하기 위해 [documentation](https://nextjs.org/docs)를 살펴보자. 특히, 다음 페이지들은 흥미로울 수 있다.
- [Data Fetching](https://nextjs.org/docs/basic-features/data-fetching/overview): data fetching에 대하여 더 자세히 학습한다.
- [Environment Variables](https://nextjs.org/docs/basic-features/environment-variables): 환경 변수를 위한 내장 지원에 대하여 더 자세히 학습한다.
- [Search Engine Optimization](https://nextjs.org/learn/seo/introduction-to-seo): Next.js의 SEO 최적화 방법에 대하여 학습한다.

**Join the Conversation**
Next.js와 관련된 어떤것에 대하여 문의가 있다면 [Github Discussions](https://github.com/vercel/next.js/discussions)에 우리의 커뮤니티에서 물어보는 것을 언제나 환영한다.

## Search Engine Optimization

### 1. Introduction to SEO

#### 1) Introduction
  **What is SEO?**

SEO는 Search Engine Optimization의 약자입니다. SEO의 목적은 검색 엔진 결과에서 순위를 증가시키기 위한 전략을 만들기 위합니다. 높은 순위는 사이트의 트래픽을 증가시키고 궁극적으로 더 많은 비즈니스를 가져오게 될 것입니다. 

**What You’ll Learn in This Course**

이번 과정에서 우리가 배울 내용은 아래와 같습니다. 

- 검색 시스템과 Googlebot과 같은 검색 엔진 로봇
- 사이트에 SEO 전략을 적용했을 때의 효과
- Next.js에서의 Crawling, indexing, rendering, ranking
- Core Web Vital을 포함한 웹 성능

**Join the Conversation**

만약 Next.js와 해당 과정에 대한 질문이 있으시다면 [Discord](https://discord.gg/Q3AsD4efFC)에 있는 커뮤니티에 와서 의견을 남겨주세요. 

그럼 시작해봅시다.

#### 2) Importance of SEO
  **Why is SEO so important?**

SEO는 여러분의 브랜드에 대한 전환과 신뢰는 높이는 열쇠입니다. 높은 검색 순위에 위치한다는 것은 더 많은 유기적인 방문자가 있다는 것과 같습니다. **Search engine organic traffic** - 검색 엔진에서 결과를 클릭하여 사이트를 방문하는 방문자 - 는 아래와 같은 이유로 많은 비즈니스에서 매우 중요한 열쇠입니다. 

1. **Qualitative** - 방문자가 고객이 될 기회가 더 많아집니다. 
2. **Trustable** - 브랜드 혹은 과제에 대한 신뢰도가 향상됩니다. 
3. **Low-Cost** - 시간과 노력을 들이는 것 이외에 검색 엔진 순위를 높일 수 있는 좋은 SEO를 만드는 것은 무료입니다. 
   
    검색엔진 최적화는 sponsored 라벨이 붙은 채로 검색 결과 상단에 노출되는 100% 유료화 된 유기적인 결과와 구분되는 [Search Engine Marketing (SEM)](https://learndigital.withgoogle.com/digitalgarage/course/promote-business-online/lesson/54)과는 다릅니다. 
    

****Three Pillars of Optimization****

웹 사이트를 최적화하는 과정은 크게 세 가지로 나눌 수 있습니다. 

1. Technical - 크롤링 및 웹 성능을 위해 웹 사이트를 최적화합니다. 
2. Creation - 특정 키워드를 대상으로 하는 콘텐츠 전략을 만듭니다. 
3. Popularity - 검색엔진이 신뢰할만한 출저임을 알 수 있도록 웹 사이트의 온라인 인지도를 향상시킵니다. 이는 사이트로 다시 연결되는 타사의 사이트인 [backlinks](https://moz.com/learn/seo/backlinks)를 사용하여 수행됩니다. 

SEO 분야는 매우 넓고 많은 측면이 있습니다. 하지만 Next.js 개발자로서 첫 번째로 알아야 할 것은 몇 가지 모범 사례를 통해 웹 앱의 SEO를 대비할 수 있는 방법을 이해하는 것입니다.

#### 3) Search Systems
  **Why is SEO so important?**

SEO는 여러분의 브랜드에 대한 전환과 신뢰는 높이는 열쇠입니다. 높은 검색 순위에 위치한다는 것은 더 많은 유기적인 방문자가 있다는 것과 같습니다. **Search engine organic traffic** - 검색 엔진에서 결과를 클릭하여 사이트를 방문하는 방문자 - 는 아래와 같은 이유로 많은 비즈니스에서 매우 중요한 열쇠입니다. 

1. **Qualitative** - 방문자가 고객이 될 기회가 더 많아집니다. 
2. **Trustable** - 브랜드 혹은 과제에 대한 신뢰도가 향상됩니다. 
3. **Low-Cost** - 시간과 노력을 들이는 것 이외에 검색 엔진 순위를 높일 수 있는 좋은 SEO를 만드는 것은 무료입니다. 
   
    검색엔진 최적화는 sponsored 라벨이 붙은 채로 검색 결과 상단에 노출되는 100% 유료화 된 유기적인 결과와 구분되는 [Search Engine Marketing (SEM)](https://learndigital.withgoogle.com/digitalgarage/course/promote-business-online/lesson/54)과는 다릅니다. 
    

****Three Pillars of Optimization****

웹 사이트를 최적화하는 과정은 크게 세 가지로 나눌 수 있습니다. 

1. Technical - 크롤링 및 웹 성능을 위해 웹 사이트를 최적화합니다. 
2. Creation - 특정 키워드를 대상으로 하는 콘텐츠 전략을 만듭니다. 
3. Popularity - 검색엔진이 신뢰할만한 출저임을 알 수 있도록 웹 사이트의 온라인 인지도를 향상시킵니다. 이는 사이트로 다시 연결되는 타사의 사이트인 [backlinks](https://moz.com/learn/seo/backlinks)를 사용하여 수행됩니다. 

SEO 분야는 매우 넓고 많은 측면이 있습니다. 하지만 Next.js 개발자로서 첫 번째로 알아야 할 것은 몇 가지 모범 사례를 통해 웹 앱의 SEO를 대비할 수 있는 방법을 이해하는 것입니다.

#### 4) What are Webcrawlers?
  **What are Web Crawlers?**

웹 사이트를 검색 결과에 표시하기 위해서 구글(Bing, Yandex, Baidu, Naver, Yahoo, DuckDuckGo와 같은 다른 검색 엔진을 포함하여)은 웹 크롤러를 사용하여 웹 사이트를 탐색하고 웹 사이트와 해당 웹 페이지를 검색합니다. 

서로 다른 검색엔진들은 각 나라마다 다른 [시장 점유율](https://gs.statcounter.com/search-engine-market-share)을 가집니다. 

이 가이드에서는 대부분의 국가에서 가장 큰 검색엔진인 구글에 대해 다룹니다. 즉 특히 대상 고객이 중국, 러시아, 일본 또는 한국인 경우 다른 검색 엔진과 그들의 가이드를 확인하는 것이 좋을 것입니다. 

Ranking과 Rendering과정에서 약간의 차이가 있지만 대부분의 검색 엔진들은 Crawling과 Indexing에서는 비슷한 방식으로 작동합니다. 

웹 크롤러는 사용자를 모방하고 웹 사이트에서 찾은 링크를 탐색하여 페이지를 인덱싱하는 일종의 봇입니다. 웹 크롤러는 custom [user-agents](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent)를 사용하여 자신을 식별합니다. 구글은 [여러 웹 크롤러](https://developers.google.com/search/docs/advanced/crawling/overview-google-crawlers)가 있지만 가장 자주 사용되는 것은 Googlebot Desktop과 Googlebot Smartphone입니다.
**How Does Googlebot Work?**
![image](https://user-images.githubusercontent.com/95066223/209816803-3568aef5-0fe0-42f0-bb0e-2338e6b70feb.png)
프로세스의 일반적인 개요는 다음과 같습니다:

1. Find URLs:구글은 Google Search Console, 웹 사이트 간 링크 또는 XML 사이트맵을 비롯한 여러 위치의 URL을 가져옵니다. 
2. Add to Crawl Queue: 수집된 URL들은 Googlebot이 처리할 Crawl Queue에 추가됩니다. Crawl Queue에 있는 URL들은 일반적으로 몇 초동안 지속되지만 경우에 따라 특히 페이지를 렌더링, 인덱싱해야 하거나 URL이 이미 인덱싱되어 있는 경우 새로 고쳐야 하는 경우에는 며칠까지 지속될 수 있습니다. 해당 페이지들은 Render Queue로 들어가게 됩니다. 
3. HTTP Request: 크롤러는 헤더를 가져오기 위해 HTTP 요청을 만들고 반환된 상태 코드에 따라 작동합니다. 
    - 200 - HTML을 크롤링하고 분석합니다.
    - 30X - 리디렉션을 따릅니다.
    - 40X - 에러를 기록하고 HTML을 로드하지 않습니다.
    - 50X - 상태 코드가 변경되었는지 확인하기 위해 추후에 다시 접속할 수 있습니다.
4. Render Queue: 검색 시스템의 다양한 서비스 및 구성 요소가 HTML을 처리하고 콘텐츠를 분석합니다. 만약 페이지의 일부가 자바스크립트 클라이언트 기반 콘텐츠를 가지고 있을 경우 URL이 Render Queue에 추가될 수 있습니다. Render Queue는 자바스크립트를 렌더링하기 위해 더 많은 자원을 사용해야 하므로 구글에게 더 많은 비용이 듭니다. 일부 다른 검색 엔진들은 아마 구글과 같ㅇㄴ 렌더링 용량을 가지고 있지 않을 수 있으므로 여기서 Next.js는 렌더링 전략에 도움이 될 수 있습니다. 
5. Ready to be indexed: 만약 모든 기준이 충족되었다면 페이지를 인덱싱하여 검색 결과로 보여줄 수 있습니다. 

다음으로 있을 몇 가지 과정에서는 검색 시스템 프로세스의 각 주요 구성 요소(크롤링 및 인덱싱, 렌더링 순위 지정)에 대해 자세히 살펴보겠습니다.

### 2. Crawling and Indexing

#### 1) Introduction

이제 검색 시스템과 구글봇의 동작방식에 대한 전반적인 개요를 알아보았으므로 크롤링과 인덱싱에 영향을 미치는 몇 가지 주요 부분을 자세히 살펴보겠습니다. 

이번 과정에서는 다음과 같은 내용을 살펴볼 것입니다. 

- HTTP 상태 코드 기본사항
- 메타데이터와 웹 크롤러가 웹 콘텐츠를 파싱할 때 찾는 항목
- 여러분의 사이트에 새로운 콘텐츠가 있을 검색 크롤러가 알 수 있도록 구글과 통신하는 방법
- 원하는 인덱싱 상태를 검색 엔진에 표시하기 위해 메타 로봇 태그 및 표준 링크를 활용하는 방법

#### 2) Status Codes

[HTTP 응답 상태 코드](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)는 특정한 HTTP 요청이 성공적으로 완료되었는지 여부를 나타냅니다. 많은 상태 코드가 있지만 SEO 관점에서 의미있는 것은 소수에 불과합니다. 이제 그것들에 대해 알아볼 것입니다. 

200

```
`HTTP 200 OK`는 성공 상태를 나타내는 응답 코드로 요청이 성공했음을 나타냅니다. 
```

구글에서 페이지를 인뎃싱하기 위해서는 상태 코드 `200`을 반환해야 합니다. 이는 전형적으로 유기적 트래픽을 수신하기 위해 페이지에서 찾고자 하는 것입니다. 

이는 Next.js가 페이지를 성공적으로 렌더링 했을 때 설정되는 기본 코드입니다. 

300 

```
`HTTP 301 Moved Permanently`는 redirect 상태를 나타내는 응답코드로 요청된 리소스가 영구적으로 다른 URL로 이동되었음을 나타냅니다. 
```

이는 영구적인 리디렉션입니다. 일반적으로 가장 널리 사용되는 리디렉션 유형입니다. 

리디렉션은 다양한 이유로 사용되지만 주된 원인은 URL이 A에서 B로 이동되었다는 것을 나타냅니다. 

만약 콘텐츠가 기존의 위치에서 다른 위치로 이동되었다면 현재의 고객과 잠재된 고객을 잃지 않고 봇이 사이트를 계속 인덱싱할 수 있도록 하기 위해서는 리디렉션이 필수적입니다. 

참고**:** [Next.js permanent redirects](https://nextjs.org/docs/api-reference/next.config.js/redirects)은 301 대신에 더 최신 버전이고 나은 옵션으로 간주되는 308을 기본으로 사용합니다. 

두 상태 코드의 주요 차이점은 `301`은 요청방법을 POST에서 GET으로 변경할 수 있는 반면 `308`은 그렇지 않다는 것입니다. 

`getStaticProps()` 함수에서 props 대신 redirect를 반환하면 Next.js에서 308 리디렉션을 트리거할 수 있습니다. 

```jsx
//  pages/about.js
export async function getStaticProps(context) {
  return {
    redirect: {
      destination: '/',
      permanent: true, // triggers 308
    },
  };
}
```

next.config.js에서 `permenent: true` 키를 사용해 리디렉션을 설정할 수 있습니다. 

```jsx
//next.config.js

module.exports = {
  async redirects() {
    return [
      {
        source: '/about',
        destination: '/',
        permanent: true, // triggers 308
      },
    ];
  },
};
```

302 

```
`HTTP 302 Found` 리디렉션 상태 응답 코드는 요청된 리소스가 일시적으로 대상 URL로 이동되었음을 나타냅니다. 
```

대부분의 경우 302 리디렉션은 301 리디렉션이어야 할 것입니다. 일시적으로 사용자를 특정 페이지(예. 홍보 페이지)로 리디렉션하거나 위치를 기반으로 사용자를 리디렉션하는 경우에는 그렇지 않을 수 있습니다. 

404

```
`HTTP 404 Not Found`는 클라이언트 에러 응답 코드로 요청된 리소스를 서버에서 찾을 수 없다는 것을 나타냅니다. 
```

위에서 언급한대로 이동된 페이지는 `HTTP 301` 상태 코드와 함께 새로운 위치로 리디렉션되어야 합니다. 그렇지 않을 경우 URL은 `404` 상태 코드를 반환할 수 있습니다. 

`404` 상태 코드는 사용자가 존재하지 않는 URL을 방문하는 경우 나타나는 결과로 기본적으로 반드시 나쁜 것은 아니지만 페이지에서 빈번하게 에러가 발생할 경우 검색 순위가 저하될 수 있습니다. 

Next.js는 여러분의 애플리케이션에서 존재하지 않는 URL에 대해 자동으로 `404`를 반환합니다. 

경우에 따라 페이지에서 `404`를 반환할수도 있습니다. props 대신 아래의 코드를 반환하여 이를 수행할 수 있습니다. 

```jsx
export async function getStaticProps(context) {
  return {
    notFound: true, // triggers 404
  };
}
```

`pages/404.js` 파일을 생성하여 빌드 시 정적으로 생성되는 [404 페이지를 커스텀할 수 있습니다.](https://nextjs.org/docs/advanced-features/custom-error-page#404-page) 

예시: 

```jsx
// pages/404.js
export default function Custom404() {
  return <h1>404 - Page Not Found</h1>;
}
```

410

```
`HTTP 410 Gone`은 클라이언트 에러 응답 코드로 오리진 서버에서 대상 리소스에 대한 접근을 할 수 없으며 이 상태가 영구적일 가능성이 있음을 나타냅니다. 
```

이는 주로 사용되지는 않지만 웹 사이트에서 더 이상 존재하지 않을 콘텐츠를 삭제하려는 경우 이 상태 코드를 사용할 수 있습니다. 

`HTTP 410 Gone`의 유용한 사용 예는 다음과 같습니다. 

- E-commerce: 재고에서 영구적으로 삭제된 상품
- Forum: 사용자가 삭제한 스레드
- Blog: 사이트에서 제거된 블로그 게시물

해당 상태 코드는 봇이 이 콘텐츠를 크롤링하기 위해 절대 돌아와서는 안 된다고 알려줍니다. 

500

```
`HTTP 500 Internal Server Error`는 응답 코드로 서버가 요청을 이행하기 못하게 하는 예상하지 못한 상황이 발생했음을 나타냅니다. 
```

Next.js는 예기치 못한 애플리케이션 오류에 대해 자동으로 `500` 상태 코드를 반환합니다. 

`pages/500.js` 파일을 생성하여 빌드 시 정적으로 생성되는 [500 에러 페이지를 커스텀할 수 있습니다](https://nextjs.org/docs/advanced-features/custom-error-page#404-page)

예시: 

```jsx
// pages/500.js
export default function Custom500() {
  return <h1>500 - Server-side error occurred</h1>;
}
```

503 

```
`HTTP 503 Service Unavailable` 서버 에러 응답 코드는 서버가 해당 요청을 처리할 준비가 되지 않았음을 나타냅니다. 
```

웹 사이트가 다운되고 웹 사이트가 장기간 다운될 것으로 예상되는 경우 해당 상태 코드를 반환하는 것이 좋습니다. 이는 장기적으로 순위를 잃는 것을 방지합니다.

#### 3) Robots.txt
**What is a robots.txt File?**

[robots.txt 파일은](https://developers.google.com/search/docs/advanced/robots/intro) 검색 엔진 크롤러에게 크롤러가 사이트에서 요청할 수 있거나 요청할 수 없는 페이지 또는 파일을 알려줍니다. `robots.txt` 파일은 웹 표준 파일로 대부분의 [좋은 봇](https://www.cloudflare.com/learning/bots/how-to-manage-good-bots)들이 특정 도메인에서 무언가를 요청하기 전에 사용합니다. 

CMS 또는 관리자, 전자 상거래의 사용자 계정 또는 일부 API 경로와 같이 웹 사이트로부터 특정 영역이 탐색되지 않도록 보호하고 싶을 수 있습니다. 

이 파일들은 각 호스트의 루트에서 제공되어야 하며 이외의 경우 루트 `/robots.txt` 경로를 대상 URL로 리디렉션할 수 있으며 대부분의 봇이 이를 따릅니다. 

**How to add a robots.txt file to a Next.js project**

[정적 페이지를](https://nextjs.org/docs/basic-features/static-file-serving) 제공하는 Next.js에서는 `public` 폴더에 `robots.txt` 이름을 가진 파일을 생성함으로서  `robots.txt` 파일을 쉽게 추가할 수 있습니다. 

파일에 넣을 수 있는 항목의 예는 다음과 같습니다. 

```
# Block all crawlers for /accounts
User-agent: *
Disallow: /accounts

# Allow all crawlers
User-agent: *
Allow: /
```

`yarn dev`로 앱을 실행할 경우 [http://localhost:3000/robots.txt](http://localhost:3000/robots.txt)에서 접근할 수 있습니다. `public` 폴더의 이름은 URL에 포함되지 않음을 주의하세요. 

public 디렉토리에 다른 이름을 지정하지 마세요. 이름은 변경이 불가능하며 정적인 assets을 처리하기 위해 사용되는 유일한 디렉토리입니다.
#### 4) XML Sitemaps

사이트 맵은 구글과 소통하는 가장 쉬운 방법입니다. 이는 웹 사이트에 포함된 URL과 업데이트 시기를 가르키며 구글이 새로운 콘텐츠를 쉽게 감지하고 여러분의 웹사이트를 더욱 효과적으로 크롤링할 수 있도록 합니다. 

XML 사이트 맵은 가장 많이 알려지고 사용되는 맵이지만 [RSS](https://developers.google.com/search/docs/advanced/sitemaps/build-sitemap)나 [Atom](https://developers.google.com/search/docs/advanced/sitemaps/build-sitemap)을 통해 생성할 수도 있고 최대로 단순한 것을 선호할 경우 [Text](https://developers.google.com/search/docs/advanced/sitemaps/build-sitemap) 파일을 사용할 수도 있습니다. 

사이트맵은 사이트의 페이지, 비디오 및 기타 파일에 대한 정보와 이들 간의 관계를 제공하는 파일입니다. 구글과 같은 검색 엔진은 당신의 사이트를 더 지능적으로 크롤링하기 위해 해당 파일을 읽습니다. 

[Google](https://developers.google.com/search/docs/advanced/sitemaps/overview)에 의하면: 

```
다음과 같은 경우 사이트 맵이 필요할 수 있습니다. 
- 사이트가 매우 클 경우. 구글 웹 크롤러는 새 페이지 또는 최근 업데이트된 페이지 중 일부를 크롤링하는 것을 간과할 가능성이 높습니다. 
- 사이트에 서로 분리되었거나 잘 연결되지 않은 콘텐츠 페이지의 대용량 아카이브가 있을 경우. 사이트 페이지가 자연스럽게 서로를 참조하지 않는 경우 사이트 맵에 나열하여 구글이 일부 페이지를 간과하지 않도록 할 수 있습니다. 
사이트가 새로 만들어졌거나 외부 링크가 거의 없을 경우. 구글봇 및 기타 웹 크롤러는 한 페이지에서 다른 페이지로 연결되는 링크를 따라 웹을 탐색합니다. 결과적으로 페이지에 연결된 다른 사이트가 없으면 구글에서 페이지를 찾지 못할 수 있습니다. 
사이트에 리치 미디어 콘텐츠(동영상, 이미지)가 많거나 구글 뉴스에 표시될 경우. 제공된 경우 구글은 적절한 경우 검색을 위해 사이트맵의 추가 정보를 고려할 수 있습니다. 
```

사이트맵은 좋은 검색 엔진 성능을 위한 필수조건은 아니지만 봇에 대한 크롤링 및 인덱싱을 용이하게 할 수 있으므로 콘텐츠가 더 빨리 선택되고 그에 따라 순위가 매겨집니다. 

사이트맵을 사용하고 웹 사이트 전체에 새로운 콘텐츠가 채워질 때 이를 동적으로 만드는 것은 강력하게 추천됩니다. 정적 사이트 맵도 유효하지만 지속적인 검색 목적으로 사용되지 않기 때문에 구글에서는 덜 유용할 수 있습니다. 

**How to Add Sitemaps to a Next.js Project**

여기에는 두가지 선택사항이 있습니다. 

- Manual
    
    만약 비교적 간단하고 정적인 사이트라면 sitemap.xml 파일을 public 디렉토리에 수동으로 생성할 수 있습니다. 
    
    ```xml
    <!-- public/sitemap.xml -->
       <xml version="1.0" encoding="UTF-8">
       <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
         <url>
           <loc>http://www.example.com/foo</loc>
           <lastmod>2021-06-01</lastmod>
         </url>
       </urlset>
       </xml>
    ```
    
- getServerSideProps
    
    사이트가 동적인 경우에는 getServerSideProps를 활용하여 필요에 따라 XML 사이트맵을 생성할 수 있습니다. 
    
    페이지 디렉터리 내에 `pages/sitemap.xml.js` 와 같은 새 페이지를 만들 수 있습니다. 이 페이지의 목표는 동적 페이지의 URL을 알 수 있는 데이터를 얻기 위해 API를 사용하는 것입니다. 그런 다음 /sitemap.xml에 대한 응답으로 XML 파일을 작성합니다. 
    
    다음은 직접 사용해 볼 수 있는 예입니다. 
    
    ```jsx
    //pages/sitemap.xml.js
    const EXTERNAL_DATA_URL = 'https://jsonplaceholder.typicode.com/posts';
    
    function generateSiteMap(posts) {
      return `<?xml version="1.0" encoding="UTF-8"?>
       <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
         <!--We manually set the two URLs we know already-->
         <url>
           <loc>https://jsonplaceholder.typicode.com</loc>
         </url>
         <url>
           <loc>https://jsonplaceholder.typicode.com/guide</loc>
         </url>
         ${posts
           .map(({ id }) => {
             return `
           <url>
               <loc>${`${EXTERNAL_DATA_URL}/${id}`}</loc>
           </url>
         `;
           })
           .join('')}
       </urlset>
     `;
    }
    
    function SiteMap() {
      // getServerSideProps will do the heavy lifting
    }
    
    export async function getServerSideProps({ res }) {
      // We make an API call to gather the URLs for our site
      const request = await fetch(EXTERNAL_DATA_URL);
      const posts = await request.json();
    
      // We generate the XML sitemap with the posts data
      const sitemap = generateSiteMap(posts);
    
      res.setHeader('Content-Type', 'text/xml');
      // we send the XML to the browser
      res.write(sitemap);
      res.end();
    
      return {
        props: {},
      };
    }
    
    export default SiteMap;
    ```

#### 5) Special Tags

**Special Meta Tags for Search Engines**

메타 로봇 태그는 검색엔진이 항상 준수하는 지시어입니다. 이러한 로봇 태그를 추가하면서 웹 사이트의 색인화가 더 쉬워집니다. 

directives(지시어)와 suggestions(제안)은 다음과 같은 차이가 있습니다. 메타 로봇 태그 또는 `robot.txt` 파일은 지시어로 항상 지켜집니다. Canonical tag(표준 태그)는 권장사항으로 구글은 이를 지키거나 그렇지 않을 수 있습니다. 

페이지 레벨의 메타 태그와 관련하여 많은 옵션들이 있지만 다음은 일반적으로 SEO와 관련된 예입니다. 

```jsx
<meta name="robots" content="noindex,nofollow" />
```

로봇 태그는 여러분이 볼 수 있는 가장 흔한 태그일 것입니다. 기본적으로 `index, follow` 값이 있으므로 지정할 필요가 없으며 `all` 유효한 대안으로 사용될 수 있습니다. 

```jsx
<meta name="robots" content="all" />
```

위의 예시와 같이 로봇 태그를 `noindex,nofollow`로 설정하면 검색엔진에 아래와 같이 표시됩니다. 

- noindex
    
    검색결과에 이 페이지를 표시하지 않기 위해 사용합니다. `noindex`를 생략하면 페이지를 인덱싱하여 검색 결과에 표시할 수 있음을 나타냅니다. 
    
    웹 사이트를 구축할 때 특정 페이지를 인덱싱하고 싶지 않을 수 있습니다. 일반적으로 설정 페이지, 내부 검색 페이지, 정책 등의 페이지에서 사용됩니다. 
    
- nofollow
    
    해당 페이지의 링크를 따라가지 않기 위해 사용합니다. 이를 생략할 경우 로봇이 이 페이지의 링크를 크롤링하고 따라갈 수 있습니다. 다른 페이지에서 찾은 링크는 크롤링을 사용하도록 설정할 수 있으므로 페이지 X와 Y에 linkA가 있고 X에 `nofollow` 로봇 태그가 있고 Y에는 없다면 구글은 해당 링크를 크롤링할 수 있습니다. 
    

참고: 구글 공식 문서에서 [지시어의 전체 목록](https://developers.google.com/search/docs/advanced/robots/robots_meta_tag#directives)을 확인할 수 있습니다. 

**Googlebot tag**

```jsx
<meta name="googlebot" content="noindex,nofollow" />
```

가끔 `googlebot` 태그를 볼수도 있을 것입니다. 대부분의 경우에서 `robots` 만 있으면 됩니다. `googlebot` 태그는 구글에만 특정됩니다. 구글봇에 대한 별도의 규칙과 나머지 검색 봇에 대한 일반적인 하나의 규칙을 원할 경우 해당 태그를 사용할 수 있습니다. 

이 경우 충돌하는 태그가 있을 때 더 제한적으로 태그가 적용됩니다. 

크롤링을 원하지 않는 URL을 `robot.txt`에 추가할 수 있는 경우 이러한 태그가 필요한 이유가 궁금할 수 있습니다. 해당 메타 태그는 요청 시 페이지를 `noindex` 로 표시할 수 있는 유연성을 제공합니다. 

예를 들어 제품 페이지에 필터를 적용했는데 결과가 없는 경우 이 페이지를 `noindex`하는 것이 일반적입니다. 

`robots.txt` 파일을 통해 크롤링하는 봇으로부터 제한된 URL은 구글에서 절대 크롤링하지 않지만 페이지의 색인이 이미 생성된 후에 규칙이 추가되면 페이지의 색인이 생성된 상태로 유지될 수 있습니다. 페이지의 색인이 생성되지 않도록 하는 가장 좋은 방법은 `noindex` 태그를 사용하는 것입니다. 

**참고:** Google은 페이지를 크롤링하지 않고 색인을 생성하도록 결정할 수 있습니다. 이것은 매우 드물지만 Google이 페이지가 특정 검색 결과를 이행하기를 원하고 페이지에 사용자가 기대하는 내용이 포함되어 있다고 확신할 때 발생합니다.

**Google tags**

nositelinkssearchbox

```jsx
<meta name="google" content="nositelinkssearchbox" />
```

사용자가 여러분의 사이트를 검색할 때 구글 검색 결과는 여러분의 사이트에 대한 다른 직접 링크와 함께 여러분의 사이트에 특정한 검색창이 표시되는 경우가 있습니다. 이 태그는 구글에 사이트 링크 검색창을 표시하지 않도록 지시합니다. 

notranslate

```jsx
<meta name="google" content="notranslate" />
```

구글은 사이트 콘텐츠가 사용자가 일고 싶어하는 언어로 되어 있지 않음을 인식하면 종종 검색 결과에 번역 링크를 제공합니다. 

일반적으로 이는 훨씬 더 많은 사용자 그룹에 매력적인 콘텐츠를 제공할 수 있습니다. 하지만 이러한 점이 적절하지 않은 상황도 있을 수 있습니다. 이 메타 태그는 구글에게 해당 페이지의 번역을 제공하지 않기를 원한다고 알립니다. 

예시

이제 우리는 접할 수 있는 몇 가지 일반적인 태그를 알아보았습니다. 다음은 그 중 일부를 사용하는 페이지의 예시입니다. 

```jsx
import Head from 'next/head';

function IndexPage() {
  return (
    <div>
      <Head>
        <title>Meta Tag Example</title>
        <meta name="google" content="nositelinkssearchbox" key="sitelinks" />
        <meta name="google" content="notranslate" key="notranslate" />
      </Head>
      <p>Here we show some meta tags off!</p>
    </div>
  );
}

export default IndexPage;
```

예제에서 볼 수 있듯이 [next/head](https://nextjs.org/docs/api-reference/next/head)는 페이지의 `head`에 요소를 추가하기 위해 사용한 빌트인 컴포넌트입니다. 

`head`에 태그가 중복되는 것을 피하기 위해서 `key` 속성을 사용할 수 있으며 이는 태그가 한 번만 렌더링되도록 합니다.

#### 6) Canonical Tags

표준 URL은 중복된 페이지들의 모임에서 검색엔진이 가장 대표적이라고 생각하는 페이지의 URL입니다. 

검색엔진에게 표준 URL을 직접적으로 전달할 수도 있지만 또한 이를 알리지 않고 여러 URL을 그룹화하도록 결정할 수도 있습니다. 구글이 여러 경로에서 URL을 찾아낼 경우 이는 자동으로 발생할 수 있습니다. 

구글은 이들을 감지하는 데 큰 역할을 하지만 시스템은 막대한 규모로 동작하며 이는 모든 극단적인 경우를 다루지는 않습니다. 표준 태그는 웹 사이트에서 우수한 성능을 보장하기 위해 다루어야 할 중요한 측면입니다. 

만약 구글이 같은 콘텐츠를 가진 여러 URL들을 찾아낸다면 이는 아마 중복된 것으로 간주될 수 있으므로 검색결과에서 해당 URL의 강등을 결정할 수 있습니다. 

이는 도메인간에도 발생할 수 있습니다 .만약 여러분이 두개의 다른 웹사이트를 운영하고 있고 그 안에서 같은 콘텐츠를 게시했다면 검색엔진은 순위를 매길 둘 중 하나를 선택하거나 둘 다 바로 강등시킬 수 있습니다. 

여기에서 표준 태그가 매우 유용합니다. 그들은 어떤 URL이 진실의 원본이고 어떤 URL이 복제되었는지 구글에 알려줍니다. 동일하거나 다른 도메인에 걸쳐 중복된 페이지가 많으면 순위가 낮아지거나 불이익을 받을 수 있습니다. 

E-commerce에서 [example.com/products/phone](https://example.com/products/phone) 와 [example.com/phone](http://example.com/phone)을 통해 제품에 접근할 수 있다고 가정해 봅시다. 

둘 모두 유효하고 동작하는 URL이지만 우리는 우리가 소유한 중복 콘텐츠의 감지를 방지하기 위해 표준을 사용합니다. 순위에 [`https://example.com/products/phone`](https://example.com/products/phone)이 사용되어야 한다고 결정한 경우 표준 태그를 생성할 수 있습니다. 

```jsx
<link rel="canonical" href="https://example.com/products/phone" />
```

표준 태그는 다른 URL을 만들 수 있을 뿐 아니라 사용자 또는 마케팅 도구도 만들 수 있기 때문에 SEO 성능의 기본입니다. 

구글에서 마케팅 캠페인을 실행 중이고 구글이 일부 [UTM parameters](https://ga-dev-tools.appspot.com/campaign-url-builder/)를 추가하기로 결정했다고 가정해 보세요. 이 새롭고 고유한 URL이 구글봇에 의해 색인 생성될 수 있으므로 중복 페이지를 통합하기 위해 표준 태그를 계속 표시하고 있는지 확인해야 합니다.

예시

```jsx
import Head from 'next/head';

function IndexPage() {
  return (
    <div>
      <Head>
        <title>Canonical Tag Example</title>
        <link
          rel="canonical"
          href="https://example.com/blog/original-post"
          key="canonical"
        />
      </Head>
      <p>This post exists on two URLs.</p>
    </div>
  );
}

export default IndexPage;
```

### 3. Rendering and Ranking

#### 1) Introduction

#### 2) Rendering Strategies

#### 3) What About AMP?

#### 4) URL Structure

#### 5) Metadata

#### 6) On Page SEO

### 4. Performanca & Core Web Vitals

#### 1) Introduction

#### 2) Vitals Overview

#### 3) Largest Contentful Paint

#### 4) First Input Delay

#### 5) Cumulative Layout Shift

#### 6) SEO Impact

### 5. Improving your Core Web Vitals

#### 1) Introduction

#### 2) Lighthouse

#### 3) Image Optimization

#### 4) Dynamic Imports

#### 5) Dynamic Imports for Components

#### 6) Optimizing Fonts

#### 7) Optimizing Third-Party Scripts

### 6. Monitoring your Core Web Vitals

#### 1) Introduction

#### 2) Next.js Analytics

#### 3) Custom Reporting

#### 4) Data Studio

#### 5) Other Tools

#### 6) What To Learn Next

## Excel

### 1. Typescript

#### 1) Introduction

#### 2) Setup

#### 3) Create tsconfig.json

#### 4) Next.js Specific Types
