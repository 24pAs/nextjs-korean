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
  우리는 블로그 페이지를 만들었지만(여기에 [결과가 있습니다](https://next-learn-starter.vercel.app/)) 블로그 내용을 아직 추가하지 못했습니다. 이번 과정에서 우리는 어떻게 외부의 블로그 데이터를 우리의 앱 안으로 들고 와야 할지에 대해 배울 예정입니다. 우리는 파일 시스템에 블로그 내용을 저장할 예정이지만 콘텐츠는 어디에 저장되어 있어도 상관없습니다.(e.g. database 혹은 Headless CMS)

**What You’ll Learn In This Lesson**

이번 과정에서 우리가 배울 내용은 아래와 같습니다: 

- Next.js의 [pre-rendering](https://nextjs.org/docs/basic-features/pages#pre-rendering)의 특징
- 두 가지 형태의 pre-rendering:  [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)과 [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)
- [데이터가 있는](https://nextjs.org/docs/basic-features/pages#static-generation-with-data) Static Generation과 [데이터가 없는](https://nextjs.org/docs/basic-features/pages#static-generation-without-data) Static Generation
- `[getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)` 와 index page에 외부 블로그 데이터를 가져오는 방법
- `[getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)` 와 관련된 몇가지 유용한 정보

만약 이전 과정부터 이어서 듣고 있다면 이 페이지는 넘어가도 좋습니다. 아래 버튼을 눌러 다음 페이지로 이동해주세요.

#### 2) Setup
  만약 이전 과정부터 이어서 듣고 있다면 이 페이지는 넘어가도 좋습니다. 아래 버튼을 눌러 다음 페이지로 이동해주세요. 

**Download Starter Code(Optional)** 

만약 이전 과정을 듣지 않았다면  아래에 있는 starter code를 다운받고 설치해서 실행해주세요. `nextjs-blog` 폴더는 이전 수업을 잘 들었다면 결과로 가지고 있을 코드입니다. 

다시한번 말하지만 지금 하는 작업은 이전 과정을 완료했다면 불필요한 작업입니다. 

```bash
npx create-next-app@latest nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/data-fetching-starter"
```

아래의 지시를 따라주세요. (`cd` 명령어를 통해 폴더로 들어가 개발 서버를 시작해주세요.)

그리고 아래의 파일들 또한 업데이트해주세요. 

- `public/images/profile.jpg` 에 여러분의 사진을 넣어주세요. (추천: 400px width/height).
- `components/layout.js` 에 있는 `const name = '[Your Name]'` 에 여러분의 이름을 적어주세요.
- `pages/index.js` 에 있는  `<p>[Your Self Introduction]</p>` 에 자기소개를 적어주세요.

#### 3) Pre-Rendering
  **Pre-rendering** 

[Data fetching](https://nextjs.org/docs/basic-features/data-fetching)에 대해서 이야기 하기 전에 Next.js의 가장 중요한 개념 중에 하나인 [Pre-rendering](https://nextjs.org/docs/basic-features/pages#pre-rendering)에 대해 이야기 해봅시다.

기본적으로 Next.js는 모든 페이지를 사전에 렌더링합니다. 즉 클라이언트 사이드에서 JavaScript가 모든 것을 하는 대신에 Next.js는 사전에 각각의 페이지를 위한 HTML을 생성한다는 뜻입니다.  Pre-rendering은 더 좋은 성능과 SEO를 가집니다. 

각각의 생성된 HTML은 페이지를 구성하는데 필요한 최소한의 JavaScript로 구성되어 있습니다. 브라우저에 의해 페이지가 로드되면 JavaScript 코드는 실행되며 페이지 전체에 상호작용을 할 수 있도록 만들어줍니다.(이 과정을 hydration이라고 합니다.) 

**Check That Pre-rendering Is Happening** 

아래와 같은 단계를 통해 pre-rendring이 일어났는지 확인할 수 있습니다.  

1. 브라우저에 JavaScript를 비활성화로 설정해주세요. ([Here's how in Chrome](https://developer.chrome.com/docs/devtools/javascript/disable/))
2. [이 페이지](https://next-learn-starter.vercel.app/) 접근에 시도해보세요.(튜토리얼의 최종 결과물입니다.)

여러분은 여러분의 앱이 JavaScript 없이도 렌더링되는 것을 확인할 수 있을 것입니다. Next.js는 정적인 HTML을 사전에 렌더링하므로 JavaScript  실행 없이도 앱의 UI가 화면에 보이는 것을 확인할 수 있습니다. 

> 참고 : 위 과정에서 `localhost`에 접속해서 시도해볼수도 있습니다. 하지만 Javascript가 비활성화 되어 있을 경우 CSS는 확인되지 않습니다.
> 

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
  Next.js는  [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended) 과 [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)이라는 두 가지 형태의 pre-rendering이 있습니다. 둘의 차이점은 페이지를 위한 HTML을 언제 생성하는 지 입니다. 

- [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)은 빌드 타임에 HTML을 생성하는 pre-rendering 메서드입니다. 사전에 생성된 HTML은 매 요청마다 재 요청됩니다.
- [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)은 매 요청 전에 HTML을 생성하는 pre-rendering 메서드입니다.

![image](https://user-images.githubusercontent.com/95066223/207740464-a6eeae30-d57f-45ba-96a5-f649a7d7e619.png)

![image](https://user-images.githubusercontent.com/95066223/207740491-d3242de7-66ba-4685-983b-4f6e909ede99.png)

> 개발모드(npm run dev 혹은 yarn dev 실행 시)에서는 모든 요청에 대해 페이지가 [pre-rendered](https://nextjs.org/docs/basic-features/pages#pre-rendering)됩니다. 이는 Static Generation에도 적용되며 이는 개발을 더 편하게 만들어줍니다. Production으로 이동 시 [Static Generation](https://nextjs.org/docs/basic-features/data-fetching/get-static-props#runs-on-every-request-in-development)은 모든 요청마다 일어나는 게 아니라 빌드 타임에 한번만 실행됩니다.
> 

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

반면에 만약 사용자의 요청 전에 페이지를 사전 렌더링할 수 없다면 [Static Generation](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)은 좋은 선택이 아닙니다.  아마 여러분의 페이지는 데이터를 빈번하게 업데이트하여 보여주고 페이지의 내용은 매 요청마다 바뀔 것입니다. 

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
> 

**Let’s Use `getStaticProps`**

사용하는 것을 배우면 더 쉽게 이해할 수 있을 것입니다. 그럼 다음페이지에서는 `[getStaticProps](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)`를 사용하여 블로그를 구현해보겠습니다.

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
