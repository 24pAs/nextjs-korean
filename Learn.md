<img src="https://camo.githubusercontent.com/f21f1fa29dfe5e1d0772b0efe2f43eca2f6dc14f2fede8d9cbef4a3a8210c91d/68747470733a2f2f6173736574732e76657263656c2e636f6d2f696d6167652f75706c6f61642f76313636323133303535392f6e6578746a732f49636f6e5f6c696768745f6261636b67726f756e642e706e67" />

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

리액트를 배우는 데 있어 가장 좋은 방법은 직접 구축해보는 것이다. 기존에 존재하는 웹 사이트에 <script>와 지금까지 배운 것들을 이용하여 작은 컴포넌트를 추가하는 것을 시작으로 리액트를 점차적으로 늘려나갈 수 있다. 하지만 많은 개발자들은 사용자와 개발자의 경험에 있어서 리액트가 전체 프론트엔드 프로젝트를 작성할 수 있을 정도록 가치가 있다는 것을 알게 되었다.

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

이것은 Next.js가 저수준 언어인 Rust로 만들어져 compilation, minification, bundling 등에 사용할 수 있는 플랫폼인  SWC라는 컴파일러를 가지고 있기 때문에 가능합니다.

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

번들링은 유저가 웹 페이지를 방문할 때 파일에 대한 수많은 요청을 줄이기 위해 웹의 의존성들을 해결하고 파일이나 모듈을  브라우저의 최적화된 번들로 병합(또는 패키징)하는 과정을 말합니다.

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
> 

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
> 

**Create a Next.js app**

Next.js 앱을 만들기 위해서는 터미널을 열고 앱을 만들 디렉토리에 가서 아래의 명령어를 실행해주세요. 

```bash
npx create-next-app@latest nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/learn-starter"
```

> 위의 코드는 Next.js 앱을 부팅하는 create-next-app이라는 도구를 사용합니다. —example 플래그를 통해 이 템플릿을 사용할 수 있습니다. 
해당 기능이 작동하지 않는다면 [이 페이지](https://github.com/vercel/next-learn/blob/master/basics/errors/install.md)에 가서 확인해주세요.
> 

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
> 

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
>

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
import Link from 'next/link';
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
import Link from 'next/link';

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

>Note: Next.js 12.2 버전 이전에는 `<a>` tag를 `<Link>` component를 감싸는 것이 필수였지만 12.2 이상부터는 필수가 아니다.
> 

작동하는지 확인하자. 각 페이지에 링크가 있고, 뒤와 앞으로 이동 할 수 있다.

![image](https://nextjs.org/static/images/learn/navigate-between-pages/links.gif)

#### 5) Client-Side Navigation
`Link` component는 같은 Next.js app 의 두개의 페이지 사이에서 clint-side navigation 할 수 있게 한다.

client-side navation의 의미는 javascript를 사용하여  브라우저가 수행하는 기본적인 navigation 보다 빠른 페이지의 transition(전환)을 일으키는 것을 말한다.

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

` in the API reference for next/link` 에서 `Link` component,  `in the routing documentation.`에서 routing을 더 학습 할수 있다. 

>Note: 만약 Next.js app 바깥의 외부 페이지 링크가 필요하다면 `<Link>` 없이 `<a>` tag를 사용하면 된다.

### 3. Assets, Metadata, and CSS

#### 1) Introduction

#### 2) Setup

#### 3) Assets

#### 4) Metadata

#### 5) Third-Party JavaScript

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

환경 설정 없이 바로 사용할 수 있는 Next.js는 [PostCSS](https://postcss.org/)를 사용하여 CSS를 컴파일합니다.

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

#### 2) Setup

#### 3) Pre-Rendering

#### 4) Two Forms of Pre-rendering

#### 5) Static Generation with and without Data

#### 6) Blog Data

#### 7) Implement getStaticProps

#### 8) getStaticProps Details

#### 9) Fetching Data at Request Time

### 5. Dynamic Routes

#### 1) Introduction

#### 2) Setup

#### 3) Page Path Depends on External Data

#### 4) Implement getStaticPaths

#### 5) Implement getStaticProps

#### 6) Render Markdown

#### 7) Polishing the Post Page

#### 8) Polishing the Index Page

#### 9) Dynamic Routes Details

### 6. API Routes

#### 1) Introduction

#### 2) Setup

#### 3) Creating API Routes

#### 4) API Routes Details

### 7. Deploying Your Next.js App

#### 1) Introduction

#### 2) Setup

#### 3) Push to GitHub

#### 4) Deploy to Vercel

#### 5) Next.js and Vercel

#### 6) Other Hosting Options

#### 7) Finally

## Search Engine Optimization

### 1. Introduction to SEO

#### 1) Introduction

#### 2) Importance of SEO

#### 3) Search Systems

#### 4) What are Webcrawlers?

### 2. Crawling and Indexing

#### 1) Introduction

#### 2) Status Codes

#### 3) Robots.txt

#### 4) XML Sitemaps

#### 5) Special Tags

#### 6) Canonical Tags

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
