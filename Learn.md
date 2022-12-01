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

#### 2) Updating the UI with JavaScript and DOM Methods

#### 3) Getting Started with React

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
