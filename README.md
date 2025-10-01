# 202130217 양하진
## 08/27 (1주차)       

## 09/03 (2주차)  

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

## 09/10 (3주차)      
- route(라우트)는 "경로"를 의미하고, routing(라우팅)은 "경로를 찾아가는 과정"을 의미합니다.
- routing이란 사용자가 요청한 URL에 따라 해당 URL에 맞는 페이지를 보여주는 것이다. 
- routes는 route의 복수형으로 route를 묶어주는 역할을 하고 기존의 switch의 역할을 하게 됩니다. routes를 사용하지 않고 route를 나열한다면 조건에 맞는 route를 다 보여주게 됩니다. route가 실질적인 역할을 합니다.

## 09/17 (4주차)
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

## 09/24 (5주차)
- searchParams 란?     
-> URL의 쿼리 문자열(Query String)을 읽는 방법입니다.     
-> 여기서 category-shoes, page=2가 search parameters 입니다.     
-> searchParams는 컴포넌트의 props로 전달되며, 내부적으로는 URLSearchParams 처럼 작동합니다.
- 왜 "동적 렌더링"이 되는가?     
- Next.js에서 페이지는 크게 정적(static) 또는 동적(dynamic)으로 렌더링될 수 있습니다.
- searchParams는 요청이 들어와야만 값을 알 수 있기 때문에, Next.js는 이 페이지를 정적으로 미리 생성할 수 없고, 요청이 올 때마다 새로 렌더링해야 합니다.
- 따라서 해당 페이지는 자동으로 동적 렌더링(dynamic rendering)으로 처리됩니다.

## 10/01 (6주차)
#### Client-side transitions(클라이언트 측 전환)      
- 일반적으로 서버 렌더링 페이지로 이동하면 전체 페이지가 로드됩니다.        
-> 이로 인해 state가 삭제되고, 스크롤 위치가 재설정되며, 상호작용이 차단됩니다.
- Next.js는 < Link >컴포넌트를 사용하는 클라이언트 측 전환을 통해 이를 방지합니다.
- 공유 레이아웃과 UI를 유지합니다.
- 현재 페이지를 미리 가져온 (prefetching) 로딩 상태 또는 사용 가능한 경우 새 페이지로 바꿉니다.
- 클라이언트 측 전환은 서버에서 렌더링된 앱을 클라이언트에서 렌더링된 앱처럼 느끼게 하는 요소입니다.
- 또한 프리페칭 및 스트리밍과 함께 사용하면 동적 경로에서도 빠른 전환이 가능합니다.


