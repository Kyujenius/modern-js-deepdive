## 개발 툴의 근본적인 목적

단순 브라우저 기반 웹앱은 브라우저만으로도 만들 수 있지만, 규모가 커지면 React, Angular, Lodash, Babel, Webpack, ESLint 같은 도구들이 필요하다 → 그래서 Node.js와 npm이 필요하다.

### 1. Node.js와 도구들의 관계
- Babel, Webpack, ESLint 같은 도구들은 자바스크립트로 작성된 프로그램이다.
- 그런데 브라우저는 소스코드를 빌드하거나 검사하는 개발 환경을 제공하지 않는다. 단순히 랜더링만 하면 되니까!
- 따라서 이 도구들은 Node.js 런타임에서 실행되도록 만들어져 있다.
- Babel: 최신 JS/TS/JSX → 브라우저가 이해할 수 있는 JS로 변환
- Webpack/Vite: 모듈 번들링, 코드 스플리팅
- ESLint: 코드 품질 검사
- 즉, Node.js는 “빌드 도구/개발 도구를 실행할 수 있는 환경”을 제공하는 역할을 해준다.

### 2. “Node.js가 영향을 끼친다”의 의미
- Node.js가 이 도구들의 런타임 실행 환경이기 때문에 사실상 전반적인 프런트엔드 개발 프로세스에 영향을 끼친다. 예를 들어,

```bash
npm install webpack babel eslint
```

 → npm(Node.js 생태계)로 설치

```bash
npx webpack build
```

→ Node.js에서 webpack을 이용해 build 명령 실행

- 빌드 결과물이 브라우저에서 실행되는 JS 코드가 됨
- 즉, 도구들이 Node.js 없이는 동작할 수 없으니 Node.js가 직,간접적으로 프런트엔드 전체 개발 흐름에 관여한다고 봐야한다.

### 3. 정리

- Node.js는 브라우저 코드를 실행하는 런타임이 아님 (React 앱 자체는 브라우저에서 돌아감).

- Node.js는 **개발 도구(Babel, Webpack, ESLint, Vite, Jest …)**를 돌릴 수 있는 환경.

- 따라서 “Node.js가 이 도구들에 전반적으로 영향을 끼친다” = Node.js가 없으면 이 도구들을 실행할 수 없고, 현대적 프런트엔드 개발 워크플로 전체가 성립하지 않는다는 의미로 이해하면 된다.

### 4. 요약

- Node.js = 개발 도구 실행 환경, Babel/Webpack/ESLint = Node.js 위에서 실행되는 도구, 그래서 Node.js가 프런트엔드 개발 생태계 전반에 깊게 관여한다고 할 수 있다.
