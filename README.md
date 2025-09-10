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
