<img src="https://camo.githubusercontent.com/f21f1fa29dfe5e1d0772b0efe2f43eca2f6dc14f2fede8d9cbef4a3a8210c91d/68747470733a2f2f6173736574732e76657263656c2e636f6d2f696d6167652f75706c6f61642f76313636323133303535392f6e6578746a732f49636f6e5f6c696768745f6261636b67726f756e642e706e67" />



## Next.js
---
### Documentation
- [Getting Started](#getting-started)
- [Basic Features](#basic-features)
  - [Pages](#pages)
  - [Data Fetching](#data-fetching)
    - [Overview](#overview)
    - [getServerSideProps](#getserversideprops)
    - [getStaticProps](#getstaticprops)
    - [getStaticPaths](#getstaticpaths)
    - [Incremental Static Regeneration](#incremental-static-regeneration)
    - [Client Side](#client-side)
  - [Built-in CSS Support](#built-in-css-support)
  - [Layouts](#layouts)
  - [Image Optimization](#image-optimization)
  - [Font Optimization](#font-optimization)
  - [Static File Serving](#static-file-serving)
  - [Fast Refresh](#fash-refresh)
  - [ESLint](#eslint)
  - [TypeScript](#typescript)
  - [Environment Variables](#environment-variables)
  - [Supported Browsers and Features](#supported-browsers-and-features)
  - [Handling Scripts](#handling-scritps)
- [Routing](#routing)
  - [Introduction](#introduction)
  - [Dynamic Routes](#dynamic-routes)
  - [Imperatively](#imperatively)
  - [Shallow Routing](#shallow-routing)
- [API Routes](#api-routes)
  - [Introduction](#introduction-1)
  - [Dynamic API Routes](#dynamic-api-routes)
  - [Request Helpers](#request-helpers)
  - [Response Helpers](#response-helpers)
  - [Edge API Routes](#edge-api-routes)
- [Going to Production](#going-to-production)
- [Deployment](#deployment)
- [Authentication](#authentication)
- [Testing](#testing)
- [Accessibility](#accessibility)
- [Guides](#guides)
  - [Building Forms](#building-forms)
- [Advanced Features](#advanced-features)
  - [Next.js Complier](#nextjs-compiler)
  - [Turbopack](#turbopack)
  - [Preview Mode](#preview-mode)
  - [Dynamic Import](#dynamic-import)
  - [Automatic Static Optimization](#automatic-static-optimization)
  - [Static HTML Export](#static-html-export)
  - [Absolute Imports and Module Path Aliases](#absolute-imports-and-module-path-aliases)
  - [Using MDX](#using-mdx)
  - [AMP Support](#amp-support)
    - [Introduction](#introduction-2)
    - [Adding AMP Components](#adding-amp-components)
    - [AMP in Static HTML Export](#amp-in-static-html-export)
    - [TypeScript](#typescript-1)
  - [Customizing Babel Config](#customizing-babel-config)
  - [Customizing PostCSS Config](#customizing-postcss-config)
  - [Custom Server](#custom-server)
  - [Custom APP](#custom-app)
  - [Custom Document](#custom-document)
  - [Custom Error Page](#custom-error-page)
  - [src Directory](#src-directory)
  - [CI Build Caching](#ci-build-caching)
  - [Multi Zones](#multi-zones)
  - [Measuring performance](#measuring-performance)
  - [Middlewares](#middleware)
  - [Debugging](#debugging)
  - [Error Handling](#error-handling)
  - [Source Maps](#source-maps)
  - [Codemods](#codemods)
  - [Internatinalized Routing](#internationalized-routing)
  - [Output File Tracing](#output-file-tracing)
  - [Security Headers](#security-headers)
  - [React 18](#react-18)
    - [Overview](#overview-2)
    - [Streaming SSR](#streaming-ssr)
    - [React Server Components](#react-server-components)
    - [Switchable Runtime](#switchable-runtiem)
- [Upgrade Guide](#upgrade-guide)
- [Migrating to Next.js](#migrating-to-nextjs)
  - [Incrementally Adopting Next.js](#incrementally-adopting-nextjs)
  - [Migrating fron Gatsby](#migrating-from-gatsby)
  - [Migrating from Create React App](#migrating-from-create-react-app)
  - [Migrating from React Router](#migrating-from-react-router)
- [FAQ](#faq)

---
## Getting Started

---
## Basic Features

- ### Pages

- ### Data Fetching

  - #### Overview

    <details >
      <summary>Examples</summary>
      <ul>

    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress">WordPress Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/blog-starter">Blog Starter using markdown files (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-datocms">DatoCMS Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-takeshape">TakeShape Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-sanity">Sanity Example (Demo)</a></li>
    ​	<li><a href="https://next-blog-prismic.vercel.app/">Prismic Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-contentful">Contentful Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-strapi">Strapi Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-prepr">Prepr Example (Demo)</a></li>
    ​	<li><a href="https://next-blog-agilitycms.vercel.app/">Agility CMS Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-cosmic">Cosmic Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-buttercms">ButterCMS Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-storyblok">Storyblok Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-graphcms">GraphCMS Example (Demo)</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-kontent">Kontent Example (Demo)</a></li>
    ​	<li><a href="https://static-tweet.vercel.app/">Static Tweet Demo</a></li>
    ​	<li><a href="https://github.com/vercel/next.js/tree/canary/examples/cms-enterspeed">Enterspeed Example (Demo)</a></li>

      </ul>
    </details>

    > **Note**
    >
    > Next.js 13버전은 `app/` 디렉토리(베타버전)를 소개합니다. 이 새로운 디렉터리는 새로운 React Hook과 확장된 웹 API를 사용하여 컴포넌트 수준에서 [colocated data fetching](https://beta.nextjs.org/docs/data-fetching/fundamentals)를 지원합니다. 

    Next.js에서 데이터를 가져오면 응용 프로그램의 사용 사례에 따라 다양한 방식으로 콘텐츠를 렌더링할 수 있습니다. 여기에는 **서버 측 렌더링(Sever Side Rendering)** 또는 **정적 생성(Static Generation)**을 사용하여 사전 렌더링하고, **증분 정적 재생(Incremental Static Regeneration)**을 사용하여 런타임에 콘텐츠를 업데이트하거나 생성하는 작업이 포함됩니다.

    #### [1. SSR: Server-side rendering](#getserversideprops)
      Next.js에서  `getServerSideProps`를 가지고 서버사이드 렌더링에 대해 알아보도록 합시다.
    #### [2. SSG: Static-site generation](#getstaticprops)
      Next.js에서  `getStaticProps`를 가지고 정적 사이트 생성에 대해 알아보도록 합시다.
    #### [3. CSR: Client-side rendering](#client-side)
      Next.js에서 `SWR`을 가지고 클라이언트 사이드 렌더링에 대해 알아보도록 합시다.
    #### [4. Dynamic routing](#getstaticpaths)
       Next.js에서  `getStaticPaths`를 가지고 동적 라우팅에 대해 알아보도록 합시다.
    #### [5. ISR: Incremental Static Regeneration](#incremental-static-regeneration)
       Next.js에서 증분 정적 생성에 대해 알아보도록 합시다.
    ## Learn more

    #### [1. Preview Mode](#preview-mode)
      Next.js에서 미리보기 모드에 대해 알아보도록 합시다.
    #### [2. Routing](#routing)
      Next.js에서 라우팅에 대해 알아보도록 합시다.
    #### [3. TypeScript](#typescript)
      우리 사이트에 TypeScript를 추가해보도록 합시다.

  - #### getServerSideProps
      만약 당신이 `getServerSideProps`라고 하는 함수를 페이지에서 `export`한다면 Next.js는 `getServerSideProps`가 반환하는 데이터를 사용해서 각각의 요청마다 페이지를 `pre-render`할 것입니다.

      ```javascript
        export async function getServerSideProps(context) {
          return {  
            props: {}, // will be passed to the page component as props
          }
        }
      ```
      > 렌더링 유형에 관계없이 모든 `props`는 page component로 전달되며 초기 HTML에서 클라이언트 측에서 볼 수 있습니다. 이는 페이지가 올바르게 [hydrate](https://reactjs.org/docs/react-dom.html#hydrate)할 수 있도록 하기 위함입니다. 클라이언트에서 사용할 수 없는 중요한 정보를 `props`로 전달하지 않도록 주의하세요.

      #### When does getServerSideProps run
      `getServerSideProps`는 브라우저에서 동작하는 것이 아닌 오직 서버 사이드에서만 동작합니다. 만약 페이지에서 `getServerSideProps`를 사용한다면 다음과 같습니다.

      ​

      - 해당 페이지에 직접적으로 요청할 때, `getServerSideProps`는 요청 시간(request time)에 동작합니다. 그리고 해당 페이지는 반환된 `props`를 가지고 사전에 렌더링됩니다.
      - 만약 `next/link`나 `next/router`를 통해 클라이언트 사이드의 페이지 전환을 통해 해당 페이지를 요청하게 되면 `Next.js`는 `getServerSideProps`를 실행하는 서버에 API 요청을 보냅니다.

      ​
      `getServerSideProps`는 페이지를 렌더링하는 데 사용될 JSON을 반환합니다. 이 모든 작업은 Next.js에 의해 자동으로 처리되므로 `getServerSideProps`를 정의하는 한 추가 작업을 수행할 필요가 없습니다.

      다음 [코드 제거 도구](https://next-code-elimination.vercel.app/)를 사용하여 Next.js가 클라이언트 측 번들에서 제거하는 항목을 확인할 수 있습니다.

      ​
      `getServerSideProps`는 오직 **페이지**에서만 `export` 할 수 있습니다. 페이지 파일이 아니면 `export`할 수 없습니다.

      ​
      반드시 `getServerSideProps`를 독립 실행형 함수로 내보내야 합니다. `getServerSideProps`를 페이지 구성 요소의 속성으로 추가하면 작동하지 않습니다.

      [getServerSideProps API 문서](https://nextjs.org/docs/api-reference/data-fetching/get-server-side-props)에는 getServerSideProps와 함께 사용할 수 있는 모든 매개 변수와 속성이 포함되어 있습니다.

      #### When should I use getServerSideProps
      요청 시 데이터를 가져와야 하는 페이지를 렌더링해야 하는 경우에만 `getServerSideProps`를 사용해야 합니다. 이는 데이터의 특성이나 요청 속성(예: 인증 헤더 또는 지리적 위치) 때문일 수 있습니다. `getServerSideProps`를 사용하는 페이지는 요청 시 서버 측에서 렌더링되며 [캐시 제어 헤더](https://nextjs.org/docs/going-to-production#caching)가 구성된 경우에만 캐시됩니다.

      요청하는 동안 데이터를 렌더링할 필요가 없는 경우 클라이언트 측에서 데이터를 가져오거나 `getStaticProps` 통해 데이터를 가져오는 것을 고려해야 합니다.

      ​
      **getServerSideProps or API Routes**

      서버에서 데이터를 가져온 다음 getServerSideProps에서 API 경로를 호출할 때 
      [API routes](https://nextjs.org/docs/api-routes/introduction)에 도달하는 방식을 시도할 수 있습니다. 서버에서 실행 중인 getServerSideProps와 API Routes로 인해 추가 요청이 발생하기 때문에 이는 불필요하고 비효율적인 접근 방식입니다.

      ​
      다음의 예를 들어보겠습니다 API 경로는 CMS에서 일부 데이터를 가져오는 데 사용되며, 이 API 경로는 getServerSideProps에서 직접 호출됩니다. 이렇게 하면 호출이 추가로 발생하여 성능이 저하됩니다. 대신 API Route 내에서 사용되는 로직을 `getServerSideProps`로 직접 가져오세요. 이는 `getServerSideProps` 내부에서 CMS, 데이터베이스 또는 기타 API를 직접 호출하는 것을 의미할 수 있습니다.

      ​

      **getServerSideProps with Edge API Routes**

      `getServerSideProps`는 서버리스와 Edge 런타임 환경에서도 사용될 수 있고 `props` 또한 설정할 수 있습니다. 그러나 현재 Edge Runtime에서 응답 객체(response object)에 액세스할 수 없습니다. 즉, 예를 들어 getServerSideProps에서 쿠키를 추가할 수 없습니다. 응답 객체에 액세스하려면 기본 런타임인 Node.js 런타임을 계속 사용해야 합니다.

      다음과 같이 구성을 수정하여 [페이지별로 런타임을 명시적](https://nextjs.org/docs/advanced-features/react-18/switchable-runtime#edge-api-routes)으로 설정할 수 있습니다:

      ```javascript
      export const config = {
        runtime: 'nodejs',
      }
      ```

      #### Fetching data on the client side

      페이지에 자주 업데이트되는 데이터가 포함되어 있고 데이터를 미리 렌더링할 필요가 없는 경우 클라이언트 측에서 데이터를 가져올 수 있습니다. 다음은 사용자별 데이터입니다:

      - 먼저, 데이터가 없는 페이지를 즉시 보여줍니다. 정적 생성(Static Generation)을 사용하여 페이지의 일부를 미리 렌더링할 수 있습니다.  결측 데이터에 대한 로드 상태를 표시할 수 있습니다.
      - 그런 다음 클라이언트 측에서 데이터를 가져와 준비되면 표시합니다.

      이 방법은 예를 들어 사용자 대시보드 페이지에서 잘 작동합니다. 대시보드는 개인 사용자별 페이지이므로 SEO는 관련이 없으며 페이지를 미리 렌더링할 필요가 없습니다. 또한 데이터는 자주 업데이트되므로 요청 시간 데이터 가져오기가 필요합니다.

      #### Using getServerSideProps to fetch data at request time

      다음 예제에서는 요청 시 데이터를 가져와 결과를 미리 렌더링하는 방법을 보여 줍니다.

      ```react
      function Page({ data }) {
        // Render data...
      }

      // This gets called on every request
      export async function getServerSideProps() {
        // Fetch data from external API
        const res = await fetch(`https://.../data`)
        const data = await res.json()

        // Pass data to the page via props
        return { props: { data } }
      }

      export default Page
      ```

      #### Caching with Server-Side Rendering(SSR)

      `getServerSideProps `내부에서 캐시 헤더(`Cache-Control`)를 사용하여 동적인응답을 캐시할 수 있습니다. 예를 들어, [`stale-while-revalidate`](https://web.dev/stale-while-revalidate/) 사용할 수 있습니다.

      ```react
      // This value is considered fresh for ten seconds (s-maxage=10).
      // If a request is repeated within the next 10 seconds, the previously
      // cached value will still be fresh. If the request is repeated before 59 seconds,
      // the cached value will be stale but still render (stale-while-revalidate=59).
      //
      // In the background, a revalidation request will be made to populate the cache
      // with a fresh value. If you refresh the page, you will see the new value.
      export async function getServerSideProps({ req, res }) {
        res.setHeader(
          'Cache-Control',
          'public, s-maxage=10, stale-while-revalidate=59'
        )

        return {
          props: {},
        }
      }
      ```

      [캐싱](https://nextjs.org/docs/going-to-production)에 대해 더 알아보려면 링크를 참고하세요.

      #### Dose getServerSideProps render an error page

      `getServerSideProps` 안에서 에러가 발생한다면 `pages/500.js` 파일을 보여줍니다. 어떻게 500 페이지를 만들고 배우는지는 [500 page](https://nextjs.org/docs/advanced-features/custom-error-page#500-page) 문서를 확인해보세요. 개발을 하는 동안 이 파일은 표시되지 않고 개발 오버레이가 대신 보여집니다.

      #### Related

      다음 작업에 대한 자세한 내용은 다음 섹션을 참조하십시오:

      [getServerSideProps API Reference](https://nextjs.org/docs/api-reference/data-fetching/get-server-side-props)

  - #### getStaticProps

      만약 당신이 `getStaticProps`(Static Site Generation)라고 하는 함수를 페이지에서 `export`한다면 Next.js는 `getStaticProps`가 반환하는 `props`를 사용하여 빌드 타임에 페이지는 미리 렌더링(pre-rendering) 합니다.

      ```react
      export async function getStaticProps(context) {
        return {
          props: {}, // will be passed to the page component as props
        }
      }
      ```

      > 렌더링 유형에 관계없이 모든 `props`는 page component로 전달되며 초기 HTML에서 클라이언트 측에서 볼 수 있습니다. 이는 페이지가 올바르게 [hydrate](https://reactjs.org/docs/react-dom.html#hydrate)할 수 있도록 하기 위함입니다. 클라이언트에서 사용할 수 없는 중요한 정보를 `props`로 전달하지 않도록 주의하세요.

      #### When should I use getStaticProps

      다음과 같은 경우 `getStaticProps`를 사용해야 합니다:

      - 페이지를 렌더링하기 위해 필요한 데이터가 사용자 요청 이전에 빌드타임에서 사용해야 하는 경우
      - headless CMS로부터 데이터가 오는 경우
      - SEO를 위해 페이지가 반드시 사전에 렌더링 되어야하고 매우 빨라야 하는 경우 - `getStaticProps`는 성능을 위해 CDN에 캐싱되는 HTML 파일과 JSON 파일을 생성합니다.
      - 데이터가 사용자별이 아닌 공개적으로 캐싱되어야 하는 경우. 이 조건은 특정 상황에서 미들웨어를 사용하여 경로를 재조정하면 무시할 수 있습니다.

      #### When does getStaticProps run

      `getStaticProps`는 항상 서버에서 실행이 되고 클라이언트에서는 절대 실행되지 않습니다. 이 [도구](https://next-code-elimination.vercel.app/)를 이용해서 클라이언트 사이드 번들에서 `getStaticProps`가 제거된 코드를 검증할 수 있습니다.

      - `getStaticProps`는 항상 `next build` 동안 실행됩니다.
      - `getStaticProps`는 `fallback: true` 옵션을 사용할 때 백그라운드에서 동작합니다.
      - `getStaticProps` 는 `fallback: blocking` 옵션을 사용할 때 초기 렌더링 이전에 호출됩니다.
      - `getStaticProps` 는 `revalidate`를 사용할 때 백그라운드에서 동작합니다.
      - `getStaticProps` 는 `revalidate()`를 사용할 때 백그라운드 안에서 on-demand로 동작합니다.

      [Incremental Static Regeneration](https://nextjs.org/docs/basic-features/data-fetching/incremental-static-regeneration)과 결합해서 `getStaticProps`를 사용하면 오래된 페이지가 재검증되고 새로운 페이지가 브라우저에서 제공되는 동안 백그라운드에서 실행됩니다.

      `getStaticProps`는 정적 HTML 파일을 생성하기 때문에 쿼리 파라미터나 HTTP Header와 같은 요청에 접근할 수 없습니다. 만약 요청에 접근하고 싶다면 `getStaticProps` 외에 [미들웨어](https://nextjs.org/docs/advanced-features/middleware)를 사용하는 것을 고려해보세요.

      #### Using getStaticProps to fetch data from a CMS

      다음 예제는 CMS로부터 블로그 게시글 목록을 어떻게 불러올 수 있는지를 보여주는 예제입니다.

      ```react
      // posts will be populated at build time by getStaticProps()
      function Blog({ posts }) {
        return (
          <ul>
            {posts.map((post) => (
              <li>{post.title}</li>
            ))}
          </ul>
        )
      }

      // This function gets called at build time on server-side.
      // It won't be called on client-side, so you can even do
      // direct database queries.
      export async function getStaticProps() {
        // Call an external API endpoint to get posts.
        // You can use any data fetching library
        const res = await fetch('https://.../posts')
        const posts = await res.json()

        // By returning { props: { posts } }, the Blog component
        // will receive `posts` as a prop at build time
        return {
          props: {
            posts,
          },
        }
      }

      export default Blog
      ```

      [getStaticProps API 문서](https://nextjs.org/docs/api-reference/data-fetching/get-static-props)에 `getStaticProps`가 사용할 수 있는 모든 파라미터와 `props`에 대해 나와있습니다.

      #### Write server-side code directly

      `getStaticProps`가 오직 서버사이드에 동작하기 때문에 클라이언트 사이드에서는 결코 동작하지 않습니다. 즉, 브라우저를 위한 자바스크립트 번틀에 포함이 되지 않습니다. 그래서 브라우저에 전송되지 않고 데이터베이스 쿼리를 직접 작성할 수 있습니다.

      즉, `getStaticProps`(자체적으로 외부 소스로부터 데이터를 가져오기)에서 API 경로를 가져오는 대신, `getStaticProps`에서 직접 서버 측 코드를 작성할 수 있습니다.

      다음의 예를 들어봅시다. API 경로는 CMS에서 일부 데이터를 가져오는 데 사용됩니다. 해당 API 경로는 getStaticProps에서 직접 호출됩니다. 이렇게 하면 호출이 추가로 발생하여 성능이 저하됩니다. 대신 lib/directory를 사용하여 CMS에서 데이터를 가져오는 로직을 공유할 수 있습니다. 그런 다음 getStaticProps와 공유할 수 있습니다.

      ```react
      // lib/load-posts.js

      // The following function is shared
      // with getStaticProps and API routes
      // from a `lib/` directory
      export async function loadPosts() {
        // Call an external API endpoint to get posts
        const res = await fetch('https://.../posts/')
        const data = await res.json()

        return data
      }

      // pages/blog.js
      import { loadPosts } from '../lib/load-posts'

      // This function runs only on the server side
      export async function getStaticProps() {
        // Instead of fetching your `/api` route you can call the same
        // function directly in `getStaticProps`
        const posts = await loadPosts()

        // Props returned will be passed to the page component
        return { props: { posts } }
      }
      ```

      또는 API 경로를 사용하여 데이터를 가져오지 않는 경우 `fetch()` API를 `getStaticProps`에서 직접 사용하여 데이터를 가져올 수 있습니다.

      다음 [코드 제거 도구](https://next-code-elimination.vercel.app/)를 사용하여 Next.js가 클라이언트 측 번들에서 제거하는 항목을 확인할 수 있습니다.

      #### Statically generates both HTML and JSON

      빌드 시 `getStaticProps`가 포함된 페이지가 미리 렌더링되면 페이지 HTML 파일 외에도 Next.js는 `getStaticProps`를 실행한 결과를 저장하는 JSON 파일을 생성합니다.

      이 JSON 파일은 `next/link `또는 `next/router`를 통한 클라이언트 측 라우팅에 사용됩니다. `getStaticProps`를 사용하여 사전 렌더링된 페이지로 이동하면 Next.js가 이 JSON 파일(빌드 시 사전 계산됨)을 가져와서 페이지 구성 요소의 `props`로 사용합니다. 이것은 내보낸 JSON만 사용되기 때문에 클라이언트 측 페이지 전환이 getStaticProps를 호출하지 않는다는 것을 의미합니다.

      증분 정적 생성(Incremental Static Regeneration)을 사용할 때 `getStaticProps`는 백그라운드에서 실행되어 클라이언트 측 탐색에 필요한 JSON을 생성합니다. 이는 동일한 페이지에 대해 여러 요청이 수행되는 형태로 나타날 수 있지만, 이는 의도된 것이며 최종 사용자 성능에 영향을 미치지 않습니다.

      #### Where can i use getStaticProps

      `getStaticProps`는 오직 페이지에서만 `export`될 수 잇습니다. 페이지가 아닌 파일이나 `_app`, `_document`, `_error` 페이지에서는 사용할 수 없습니다.

      이러한 제한의 이유들 중 한가지는 페이지가 렌더링되기 이전에 리액트에 필요한 모든 데이터를 가지고 있어야하기 때문입니다.

      또한, 반드시 `getStatocProps`를 독립 실행형 함수로 내보내야 합니다. `getStaticProps`를 페이지 구성 요소의 속성으로 추가하면 작동하지 않습니다.

      > 참고: 사용자 지정 앱을 만든 경우 링크된 [문서](https://nextjs.org/docs/advanced-features/custom-app)에 표시된 것처럼 pageProps를 페이지 구성 요소로 전달하고 있는지 확인하십시오. 그렇지 않으면 속성이 비어 있습니다.

      #### Runs on every request in development

      개발 환경에서(`next dev`) `getStaticProps`는 모든 요청에 호출됩니다.

      #### Preview Mode

      임시로 정적 생성(static generation)을 무시하고 [Preivew Mode](https://nextjs.org/docs/advanced-features/preview-mode)를 사용하여 빌드 시간 대신 요청 시 페이지를 렌더링할 수 있습니다. 예를 들어 헤드리스 CMS를 사용하는 경우 초안이 배포되기 전에 미리 보기를 원할 수 있습니다.

      #### Related

      다음 작업에 대한 자세한 내용은 다음 섹션을 참조하십시오:

      [getStaticProps API Reference](https://nextjs.org/docs/api-reference/data-fetching/get-static-props)

  - #### getStaticPaths

만약에 [Dynamic Routes](https://nextjs.org/docs/routing/dynamic-routes)인 페이지고 `getStaticProps` 를 사용중이라면 , 정적으로 생성된 path들의 list를 정의하는것이 필요합니다. 

dynamic routes를 사용한 페이지에서 `getStaticPaths` (SSG)라고 불리는 함수를 export 할때 , Next.js는 `getStaticPaths` 에 의해 구체화된 모든 paths들을 pre-render 할 것 입니다. 

```javascript
// pages/posts/[id].js

// Generates `/posts/1` and `/posts/2`
export async function getStaticPaths() {
  return {
    paths: [{ params: { id: '1' } }, { params: { id: '2' } }],
    fallback: false, // can also be true or 'blocking'
  }
}

// `getStaticPaths` requires using `getStaticProps`
export async function getStaticProps(context) {
  return {
    // Passed to the page component as props
    props: { post: {} },
  }
}

export default function Post({ post }) {
  // Render post...
}
```

`getStaticPaths` API reference는 [getStaticPaths](https://nextjs.org/docs/api-reference/data-fetching/get-static-paths)와 함께 사용할 수 있는 모든 매개 변수와 소도구를 다룹니다.

 When should I use getStaticPaths? 

Dynamic routes를 이용해서 정적으로 pre-rendering된 페이지를 getStaticPaths를 사용해서 만들 수 있습니다. 

- 데이터는 헤드리스 CMS에서 가져옵니다.
- 데이터는 데이터베이스에서 가져옵니다. 
- 데이터는 파일 시스템에서 가져옵니다. 
- 데이터는 공개적으로 캐시될 수 있습니다. 
- 페이지는 사전 렌더링(SEO)용 이어야 하며 매우 빨라야 합니다. `getStaticProps` 는 HTML과 JSON file을 생성하고 둘 다 CDN에 캐시될 수 있습니다. 



When does getStaticPaths run 

`getStaticPaths`는 프로덕션 환경에서만 동작할 것이고 runtime에서는 동작하지 않습니다. [도구](https://next-code-elimination.vercel.app/)를 사용하여 `getStaticPaths`안쪽에 쓰여진 코드를 validate하고 클라이언트 측 번들에서 제거되었는지 확인할 수 있습니다.

How does getStaticProps run with regards to getStaticPaths

- `getStaticProps` 는 `next build` 하는 동안 작동하고 , 모든 paths는 빌드 시간동안 반환된다.
- `getStaticProps` 는 `fallback : true` 일때 background에서 작동합니다. 
- `getStaticProps ` 는 `fallback : blocking` 일때 최초 render전에 불려집니다. 



Where can I use getStaticPaths 

- `getStaticPaths` 는 `getStaticProps`와 함께 사용해야합니다. 
- `getServerSideProps` 에서는 `getStaticPaths` 를 사용할 수 없습니다. 
- getStaticProps도 사용하는 [Dynamic Route](https://nextjs.org/docs/routing/dynamic-routes) getStaticPaths를 내보낼 수 있습니다.
- Page 파일이 아닌곳에서 `getStaticPaths` 를 export 할 수 없습니다. ( ex , components 폴더 )
- getStaticPaths를 페이지 구성 요소의 속성이 아닌 독립 실행형 함수로 내보내야 합니다.



Runs on every request in development

개발 모드( `next dev` )에서는 , `getStaticPaths` 는 모든 요청마다 불릴 것 입니다.



[Generating paths on-demand](https://nextjs.org/docs/basic-features/data-fetching/get-static-paths#generating-paths-on-demand)

`getStaticPaths`를 사용하면 on-demand 대체 대신 빌드 중에 생성되는 페이지를 제어할 수 있습니다. 많은 페이지를 빌드하는 시간동안 생성하는것은 빌드 속도가 느려집니다.

빈 배열 paths를 반환하면서 모든 페이지 생성을 연기할 수 있습니다. 이것은 nextjs가 여러 환경에서 배포할때 유용합니다. 예를 들어, 미리보기를 위한 모든 페이지를 온디맨드로 생성하여 빌드 속도를 높일 수 있습니다(실제 빌드 X). 이 기능은 정적 페이지가 수백/수천 개인 사이트에 유용합니다.

```javascript
// pages/posts/[id].js

export async function getStaticPaths() {
  // When this is true (in preview environments) don't
  // prerender any static pages
  // (faster builds, but slower initial page load)
  if (process.env.SKIP_BUILD_STATIC_GENERATION) {
    return {
      paths: [],
      fallback: 'blocking',
    }
  }

  // Call an external API endpoint to get posts
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // Get the paths we want to prerender based on posts
  // In production environments, prerender all pages
  // (slower builds, but faster initial page load)
  const paths = posts.map((post) => ({
    params: { id: post.id },
  }))

  // { fallback: false } means other routes should 404
  return { paths, fallback: false }
}
```




  - #### Incremental Static Regeneration


Next.js는 사이트가 빌드된 후에 업데이트하거나 만드는것을 허락합니다. ISR은 **전체 웹사이트의 재빌드없이** static-generation을 사용하는것을 가능하게 합니다. ISR을 사용하면 수백만 페이지로 확장하면서 정적의 이점을 유지할 수 있습니다. 

> 참고 : [`experimental-edge`](https://nextjs.org/docs/api-reference/edge-runtime) 런타임은 현재 ISR과 호환되지 않지만 `cache-control` 헤더를 수동으로 설정하여 `stale-while-revalidate`을 활용할 수 있습니다.

ISR을 사용하여 `getStaticProps`에 `revalidate`를 추가하세요.

```javascript
function Blog({ posts }) {
  return (
    <ul>
      {posts.map((post) => (
        <li key={post.id}>{post.title}</li>
      ))}
    </ul>
  )
}

// This function gets called at build time on server-side.
// It may be called again, on a serverless function, if
// revalidation is enabled and a new request comes in
export async function getStaticProps() {
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  return {
    props: {
      posts,
    },
    // Next.js will attempt to re-generate the page:
    // - When a request comes in
    // - At most once every 10 seconds
    revalidate: 10, // In seconds
  }
}

// This function gets called at build time on server-side.
// It may be called again, on a serverless function, if
// the path has not been generated.
export async function getStaticPaths() {
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // Get the paths we want to pre-render based on posts
  const paths = posts.map((post) => ({
    params: { id: post.id },
  }))

  // We'll pre-render only these paths at build time.
  // { fallback: blocking } will server-render pages
  // on-demand if the path doesn't exist.
  return { paths, fallback: 'blocking' }
}

export default Blog
```

요청된 페이지가 빌드 시간에 미리 만들어질때 , 최초로 캐시된 페이지를 보여줍니다. 

- 첫번째 요청 이후 10초 전에 페이지에 대한 모든 요청도 캐시되고 즉시 처리됩니다. 
- 10초 이후에는 , 다음 요청은 여전히 캐시된 페이지를 보여줄 것 입니다. 
- Next.js는 백그라운드에서 페이지를 재생성합니다.
- 페이지가 성공적으로 생성되면 Next.js는 캐시를 무효화하고 업데이트된 페이지를 표시합니다. 백그라운드 재생성이 실패해도 이전 페이지는 변경되지 않습니다. 

생성되지 않은 경로에 요청이 있을 때 Next.js는 첫 번째 요청 시 페이지를 서버에 렌더링합니다. 이후 요청은 캐시에서 정적 파일을 제공합니다. Vercel의 [ISR은 캐시를 전체적으로 유지하고 롤백](https://vercel.com/docs/concepts/incremental-static-regeneration/overview?utm_source=next-site&utm_medium=docs&utm_campaign=next-website)을 처리합니다.

> 참고 : 만약에 upstream data 공급자가 기본적으로 캐시를 가능하게 한다면 , 사용하지 않도록 설정해야 할 수 있습니다. (ex :`useCdn:false`) 그렇지 않으면 revalidation은 캐시를 업데이트하기 위해 새로운 데이터를 가져올 수 없습니다. 캐싱은 Cache-Control 헤더가 반환될때 CDN에서 할 수 있습니다. 



### On-demand Revalidation

만약에 `revalidate` 시간을 60초로 설정한다면 , 모든 방문자는 재생성된 버전의 페이지를 1분마다 볼 것 입니다. 캐시를 무효화하는 유일한 방법은 1분이 지난 후 해당 페이지를 방문하는 것입니다. `v12.2.0` 부터 Next.js는 On-Demand ISR을 지원하여 특정 페이지에 대한 캐시를 수동으로 제거합니다. 이것은 페이지를 더 쉽게 업데이트할 수 있습니다. 

- Headless CMS로부터 컨텐츠는 만들어지고 업데이트 된다. 
- 전자상거래 메타데이터 변경(가격, 설명, 범주, 리뷰 등)

`getStaticProps`안에서는 on-demand `revalidation`을 사용하기 위해 구체적으로 입력 할 필요가 없습니다.

만약에 `revalidate`가 제거됐다면 , Next.js는 기본적으로 `false` ( no revalidation )를 사용할것이고 `revalidate()` 가 불려질때만 페이지를 on-demand로 사용할 것 입니다. 

> 참고 : [미들웨어](https://nextjs.org/docs/advanced-features/middleware)는 On-Demand ISR 요청에 실행되지 않을 것입니다. 대신에 `revalidate()`를 호출하여 revalidate를 원하는 정확한 path를 요청할 수 있습니다.  `pages/blog/[slug].js`를 가졌고 `/post-1` -> `/blog/post-1`으로 다시 쓴다면 `res.revalidate('/blog/post-1')`를 부를 필요가 있습니다. 



### Using On-demand Revalidation

첫째로 , Next.js app에 비밀토큰을 만듭니다. 이 비밀 토큰은 revalidation API 경로에 대한 무단 액세스 방지하는데 사용됩니다. 다음 URL 구조를 사용하여 경로(수동 또는 웹 후쿠를 사용하여)에 액세스할 수 있습니다.

```
https://<your-site.com>/api/revalidate?secret=<token>
```

다음으로 , 애플리케이션에 [환경 변수](https://nextjs.org/docs/basic-features/environment-variables)를 추가합니다. 마침내 , revalidation API 경로를 만들어야 합니다.

```javascript
// pages/api/revalidate.js

export default async function handler(req, res) {
  // Check for secret to confirm this is a valid request
  if (req.query.secret !== process.env.MY_SECRET_TOKEN) {
    return res.status(401).json({ message: 'Invalid token' })
  }

  try {
    // this should be the actual path not a rewritten path
    // e.g. for "/blog/[slug]" this should be "/blog/post-1"
    await res.revalidate('/path-to-revalidate')
    return res.json({ revalidated: true })
  } catch (err) {
    // If there was an error, Next.js will continue
    // to show the last successfully generated page
    return res.status(500).send('Error revalidating')
  }
}
```

[demo](https://on-demand-isr.vercel.app/)에 on-demand revalidation을 보고 피드백을 제공해주세요. 

### Testing on-Demand ISR during development

`next dev`를 실행할 때 , `getStaticProps` 는 모든 요청에 포함됩니다. On-demand ISR을 올바르게 확인하기 위해서 , [production build](https://nextjs.org/docs/api-reference/cli#build)할 필요가 있고 [production server](https://nextjs.org/docs/api-reference/cli#production)를 시작해야합니다.

```
$ next build
$ next start
```

그리고 , 정적 페이지가 성공적으로 revalidate되는지 확인해야합니다. 

### Error handling and revalidation

만약에 백그라운드 재생을 다룰때 `getStaticProps` 안에 에러가 있거나 수도으로 에러를 던지면 마지막으로 성공적으로 생성된 페이지가 계속 표시됩니다. 이후 요청에서는 `getStaticProps`를 다시 부를 것 입니다.

```javascript
export async function getStaticProps() {
  // If this request throws an uncaught error, Next.js will
  // not invalidate the currently shown page and
  // retry getStaticProps on the next request.
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  if (!res.ok) {
    // If there is a server error, you might want to
    // throw an error instead of returning so that the cache is not updated
    // until the next successful request.
    throw new Error(`Failed to fetch posts, received status ${res.status}`)
  }

  // If the request was successful, return the posts
  // and revalidate every 10 seconds.
  return {
    props: {
      posts,
    },
    revalidate: 10,
  }
}
```

### Self - hosting ISR

ISR은 `next start`를 사용할때 자체 호스팅된 Next.js 사이트에서 작동합니다.

[Kubernetes](https://kubernetes.io/)나 [HashiCorp Nomad](https://www.nomadproject.io/)를 통해 container orchestrators를 배포하면 접근할 수 있습니다. 기본적으로 생성된 assets는 각 pod에 인메모리에 저장될 것 입니다. 각 pod는 정적 파일 자체 복사본을 가집니다. 특정 포드가 요청에 의해 히트할 때까지 오래된 데이터가 표시될 수 있습니다. 

모든 pods를 끊임없이 유지하기 위해 인메모리 캐싱을 비활성화 할 수 있습니다. 이렇게하면 Next.js 서버가 파일 시스템에서 ISR에 의해 생성된 자산만 활용하도록 알립니다.

인메모리 캐싱을 비 활성화하기위해 `next.config.js` 파일에 `isrMemoryCacheSize`를 `0`으로 설정합니다. 

```javascript
module.exports = {
  experimental: {
    // Defaults to 50MB
    isrMemoryCacheSize: 0,
  },
}
```

> 참고 : 공유 마운트를 구성하는 방법에 따라 캐시를 동시에 업데이트하려는 다수의 pods간의 경쟁 상태를 고려해야할 수 있습니다. 



### Related

다음 작업에 대한 내용은 다음 section을 참고해주세요.



  - #### Client Side
## Client-side data fetching

Client-side 데이터 패칭은 해당 페이지가 SEO를 요구하지 않을때  , 데이터를 pre-render하지 않을때나 , 페이지의 컨텐츠를 자주 업데이트해야할때 유용합니다. server-side rendering API와 달리 client-side는 컴포넌트 레벨에서 데이터 패칭이 가능합니다. 

만약에 페이지레벨에서 해야한다면 , 데이터는 런타임에 패치되고 데이터가 변할때마다 페이지가 업데이트 됩니다. 컴포넌트 레벨에서 사용할 경우에는 데이터는 컴포넌트가 마운트될시 패치되 데이터가 변화할때마다 업데이트 됩니다. 

Client-side 데이터 패칭은 페이지 로드속도와 어플리케이션 퍼포먼스에 영향을 끼칠 수 있음을 알아야 합니다. 왜냐하면 데이터 패칭은 캐쉬되지 않고 마운트되는 시점에 수행되기 때문입니다. 



### Client-side data fetching with useEffect

아래 예제를 따라서 useEffect hook을 사용해서 어떻게 데이터 패칭을 하는지 알아봅시다.

```js
import { useState, useEffect } from 'react'

function Profile() {
  const [data, setData] = useState(null)
  const [isLoading, setLoading] = useState(false)

  useEffect(() => {
    setLoading(true)
    fetch('/api/profile-data')
      .then((res) => res.json())
      .then((data) => {
        setData(data)
        setLoading(false)
      })
  }, [])

  if (isLoading) return <p>Loading...</p>
  if (!data) return <p>No profile data</p>

  return (
    <div>
      <h1>{data.name}</h1>
      <p>{data.bio}</p>
    </div>
  )
}

```

###  [Client-side data fetching with SWR](https://nextjs.org/docs/basic-features/data-fetching/client-side#client-side-data-fetching-with-swr)

Next.js 팀은 **SWR**이라는 데이터 패칭 React Hook 라이브러리를 만들었습니다. 이것은 client-side 데이터 패칭 방식을 사용할때 매우 추천드립니다. caching , revalidation , focus tracking , refetching on intervals 를 지원합니다. 

위와 같은 예를 사용하여 SWR을 사용하여 프로파일 데이터를 가져올 수 있습니다. SWR은 자동으로 데이터를 캐시하고 오래된 데이터가 되면 데이터를 다시 확인합니다.

SWR을 사용해 더 많은 정보를 알고 싶다면 [SWR docs](https://swr.vercel.app/docs/getting-started)를 확인하세요.

```javascript
import useSWR from 'swr'

const fetcher = (...args) => fetch(...args).then((res) => res.json())

function Profile() {
  const { data, error } = useSWR('/api/profile-data', fetcher)

  if (error) return <div>Failed to load</div>
  if (!data) return <div>Loading...</div>

  return (
    <div>
      <h1>{data.name}</h1>
      <p>{data.bio}</p>
    </div>
  )
}
```





- ### Built-in CSS Support

- ### Layouts

- ### Image Optimization

>Examples
> 
>[Image Component](https://github.com/vercel/next.js/tree/canary/examples/image-component)
>

Next.js Image Component, `next/image`, 는 HTML `img' 태그의 확장이며 모던웹에 맞게 발전시켰다. 
이것은 우수한 [Core Web Vitals](https://nextjs.org/learn/seo/web-performance)를 성취할 수록 도움을 주는 다양한 내장형 성능 최적화를 포함한다. 
이 점수들은 당신의 웹사이트에서 사용자 경험의 중요한 측정치이고, [Google의 검색 랭킹에서 하나의 중요한 요인](https://nextjs.org/learn/seo/web-performance/seo-impact)이다.

Image component에 내장된 몇몇의 최적화에 다음이 포함된다:

-Improved Performance(개선된 성능): 항상 각 디바이스를 위한 알맞은 사이즈의 이미지를 전달하고, 모던 이미지 포맷을 사용

-Visual Stability(시각의 안정성):   [Cumulative Layout Shift](https://github.com/24pAs/nextjs-korean/blob/main/Learn.md#5-cumulative-layout-shift) 자동으로 방지

-Faster Page Loads(더 빠른 페이지 로드): 이미지들이 viewport에 진입했을때에만 로드되고 옵션으로 blur-up placeholders를 사용할수있다.

-Asset Flexibility(자산 유연성): 원격 서버에 저장된 이미지에 대해서도 필요에 따라 이미지 크기 조정이 가능합니다.

#### Using the Image Component

어플리케이션에 이미지를 추가할때 다음과 같이 `next/image` component 를 import 한다:
```jsx
import Image from 'next/image'
```
지금 이미지의 `src`를 정의할 수 있다(local 또는 원격 둘다).

##### Local Images

local 이미지를 사용하기 위해서 다음과 같이 `.jpg`, `.png`, `.webp` 파일들을 import 한다:

```js
import profilePic from '../public/me.png'
```

동적으로 `await import()` 또는 `reqire()`을 지원하지 않는다. `import`는 반드시 정적이여야 해서 빌드 타임때 분석할 수 있다.

Next.js 는 import된 파일을 기반으로 이미지의 `width`와 `height`를 자동적으로 결정한다. 이 값들은 이미지가 로딩할때마다 [Cumulative Layout Shift](https://nextjs.org/learn/seo/web-performance/cls) 를 방지하기 위해 사용된다.

```jsx 
import Image from 'next/image'
import profilePic from '../public/me.png'

function Home() {
  return (
    <>
      <h1>My Homepage</h1>
      <Image
        src={profilePic}
        alt="Picture of the author"
        // width={500} automatically provided
        // height={500} automatically provided
        // blurDataURL="data:..." automatically provided
        // placeholder="blur" // Optional blur-up while loading
      />
      <p>Welcome to my homepage!</p>
    </>
  )
}
```

##### Remote Images

remote 이미지들을 사용하기 위해선 `src` property에 상대 또는 절대 가능한 URL 문자는 반드시 있어야 한다.
Next.js는 빌드 프로세스 동안 원격 파일에 접근 할 수 없기 때문에,  `width`, `height', 그리고 옵션 `blurDataURL` props를 다음과 같이 수동으로 제공해야할 필요가 있다.

```jsx
import Image from 'next/image'

export default function Home() {
  return (
    <>
      <h1>My Homepage</h1>
      <Image
        src="/me.png"
        alt="Picture of the author"
        width={500}
        height={500}
      />
      <p>Welcome to my homepage!</p>
    </>
  )
}
```

> `next/image` 에서 [sizing requirements](https://nextjs.org/docs/basic-features/image-optimization#image-sizing) 에 대하여 더 배워보자

##### Domains

때떄로 원격 이미지가 최적화 되길 바란지만, 내장된 Next-js Image Optimization API 를 사용하면 된다. 
이것을 위해, 기본 설정에 `loader` 를 두고 Image `src` prop 에 절대 URL을 입력해라.

>[`remotePatterns`](https://nextjs.org/docs/api-reference/next/image#remote-patterns) 설정을 더 배워보자.

##### Loaders

이전 [예](https://nextjs.org/docs/basic-features/image-optimization#remote-images)에서 일부의 URL(`/me.png`)은 원격 이미지를 위해 제공됐다. 이것은 로더 아키텍쳐로 인해 가능하다.

loader는 이미지를 위해 URLs를 생성하는 함수이다. 이것은 제공된 `src` 를 변경하고, 다른 사이즈들로 이미지들을 요청 위해 여러개의 URLs 로 생성한다.
이 여러 URL들은 자동 [srcset](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/srcset) 생성에서 사용되어서 사이트에 방문한 사용자들은 그들의 viewprot에 알맞은 사이즈를 가진 이미지를 제공받을 것이다.

Next.js 어플리케이션을 위한 기본 loader는 내장된 Image Optimization API를 사용하고, 웹 모든 곳의 이미지들을 최적화 하여 Next.js web server 로 부터 사용자에게 직접 전달된다.
만약 CDN 또는 이미지 서버로 부터 직접 이미지들을 제공받고 싶어한다면, 몇줄의 javascript로 되어있는 당신의 loader 함수를 쓸수 있다.

`loader` prop와 함께 image 당 로더를 정의할 수 있거나 어플리케이션 단위로 [`loaderFile`](https://nextjs.org/docs/api-reference/next/image#loader-configuration) 설정을 정의 할 수 있다.

##### Priority
당신은 `priority` property를 각 페이지에서 [Largest Contentful Paint (LCP) element](https://web.dev/lcp/#what-elements-are-considered) 가 될 이미지에 반드시 추가해야한다.
이렇게 하면 Next.js에서 이미지 로딩(예: preload tags를 통하거나 우선 순위 힌트)에 특별한 우선 순위로 설정하여, LCP에서 의미있는 향상을 만들 수 있다.

LCP element는 전형적으로 페이지의 viewport에서 보이는 제일큰 이미지 이거나, 텍스트 블록이다.
`next dev`를 실행할 시, 만약 LCP element가 `priority` property가 없는 `<Image>` 라면 console warning을 보게 될 것이다.

LCP 이미지를 확인한적이 있다면, 다음과 같이 property를 추가할 수 있다:

```jsx
import Image from 'next/image'

export default function Home() {
  return (
    <>
      <h1>My Homepage</h1>
      <Image
        src="/me.png"
        alt="Picture of the author"
        width={500}
        height={500}
        priority
      />
      <p>Welcome to my homepage!</p>
    </>
  )
}
```

[`next/image` component documentation](https://nextjs.org/docs/api-reference/next/image#priority) 에서 priority 에 대해 더 알아보자.

#### Image Sizing

이미지들이 가장 일반적으로 성능을 상하게 하는 하나의 길은 layout shift를 통하고, 여기서 이미지들이 로드 될때 다른 element 들을 푸쉬한다.(압박?)
이 성능 문제는 사용자를 너무 성가셔  Core Web Vital에는 [Cumulative Layout Shift](https://web.dev/cls/)라고 불린다.
이미지 기반 layout shift를 피할 방법은 항상 당신의 이미지들의 크기를 재는 것이다. 이렇게 하면 브라우저는 이미지가 로드되기 전에 정확하게 충분한 공간을 남겨 놓는다.

그 이유는 `next/image`는 우수한 성능 결과를 보증하도록 설계되었고, layout shift 에 기여되는 방식으로 사용할 수 없으며, 다음 꼭 세가지 방법중 하나로 크기를 측정한다.

1. Automatically(자동적), 정적 import 에 사용
2. Explicitly(명시적), `width`와 `height` property를 포함하여
3. Implicitly(절대적), [fill](https://nextjs.org/docs/api-reference/next/image#fill) 를 사용하여  이미지를 부모 element에 확장하고 채운다. 

> 이미지 사이즈를 모른다면?
> 
> 만약 이미지 사이지의 정보가 없는 소스로 부터 이미지들에 접근했다면, 아래와 같이 몇가지 할수 있는게 있다:
> 
> Use `fill`
> 
> `fill` prop은 이미지가 부모 element에 의해 크기가 측정된다. CSS를 사용하여 모든 media query break points에 일치하는 페이지의 `sizes` prop에 따라 부모의 element에 공간을 주는 것을 고려해라. 
> `object-fit` 에 `fill`, `contain` 또는 `cover` 를 사용하고, `object-position`를 사용해서 그 공간을 이미지가 매우는 방법을 정의할 수 있다.
> 
> Normalize your images
> 
>제어하는 소스로부터 이미지를 제공할 경우, 일정한 사이지로 이미지를 표준하는 이미지 파이프 라인을 수정하는 것을 고려해라.
>
>Modify your API calls
> 
> 만약 어플리케이션이 API call(cms와 같은)을 사용하여 이미지 URL들을 회수한다면, URL과 함께 이미지 치수를 함께 리턴하는 API call을 수정할 수 있을 것이다.
> 
제안된 방법 중 이미지 크기 조정에 적합한것이 없다면  `next/image` component는 표준의 `<img>` elements 와 함께 페이지에서 잘 작동하도록 설계되었다.

#### Styling
image component 스타일링은 보통 `<img>` element에 스타일링 하는것과 유사해 보이지만, 아래의 몇가지 지침을 명심해야한다:

**Use `className` or `style`, not `styled-jsx`**

많은 케이스에서, `className` prop를 사용하는 것을 추천한다. 이것은 [CSS Module](https://nextjs.org/docs/basic-features/built-in-css-support#adding-component-level-css), [global stylesheet](https://nextjs.org/docs/basic-features/built-in-css-support#adding-a-global-stylesheet), 기타를 import 할 수 있게한다.

inline styles로 `style` prop 를 사용할 수 있다.

[styled-jsx](https://nextjs.org/docs/basic-features/built-in-css-support#css-in-js) 를 사용할 수 없는데, 현재 component에 지정 되어있기 때문이다.(스타일을 `global`으로 표시하지 않는 한)

**`fill`을 사용할시, 부모 element는 `position: relative`를 꼭 가져야 한다.**

layout mode에서 이미지 element의 알맞은 렌더링을 위해 필요하다.

**`fill`을 사용할시, 부모 element는 `display: block` 을 꼭 가져야한다. **

이것은 `div` element는 기본이지만, 그렇지 않으면 지정해야한다.

#### Properties

[`next/image` component 에 사용가능한 모든 property를 보자](https://nextjs.org/docs/api-reference/next/image)

##### Styling Examples

image component가 다양한 스타일을 사용한 예는 [Image Component Demo](https://image-component.nextjs.gallery/)를 보자

#### Configuration

`next/image` component 와 Next.js Image Optimization API 는 [`next.config.js` 파일](https://nextjs.org/docs/api-reference/next.config.js/introduction)에서 구성할 수 있다. 
이 구성들을 사용하면 [원격 이미지들을 사용](https://nextjs.org/docs/api-reference/next/image#remote-patterns), [이미지 breackpoints 맞춤 정의](https://nextjs.org/docs/api-reference/next/image#device-sizes), [캐싱 동작 변경](https://nextjs.org/docs/api-reference/next/image#caching-behavior) 그리고 더 많은 것들을 가능케 한다.

[더 많은 정보를 위해 전체 image configuration documentation 읽자](https://nextjs.org/docs/api-reference/next/image#configuration-options)

#### Related

다음에 작업에 대한 자세한 내용은 다음 섹션을 참조하자.

[`next/image`](https://nextjs.org/docs/api-reference/next/image)


- ### Font Optimization

`@next/font`는 폰트를(custom font 포함)을 자동으로 최적화하고 개인 정보 보호와 성능을 위해 외부 네트워크 요청을 삭제한다.

>Watch: `@next/font` 사용하는 방법에 대해 더 배우자. -> [YouTube(6 minutes)](https://www.youtube.com/watch?v=L8_98i_bMMA)

#### Overview

`@next/font` 는 모든 폰트 파일을 위해 built-in automatic self-hosting 을 포함한다. 이는 기본적인 CSS 크기 조정 속성 덕분에 zero layout shift 와 함께 웹 폰트를 최적화 로드할수 있다는 것을 의미한다.

새로운 폰트 시스템은 Google fonts를 성능과 개인 정보 보호를 염두에 두고 편리하게 사용할 수 있도록 한다.
CSS 와 폰트 파일은 빌드타임때 다운로드 되고 정적 자산의 나머지와 함께 self-hosted 한다. 브라우저로 Google에 보내는 리퀘스트는 없다.

#### Usage

시작하려면 다음과 같이 `@next/font`를 설치한다:

```zsh
npm install @next/font
```

##### Google Fonts

자동으로 모든 Google Font를 self-host한다. 
폰트들은 배포에 포함되어 있고, 배포와 동일한 도메인으로 제공된다. 브라우저로 Google에 보내는 요청은 없다.

`@next/font/google` 함수를 사용하여 폰트를 import 하자. 우수한 성능과 유연함을 위해 [variable fonts](https://fonts.google.com/variablefonts)를 사용하는 것을 추천한다.

모든 페이지에서 폰트를 사용하기 위해선 아래와 같이 `/pages` 아래에 `_app.js`file에 추가한다.

```jsx
// pages/_app.js
import { Inter } from '@next/font/google'

// If loading a variable font, you don't need to specify the font weight
const inter = Inter({ subsets: ['latin'] })

export default function MyApp({ Component, pageProps }) {
  return (
    <main className={inter.className}>
      <Component {...pageProps} />
    </main>
  )
}
```

만약 다양한 폰트를 사용하지 못한다면, weight(무게)를 지정해야 할 필요가 있다.
```jsx
// pages/_app.js
import { Roboto } from '@next/font/google'

const roboto = Roboto({
  weight: '400',
  subsets: ['latin'],
})

export default function MyApp({ Component, pageProps }) {
  return (
    <main className={roboto.className}>
      <Component {...pageProps} />
    </main>
  )
}

```

여러개의 weights(무게) 그리고/또는 styles 를 array를 사용하여 지정할 수 있다:
```js
const roboto = Roboto({
  weight: ['400', '700'],
  style: ['normal', 'italic'],
  subsets: ['latin'],
})
```

###### Apply the font in `<head>`

wrapper과 `className` 없이 다음과 같이 `<head>`안에서 주입하여 폰트를 사용할 수 있다.

```jsx
// pages/_app.js
import { Inter } from '@next/font/google'

const inter = Inter({ subsets: ['latin'] })

export default function MyApp({ Component, pageProps }) {
  return (
    <>
      <style jsx global>{`
        html {
          font-family: ${inter.style.fontFamily};
        }
      `}</style>
      <Component {...pageProps} />
    </>
  )
}
```

###### Single page usage

싱글 페이지에서 폰트를 사용하기 위해, 아래와 같이 지정한 페이지에 추가한다.
```jsx
// pages/index.js
import { Inter } from '@next/font/google'

const inter = Inter({ subsets: ['latin'] })

export default function Home() {
  return (
    <div className={inter.className}>
      <p>Hello World</p>
    </div>
  )
}
```

###### Specifying a subset

Google Fonts는 자동 [subset](https://fonts.google.com/knowledge/glossary/subsetting)이다.
폰트 파일의 사이즈를 재구성(압축)하고 성능을 개선한다.
이러한 subsets중 preload하기를 원하는 것을 정의할 필요가 있다.
`preload`가 true일때마다  모든 subset을 지정하지 못하면 경고가 발생할 것이다.

아래와 같이 두가지 방법에서 수행할 수 있다:

- 함수를 호출을 추가하여 글꼴 별로 글꼴 단위로
```js
// pages/_app.js
const inter = Inter({ subsets: ['latin'] })
```

- `next.config.js` 에서 모든 폰트를 전역화
```js
// next.config.js
module.exports = {
  experimental: {
    fontLoaders: [
      { loader: '@next/font/google', options: { subsets: ['latin'] } },
    ],
  },
}
```
- 둘다 설정되어있으면, 함수 호출안의 subset을 사용한다.

더 많은 정보를 위해 [Font API Reference](https://nextjs.org/docs/api-reference/next/font#nextfontgoogle)를 보자


##### Local Fonts

`@next/font/local`을 import 하고 local 폰트 파일의 src를 지정하자. 우리는 최고의 성능과 유연함을 위해 [variable fonts](https://fonts.google.com/variablefonts)를 추천한다.

```js
// pages/_app.js
import localFont from '@next/font/local'

// Font files can be colocated inside of `pages`
const myFont = localFont({ src: './my-font.woff2' })

export default function MyApp({ Component, pageProps }) {
  return (
    <main className={myFont.className}>
      <Component {...pageProps} />
    </main>
  )
}
```
단일 font family를 위한 여러개의 파일을 사용하길 원하다면 `src`는 array로 할 수 있다.

```js
const roboto = localFont({
  src: [
    {
      path: './Roboto-Regular.woff2',
      weight: '400',
      style: 'normal',
    },
    {
      path: './Roboto-Italic.woff2',
      weight: '400',
      style: 'italic',
    },
    {
      path: './Roboto-Bold.woff2',
      weight: '700',
      style: 'normal',
    },
    {
      path: './Roboto-BoldItalic.woff2',
      weight: '700',
      style: 'italic',
    },
  ],
})
```
더 많은 정보를 위해 [Font API Reference](https://nextjs.org/docs/api-reference/next/font#nextfontlocal)를 보자.

#### With Tailwind CSS

`@next/font`는 CSS 변수들에 통한 Tailwind CSS 와 함께 사용할 수 있다.

다음 예제에서, `@next/font/google`(모든 google의 폰트나 local 폰트들을 사용 가능하다.) 로 부터 `Inter` 폰트를 사용한다.
변수 옵션으로 폰트가 로드되고, CSS 변수 이름을 정의하고, 이를 `inter`에 할당한다. 
그리고나서, `inter .variable`를 사용하여 HTML document에 CSS 변수를 추가한다.
```js
// pages/_app.js
import { Inter } from '@next/font/google'

const inter = Inter({
  subsets: ['latin'],
  variable: '--font-inter',
})

export default function MyApp({ Component, pageProps }) {
  return (
    <main className={`${inter.variable} font-sans`}>
      <Component {...pageProps} />
    </main>
  )
}
```

마지막으로, [Tailwind CSS config](https://github.com/vercel/next.js/tree/canary/examples/with-tailwindcss)에 CSS 변수를 추가할 수 있다.

```js
// tailwind.config.js
const { fontFamily } = require('tailwindcss/defaultTheme')

/** @type {import('tailwindcss').Config} \*/
module.exports = {
  content: [
    './pages/**/*.{js,ts,jsx,tsx}',
    './components/**/*.{js,ts,jsx,tsx}',
  ],
  theme: {
    extend: {
      fontFamily: {
        sans: ['var(--font-inter)', ...fontFamily.sans],
      },
    },
  },
  plugins: [],
}

```

이제 `font-sans` utility class를 사용하여 element에 폰트를 적용할 수 있다.

#### Preloading

사이트의 페이지에서 폰트 함수를 호출할때, 이것은 전역적으로 사용할 수 없고 모든 라우트에서 preload 되었다.
오히려, 폰트는 사용하는 파일의 타입에 따라서 관계된 라우트에서만 사전 로드된다.

- 만약 [unique page](https://nextjs.org/docs/basic-features/pages)라면, 해당 페이지의 unique route에만 preload 된다.
- 먼역 [custom App](https://nextjs.org/docs/advanced-features/custom-app)이라면, `/pages` 아래 사이트이 모든 route 에서 preload 된다.

#### Reusing fonts

`localFont` 또는 Google 폰트 함수를 호출할 모든 시간마다, 어플리케이션에서 하나의 인스턴스로 호스트 된다.
그러므로 여러 파일에서 같은 폰트 함수로 로드하고 있다면 같은 폰트의 여러개 인스턴스들이 호스트 된다. 
이런 경우, 아래와 같이 하길 추천한다.

- 하나의 공유 파일에서 font loader 함수를 호출
- 상수로 Export
- 폰트를 사용하려고 하는 각 파일에서 상수를 import

#### Next Steps

[Font API Reference](https://nextjs.org/docs/api-reference/next/font)
[Image Optimization](https://nextjs.org/docs/basic-features/image-optimization)

- ### Static File Serving
Next.js는 root 디렉토리에 `public` 폴더 아래에서 이미지같은 static 파일들을 관리 할 수 있습니다. `public` 안쪽에 파일은 URL(`/`)로 시작하여 접근 할 수 있습니다.

예를 들어 , 만약에 public/me.png 이미지를 추가하려면 , 아래와 같은 코드는 이미지에 접근 할 수 있습니다.

```js
import Image from 'next/image'

function Avatar() {
  return <Image src="/me.png" alt="me" width="64" height="64" />
}

export default Avatar
```

> 참고 : `next/image`는 Next.js 10이후에 도입됐습니다. 

이 폴더는 `robots.txt` , `favicon.ico` , 구글 사이트 검증 등 모든 static 파일( `html`을 포함하여 )에 유용합니다.

> **참고** : 폴더 이름은 확실하게 `public`이여야 합니다. 폴더 이름은 변할 수 없고 , 오직 정적인 파일들만 관리해야 합니다. 

> **참고** : 페이지 디렉토리 안에 같은 이름의 정적인 파일이 없도록 해야합니다. 이것은 에러의 결과를 가집니다. 
>
> Read more: https://nextjs.org/docs/messages/conflicting-public-file-page

> **참고** : Next.js는 [빌드 타임](https://nextjs.org/docs/api-reference/cli#build)에 `public` 폴더 안에 assets들을 제공합니다. 런타임에 추가된 것은 이용할 수 없습니다. 우리는 [AWS S3](https://aws.amazon.com/ko/s3/)와 같은 저장소를 추천합니다. 


- ### Fash Refresh
Fast Refresh는 Next.js에 기능이고 이 기능은 리액트 컴포넌트를 수정할때 즉각적인 피드백을 줍니다. Fast Refresh는 Next.js **9.4 버전** 부터 가능합니다. Next.js Fast Refresh를 사용하면 **컴포넌트 상태를 잃지** 않고 대부분의 편집 내용을 1초 이내에 볼 수 있습니다.

**How It Works**

- 만약에 React components를 수정한다면 , Fast Refresh는 그 파일의 코드를 업데이트 할 것이고 , 컴포넌트를 리렌더링 합니다. 스타일 , 렌더링 로직 , 이벤트 핸들러 등 파일 안에 모든 것을 수정 할 수 있습니다.
- 만약에 React components가 아닌 것을 수정한다면 , Fast Refresh는 해당 파일과 import된 다른 파일을 다시 실행합니다. 따라서 `Button.js`와 `Modal.js`가 모두 `theme.js`를 가져오면 `theme.js`를 편집하면 두 컴포넌트가 모두 업데이트됩니다.

- 마지막으로 응답 트리 외부의 파일에서 가져온 파일을 편집하면 , Fast Refresh가 다시 전체 다시 로드를 수행합니다. React 컴포넌트를 렌더링하지만 React가 아닌 컴포넌트에서 가져온 값을 내보내는 파일이 있을 수 있습니다. 예를 들어 구성 요소가 상수를 내보내고 non-React 유틸리티 파일이 상수를 가져올 수 있습니다. 이 경우 상수를 별도의 파일로 마이그레이션하고 두 파일로 모두 가져오는 것이 좋습니다. 이렇게 하면 Fast Refresh가 다시 활성화됩니다. 다른 사례들도 대개 비슷한 방식으로 해결될 수 있습니다.

**Error Resilience**

만약에 컴포넌트 내부에서 런타임 오류로 이어지는 실수를 하면 상황에 맞는 오버레이를 만날 것 입니다. 오류를 수정하면 앱을 다시 로드하지 않고 오버레이가 자동으로 해제됩니다. 

렌더링하는 동안 에러가 발생하지 않는다면 컴포넌트 상태는 유지됩니다. 만약에 렌더링하는 동안 에러가 발생한다면 , React는 업데이트된 코드를 다시 시작할 것 입니다. 

만약에 앱에 [Error Boundaries](https://reactjs.org/docs/error-boundaries.html)( production에서 우아한 실패의 좋은 방식입니다. )가 있다면 , 렌더링 에러 이후에 다시 시도 할 것 입니다. Error Boundaries는 root app 상태를 reset하는 것을 방지함을 의미합니다. 그러나 Error Boundaries가 너무 세밀하지 않아야 합니다. 이들은 React에서 생산에 사용되며, 항상 의도적으로 설계되어야 합니다.

**Limitations**

Fast Refresh는 편집중인 컴포넌트에 로컬 React 상태를 안전한 경우에만 보존하려고 합니다. 다음은 파일을 편집할 때마다 로컬 상태가 재설정되는 것을 볼 수 있는 몇 가지 이유입니다.

- 클래스 컴포넌트에서는 로컬 상태가 보존되지 않습니다. ( 오직 함수형 컴포넌트가 가능합니다. )
- 편집 중인 파일에 React 컴포넌트 외에 다른 내보내기가 있을 수 있습니다.
- 때떄로 , 파일은HOC(Wrapped Component)와 같은 상위 구성 요소를 호출한 결과를 내보냅니다. 반환된 구성 요소가 클래스인 경우 해당 상태가 재설정됩니다.
-  `export default () => <div />`와 같은 익명 화살표는 Fast Refresh로 인해 로컬 구성 요소 상태가 유지되지 않습니다. 대규모 코드베이스의 경우 Name-default-component 코드모드를 사용할 수 있습니다.

함수형 컴포넌트로 변함에 따라서 더 많은 경우 상태가 유지될 것입니다. 



**Tips**

- Fast Refresh는 기본적으로 함수형 컴포넌트의 로컬 상태를 보존합니다.
- 때때로 너가 강제로 초기화 하길 원하면 , 컴포넌트는 remount 해야 할 수도 있습니다. 예를 들어, 마운트에서만 발생하는 애니메이션을 조정하는 경우 편리할 수 있습니다. 이렇게하려면 편집중인 파일의 아무 곳이나 `// @refresh` 재설정을 추가 할 수 있습니다. 이 지시문은 파일의 로컬이며 모든 편집에서 해당 파일에 정의된 구성 요소를 다시 마운트하도록 Fast Refresh에 지시합니다. 
- 개발 중에 편집하는 구성 요소에 `console.log` 또는 `debugger;` 넣을 수 있습니다.



**Fast Refresh and Hooks**

Fast Refresh는 가능한 편집하는동안 컴포넌트 상태를 유지하려고 합니다. 특히 , useState , useRef는 Hook의 호출 순서를 바꾸지 않는 한 이전 상태를 보존합니다.

`useEffect` , `useMemo` , `useCallback`은 항상 Fast Refresh 할 것 입니다. dependencies 목록은 Fast Refresh가 일어나는 동안 무시됩니다. 

예를들어 ,  `useMemo(() => x * 2, [x])` 을 `useMemo(() => x * 10, [x])`로 편집할때 x dependency가 변하지 않더라도 재 실행 될 것 입니다. 만약에 리액트가 그렇게 하지 않는다면 , 편집은 화면에 반영되지 않을 것 입니다. 

때떄로 이것은 기대되지 않은 결과를 이끕니다. 예를 들어 , `useEffect`가 빈 depth라도 Fast Refresh 동안은 재 실행 됩니다. 

그러나 때때로 useEffect의 재실행에 탄력적인 코드 작성은 Fast Refresh가 없어도 좋은 방법입니다. 당신이 나중에 그것에 새로운 의존성을 소개하는 것이 더 쉽게 만들 것이며, 우리가 적극적으로 활성화하는 것을 권장하는 [React Strict Mode](https://nextjs.org/docs/api-reference/next.config.js/react-strict-mode)에 의해 시행됩니다.
- ### ESLint

- ### TypeScript

- ### Environment Variables

- ### Supported Browsers and Features

- ### Handling Scritps
---
## Routing

- ### Overview

- ### Introduction

- ### Dynamic Routes

- ### Imperatively

- ### Shallow Routing
---
## API Routes

- ### Introduction

- ### Dynamic API Routes

- ### Request Helpers

- ### Response Helpers

- ### Edge API Routes
---
## Going to Production
---
## Deployment
---
## Authentication
---
## Testing
---
## Accessibility
---
## Guides
- ### Building Forms
---
## Advanced Features

- ### Next.js Compiler

- ### Turbopack

- ### Preview Mode

- ### Dynamic Import

- ### Automatic Static Optimization

- ### Static HTML Export

- ### Absolute Imports and Module Path Aliases

- ### Using MDX

- ### AMP Support

  - #### Introduction

  - #### Adding AMP Components

  - #### AMP in Static HTML export

  - #### TypeScript

- ### Customizing Babel config

- ### Customizing PostCSS Config

- ### Custom Server

- ### Custom App

- ### Custom Document

- ### Custom Error Page

- ### src Directory

- ### CI Build Caching

- ### Multi Zones

- ###  Measuring performance

- ### Middleware

- ### Debugging

- ### Error Handling

- ### Source Maps

- ###  Codemods

- ### Internationalized Routing

- ### Output File Tracing

- ### Security Headers

- ### React 18

  - #### Overview

  - #### Streaming SSR

  - #### React Server Components

  - #### Switchable Runtiem
---
## Upgrade Guide
---
## Migrating to Next.js

- ### Incrementally Adopting Next.js

- ### Migrating from Gatsby

- ### Migrating from Create React App

- ### Migrating from React Router
---
## FAQ
