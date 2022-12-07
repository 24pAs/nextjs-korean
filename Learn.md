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
      const app = document.getElementById('app');
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
      const app = document.getElementById('app');

      // Create a new H1 element
      const header = document.createElement('h1');

      // Create a new text node for the H1 element
      const headerContent = document.createTextNode(
        'Develop. Preview. Ship. 🚀',
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
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const headerContent = document.createTextNode('Develop. Preview. Ship. 🚀');
  header.appendChild(headerContent);
  app.appendChild(header);
</script>
```

프로젝트나 팀의 크기가 커짐에 따라 이런 방식으로 애플리케이션을 빌드하는 것은 매우 어려워질 수 있습니다. 이러한 생각을 가지고 많은 개발자들은 어떻게 컴퓨터가 작동해야 하는지를 컴퓨터에게 알려주기 위해 많은 시간을 보냈습니다.

하지만 당신이 보여주고 싶은 것을 설명하고 컴퓨터가 DOM을 업데이트 하는 방법을 알게 하는 것이 좋지 않을까요?

#### Imperative vs Declarative Programming

위 코드는 명령형 프로그래밍의 좋은 예입니다. 당신은 어떻게 UI가 업데이트 되어야 하는지에 대한 과정을 적습니다.

하지만 UI를 구성하는 것에 관해서는 개발 프로세스를 빠르게 만들 수 있기 때문에 선언적인 접근이 선호됩니다. DOM method를 적는 것 대신, 개발자가 보여주고 싶은 것을 선언할 수 있다면 더욱 도움이 될 수 있습니다.(위 예시의 경우, 몇가지 단어가 포함된 `h1` 태그).

다시 말해, **선언형 프로그래밍**은 피자 만드는 방법을 하나하나 요리사가 지시하는 것과 같습니다. **명령형 프로그래밍**은 피자를 만드는 데 필요한 과정에 대해서는 생각하지 않고 그저 피자를 주문하는 것과 같습니다.

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
      const app = document.getElementById('app');
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
      const app = document.getElementById('app');
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

브라우저는 JSX를이해할 수 없다는 것을 기억하세요. 그렇기 때문에 당신은 JSX를 일반 JavaScript로 변환하기 위해  [Babel](https://babeljs.io/)과 같은 JavaScript 컴파일러가 필요합니다.

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
  const app = document.getElementById('app');
  const header = document.createElement('h1');
  const headerContent = document.createTextNode('Develop. Preview. Ship. 🚀');
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

자바스크립트 함수와 비슷하게 컴포넌트의 동작이나 화면에 렌더링 될 때 보여지는 내용을 변경하는 인자(혹은 props)를 받도록 컴포넌트를 설계할 수 있다.  그리고 이러한 props를 부모 컴포넌트에서 자식 컴포넌트로 전달할 수 있다. 

> 참고 : 리액트에서 데이터는 컴포넌트 트리 아래로 흐르며 이를 단방향 데이터 흐름이라고 한다. 다음 섹션에서 다룰 State는 부모에서 자식 컴포넌트로 전달된다.
> 

### Using props

우리는 HTML 속성을 전달하는 것과 비슷한 방식으로 `HomePage` 컴포넌트에서 `Header` 컴포넌트로 원하는대로 변경할 수 있는  `title` 속성을 넘길 수 있다. 

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

정의한 변수를 사용하기 위해서 일반 자바스크립트를 JSX 마크업 내에 직접 작성할 수 있도록 해주는 특수 JSX 구문인 중괄호를  사용할 수 있다. 

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
        return 'Default title';
      }
    }
    
    function Header({ title }) {
      return <h1>{createTitle(title)}</h1>;
    }
    ```
    
4. 삼항 연산자
    
    ```jsx
    function Header({ title }) {
      return <h1>{title ? title : 'Default Title'}</h1>;
    } 
    ```
    

이제 우리는 title props에 어떠한 문자열도 전달할 수 있으며 삼항 연산자를 이용하여 기본값을 할당하는 방법을 이용하면 title prop을 전달하지 않아도 된다. 

```jsx
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
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
> 

`HomePage` 컴포넌트에 이름으로 된 배열을 추가하겠습니다. 

```jsx
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

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
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

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
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

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
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

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
    console.log('increment like count');
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
> 

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

#### 2) From Development to Production

#### 3) Compiling

#### 4) Minifying

#### 5) Bundling

#### 6) Code Splitting

#### 7) Build Time vs. Runtime

#### 8) Client and Server

#### 9) Rendering

#### 10) CDNs and the Edge

#### 11) Next Steps

## Create Your First App

### 1 Create a Next.js App

#### 1) Introduction

#### 2) Setup

#### 3) Welcome to Next.js

#### 4) Editing the Page

### 2. Navigate Between Pages

#### 1) Introduction

#### 2) Setup

#### 3) Pages in Next.js

#### 4) Link Component

#### 5) Client-Side Navigation

### 3. Assets, Metadata, and CSS

#### 1) Introduction

#### 2) Setup

#### 3) Assets

#### 4) Metadata

#### 5) Third-Party JavaScript

#### 6) CSS Styling

#### 7) Layout Component

#### 8) Global Styles

#### 9) Polishing Layout

#### 10) Styling Tips

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
