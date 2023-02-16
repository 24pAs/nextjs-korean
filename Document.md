<img src="https://camo.githubusercontent.com/f21f1fa29dfe5e1d0772b0efe2f43eca2f6dc14f2fede8d9cbef4a3a8210c91d/68747470733a2f2f6173736574732e76657263656c2e636f6d2f696d6167652f75706c6f61642f76313636323133303535392f6e6578746a732f49636f6e5f6c696768745f6261636b67726f756e642e706e67" />



## Next.js
---
### Documentation
- [Next.js](#nextjs)
  - [Documentation](#documentation)
- [Getting Started](#getting-started)
- [Basic Features](#basic-features)
  - [When should I use getStaticPaths?](#when-should-i-use-getstaticpaths)
  - [When does getStaticPaths run](#when-does-getstaticpaths-run)
  - [How does getStaticProps run with regards to getStaticPaths](#how-does-getstaticprops-run-with-regards-to-getstaticpaths)
  - [Where can I use getStaticPaths](#where-can-i-use-getstaticpaths)
  - [Runs on every request in development](#runs-on-every-request-in-development)
  - [Generating paths on-demand](#generating-paths-on-demand)
  - [On-demand Revalidation](#on-demand-revalidation)
  - [Using On-demand Revalidation](#using-on-demand-revalidation)
  - [Testing on-Demand ISR during development](#testing-on-demand-isr-during-development)
  - [Error handling and revalidation](#error-handling-and-revalidation)
  - [Self - hosting ISR](#self---hosting-isr)
  - [Related](#related)
- [Client-side data fetching](#client-side-data-fetching)
  - [Client-side data fetching with useEffect](#client-side-data-fetching-with-useeffect)
  - [Client-side data fetching with SWR](#client-side-data-fetching-with-swr)
- [Routing](#routing)
- [API Routes](#api-routes)
- [Going to Production](#going-to-production)
- [Deployment](#deployment)
- [Authentication](#authentication)
- [Testing](#testing)
- [Accessibility](#accessibility)
- [Guides](#guides)
- [Advanced Features](#advanced-features)
- [Upgrade Guide](#upgrade-guide)
- [Migrating to Next.js](#migrating-to-nextjs)
- [FAQ](#faq)

---
## Getting Started

---
## Basic Features

- ### Pages

- ### Data Fetching

  - #### Overview

  - #### getServerSideProps

  - #### getStaticProps

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

 ### When should I use getStaticPaths? 

Dynamic routes를 이용해서 정적으로 pre-rendering된 페이지를 getStaticPaths를 사용해서 만들 수 있습니다. 

- 데이터는 헤드리스 CMS에서 가져옵니다.
- 데이터는 데이터베이스에서 가져옵니다. 
- 데이터는 파일 시스템에서 가져옵니다. 
- 데이터는 공개적으로 캐시될 수 있습니다. 
- 페이지는 사전 렌더링(SEO)용 이어야 하며 매우 빨라야 합니다. `getStaticProps` 는 HTML과 JSON file을 생성하고 둘 다 CDN에 캐시될 수 있습니다. 



### When does getStaticPaths run 

`getStaticPaths`는 프로덕션 환경에서만 동작할 것이고 runtime에서는 동작하지 않습니다. [도구](https://next-code-elimination.vercel.app/)를 사용하여 `getStaticPaths`안쪽에 쓰여진 코드를 validate하고 클라이언트 측 번들에서 제거되었는지 확인할 수 있습니다.

### How does getStaticProps run with regards to getStaticPaths

- `getStaticProps` 는 `next build` 하는 동안 작동하고 , 모든 paths는 빌드 시간동안 반환된다.
- `getStaticProps` 는 `fallback : true` 일때 background에서 작동합니다. 
- `getStaticProps ` 는 `fallback : blocking` 일때 최초 render전에 불려집니다. 



### Where can I use getStaticPaths 

- `getStaticPaths` 는 `getStaticProps`와 함께 사용해야합니다. 
- `getServerSideProps` 에서는 `getStaticPaths` 를 사용할 수 없습니다. 
- getStaticProps도 사용하는 [Dynamic Route](https://nextjs.org/docs/routing/dynamic-routes) getStaticPaths를 내보낼 수 있습니다.
- Page 파일이 아닌곳에서 `getStaticPaths` 를 export 할 수 없습니다. ( ex , components 폴더 )
- getStaticPaths를 페이지 구성 요소의 속성이 아닌 독립 실행형 함수로 내보내야 합니다.



### Runs on every request in development

개발 모드( `next dev` )에서는 , `getStaticPaths` 는 모든 요청마다 불릴 것 입니다.



### [Generating paths on-demand](https://nextjs.org/docs/basic-features/data-fetching/get-static-paths#generating-paths-on-demand)

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

- ### Font Optimization

- ### Static File Serving

- ### Fash Refresh

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
