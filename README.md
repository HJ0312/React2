# 202130217 양하진

## 11/05
#### Fetching Data
1. 서버 컴포넌트
- 서버 컴포넌트에서 데이터를 fetch 하는 방법은 두가지가 있습니다.        
-> fetch API      
-> ORM 또는 데이터베이스         

[fetch API 사용]
- 데이터를 가져오려면 fetch API를 사용하여 컴포넌트를 비동기식 함수로 변환하고 다음 fetch의 호출을 기다립니다.        
[알아두면 좋은 정보]
- fetch 응답은 기본적으로 캐싱되지 않습니다.
- 그러나 Next.js는 라우팅 페이지를 미리 렌더링하고, 성능 향상을 위해 출력은 캐싱됩니다.
- 동적 렌더링을 사용하려면 { cache : 'no-store' }옵션을 사용합니다. **fetch API 참고**
- 개발 중에는 가시성과 디버깅을 개선하기 위해 fetch 호출을 기록할 수 있습니다. **logging API 참고**

##### 뒤에서 자세히 살펴보겠지만 Next.js 15.1 이후부터 서버 컴포넌트에서 await 없이 fetch를 사용하게 되었습니다.



## 10/29
#### Context provider 실습 코드 설명
1. Context 생성 코드 설명(theme-provider.tsx) -client 컴포넌트       
-> context를 사용하면 **props를 사용하지 않고도** 전역적으로 사용할 theme, 언어 설정, 로그인 정보 등을 하위 컴포넌트에 전달할 수 있습니다.      
-> createContext()는 React 컴포넌트 트리 전체에 값을 공유할 수 있도록 하는 역할을 합니다.      
-> createContext(..)로 Context 객체를 생성하여, Theme state를 공유합니다.      
-> 초기값(default value)은 provider가 없을 때 사용할 fallback value 입니다.     
--> React에서는 createContext()를 호출할 때 기본값이 반드시 있어야 합니다.      
--> 보통은 실제 동작하지 않는 빈 함수 (()=>{})를 기본으로 넣어둡니다.     
--> 실제 동작은 ThemeProvider 컴포넌트에서 설정하게 됩니다.        
##### TypeScript의 유니온 타입(Union Type)이란?
- '|'(파이프)로 여러 타입을 연결해서 "이 값은 각각의 타입 중 하나가 될 수 있다"는 것을 지정합니다.
- 코드에서 문자열 리터럴 유니온 타입의 경우, state 값으로 'light' 또는 'dark'만 설정할 수 있어 코드 자동완성과 타입 안정성이 향상됩니다.



## 10/22 
#### server 및 client component interleaving
- 클라이언트 컴포넌트가 껍데기 역할을 하고, 서버 컴포넌트가 그 안의 내용(children)으로 들어오는 구조(패턴)를 설명하는 것입니다.
- Next.js에서는 기본적으로      
-> Server Component -> 서버에서 렌더링됨.(데이터 패칭 가능)        
-> Client Component -> 브라우저에서 렌더링됨.(상호작용 가능)
- 즉, **서버 컴포넌트 안에는 클라이언트 컴포넌트를 넣을 수 있지만**, 그 **반대는 직접적으로는 불가능**합니다.
- 그래서 "interleaving"이라는 아이디어가 나오게 되는 것입니다.       
-> **클라이언트 컴포넌트 안에 생성한 children 슬롯에 서버 컴포넌트를 '끼워 넣는' 방식**으로 둘을 섞어서 사용하자는 아이디어 입니다.

## 10/01 
#### Client-side transitions(클라이언트 측 전환)      
- 일반적으로 서버 렌더링 페이지로 이동하면 전체 페이지가 로드됩니다.        
-> 이로 인해 state가 삭제되고, 스크롤 위치가 재설정되며, 상호작용이 차단됩니다.
- Next.js는 < Link >컴포넌트를 사용하는 클라이언트 측 전환을 통해 이를 방지합니다.
- 공유 레이아웃과 UI를 유지합니다.
- 현재 페이지를 미리 가져온 (prefetching) 로딩 상태 또는 사용 가능한 경우 새 페이지로 바꿉니다.
- 클라이언트 측 전환은 서버에서 렌더링된 앱을 클라이언트에서 렌더링된 앱처럼 느끼게 하는 요소입니다.
- 또한 프리페칭 및 스트리밍과 함께 사용하면 동적 경로에서도 빠른 전환이 가능합니다.

