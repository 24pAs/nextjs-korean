<img src="https://camo.githubusercontent.com/f21f1fa29dfe5e1d0772b0efe2f43eca2f6dc14f2fede8d9cbef4a3a8210c91d/68747470733a2f2f6173736574732e76657263656c2e636f6d2f696d6167652f75706c6f61642f76313636323133303535392f6e6578746a732f49636f6e5f6c696768745f6261636b67726f756e642e706e67" />



## 																		Next.js

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

#### 5) React Core Concepts

#### 6) Building UI with Components

#### 7) Displaying Data with Props

#### 8) Adding Interactivity with State

#### 9) How to continue learning React



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