## 09/24 
- searchParams 란?     
-> URL의 쿼리 문자열(Query String)을 읽는 방법입니다.     
-> 여기서 category-shoes, page=2가 search parameters 입니다.     
-> searchParams는 컴포넌트의 props로 전달되며, 내부적으로는 URLSearchParams 처럼 작동합니다.
- 왜 "동적 렌더링"이 되는가?     
- Next.js에서 페이지는 크게 정적(static) 또는 동적(dynamic)으로 렌더링될 수 있습니다.
- searchParams는 요청이 들어와야만 값을 알 수 있기 때문에, Next.js는 이 페이지를 정적으로 미리 생성할 수 없고, 요청이 올 때마다 새로 렌더링해야 합니다.
- 따라서 해당 페이지는 자동으로 동적 렌더링(dynamic rendering)으로 처리됩니다.

## 09/17 
- git checkout vs git switch 차이     
-> branch 명령은이동 할 수 없음       
-> switch 와 checkout은 branch를 만들기만 할 수는 없고, 만들고 바로 이동합니다.        
-> 참고로 branch 명령은 branch의 생성, 삭제, 확인 등을 할 때 사용합니다.

- Creating a layout (레이아웃 만들기)        
-> layout은 여러 페이지에서 공유되는 UI 입니다.      
-> layout은 네비게이션에서 state 및 상호작용을 유지하며, 다시 렌더링 되지는 않습니다.      
-> layout 파일에서 React 컴포넌트의 default export를 사용하여 layout을 정의할 수 있습니다.      
-> layout 컴포넌트는 page 또는 다른 layout이 될 수 있는 children prop을 허용해야 합니다.       
-> 루트 레이아웃은 필수이며, html 및 body 태그를 포함해야 합니다.      
-> 중첩 라우트는 다중 URL 세그먼트로 구성된 라우트입니다.    

- slug의 이해      
-> 데이터 소스가 크다면 .find는 0(n)이므로 DB 쿼리로 바꿔야합니다.       
: 0(n)은 알고리즘의 시간 복잡도가 입력 데이터의 크기 n에 비례하여 시간이나 메모리 사용량이 선형적으로 증가하는 것을 의미합니다.

## 09/10      
- route(라우트)는 "경로"를 의미하고, routing(라우팅)은 "경로를 찾아가는 과정"을 의미합니다.
- routing이란 사용자가 요청한 URL에 따라 해당 URL에 맞는 페이지를 보여주는 것이다. 
- routes는 route의 복수형으로 route를 묶어주는 역할을 하고 기존의 switch의 역할을 하게 됩니다. routes를 사용하지 않고 route를 나열한다면 조건에 맞는 route를 다 보여주게 됩니다. route가 실질적인 역할을 합니다.

## 09/03 

### Installation     
#### Strict    
- Next.js의 기본 ESLint 구성과 더욱 엄격한 **Core Web Vitals 규칙 세트**를 포함합니다. **EsLint를 처음 설정하는 개발자에게 권장**되는 구성입니다.
- Base : Next.js의 기본 ESLint 구성을 포함합니다.
- Cancel : 구성을 건너뜁니다. 사용자가 지정 ESLint 구성을 설정하려면 이 옵션을 선택하세요.
- Strict 또는 Base 중 하나가 선택되면, Next.js는 자동으로 eslint와 eslint-config-next를 애플리케이션의 의존성으로 설치합니다.
- 또한 선택한 설정을 포함하는 .eslintrc.json 파일을 프로젝트 루트 디렉토리에 생성합니다.     
### import 및 모듈의 절대 경로 별칭 설정
- Next.js에는 tsconfig.json 및 jsconfig.json 파일의 "paths" 및 "baseUrl" 옵션에 대한 지원을 내장하고 있습니다.
- 이 옵션을 사용하면 프로젝트 디렉터리를 절대 경로로 별칭하여 모듈을 더 쉽고 깔끔하게 가져올 수 있습니다.
- 별칭으로 import를 구성하려면 tsconfig.json 또는 jsconfig.json 파일의 baseUrl에 구성 옵션을 추가하세요.    
### Core Web Vitals
- LCP(Largest Contentful Paint) : 뷰포트 내에서 **가장 큰 페이지 요소(큰 텍스트 블록, 이미지 또는 비디오)**를 표시하는데 걸리는 시간.
- FID(First Input Delay) : **사용자가 웹페이지와 상호작용을 시도하는 첫 번째 순간부터 웹페이지가 응답하는 시간**
- CLS(Cumulative Layout Shift) : 방문자에게 **콘텐츠가 얼마나 불안정한 지 측정한 값.** 페이지에서 갑자기 발생하는 레이아웃의 변경이 얼마나 일어나는지를 측정. 즉, 레이아웃 이동(layout shift) 빈도를 측정합니다. 

## 08/27 