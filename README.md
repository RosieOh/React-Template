# [React] 초기세팅
리액트 프로젝트를 기본적으로 구성하는 것들을 주로 작성

## 프로젝트 생성
### 1. CRA

```
npx create-reat-app [프로젝트명]
npx create-react-app [프로젝트명] --template typescript
```


### 2. Vite
```
npm create vite@latest [프로젝트 명] 
npm create vite@latest [프로젝트 명] --template react-ts
```

CRA와 Vite 방식으로 프로젝트를 생성할 수 있는데, CRA로 프로젝트를 만들면서 빌드가 매우 느리다는 이슈 발생

그래서 Vite를 사용해보니 빌드가 CRA보다 상대적으로 빠름

#### Eslint 파일

```
module.exports = {
  root: true,
  env: { browser: true, es2020: true }, // 브라우저 환경 및 ES2020 환경 설정

  extends: [
    "eslint:recommended", // ESLint의 기본 권장 규칙 사용
    "plugin:@typescript-eslint/recommended", // TypeScript 관련 권장 규칙 사용
    "plugin:react-hooks/recommended", // React Hooks 규칙 사용
  ],

  ignorePatterns: ["dist", ".eslintrc.cjs"], // ESLint 무시할 파일 또는 디렉토리 설정

  parser: "@typescript-eslint/parser", // TypeScript 구문 분석기 사용

  plugins: ["react-refresh"], // React Refresh 플러그인 사용

  rules: {
    "react-refresh/only-export-components": [
      "warn",
      { allowConstantExport: true },
    ], // React 컴포넌트는 오직 컴포넌트만 내보내야 합니다.

    indent: ["error", 2], // 들여쓰기 스타일 설정 (2칸 들여쓰기)

    "no-unused-vars": "off", // 사용하지 않는 변수 경고 끄기

    "@typescript-eslint/no-unused-vars": [
      "error",
      { vars: "all", args: "after-used", ignoreRestSiblings: false },
    ], // TypeScript에서 사용하지 않는 변수를 검출합니다.

    "@typescript-eslint/explicit-function-return-type": "warn",
    // 함수의 반환 타입이 추론 가능할 때도 명시적으로 타입을 선언하도록 경고합니다.

    "no-empty": "warn", // 빈 블록문에 대한 경고 설정

    semi: ["error", "always"], // 세미콜론(;) 사용 강제 설정
  },
};
```

#### Prettier
```
npm install -D prettier
```

```
// .eslintrc
{
  "extends": ["plugin:prettier/recommended"]
}
prettier 설치 시, .eslintrc가 있으면 extends에 추가
```

```
// .prettierrc
{
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": false,
  "quoteProps": "as-needed",
  "jsxSingleQuote": false,
  "trailingComma": "none",
  "bracketSpacing": true,
  "jsxBracketSameLine": false,
  "arrowParens": "always",
  "endOfLine": "auto"
}
```

### 라이브러리
#### CSS

####1. styled-components
```
npm install styled-components
```

#### 2. emotion
```
npm install @emotion/react
```
```

{  // tsconfig.json
  "compilerOptions": {
    ...
    "types": ["@emotion/react/types/css-prop"] // 추가
  }
}
```
styled-components를 사용했더니, 컴포넌트 태그가 스타일 컴포넌트인지 혹은 UI가 있는 컴포넌트인지 눈으로 쉽게 확인을 할 수 없었던 경험이 있다.

그러다보니, 개인적인 프로젝트 스타일 라이브러리는 emotion을 사용을 한다.

### Router
```
npm install react-router-dom
```

### State 관리

#### Redux
```
npm install redux react-redux
npm install @reduxjs/toolkit react-redux
npm install -D redux-devtools //  크롬브라우저 확장프로그램 
```

### 연동을 위한 설치
### Recoil

```
npm install recoil
```

### 폴더 구조
```
Project/
├── src/
│ ├── components/ # React 컴포넌트들
│ ├── pages/ # 페이지 컴포넌트들 (라우팅)
│ ├── styles/ # CSS 스타일 및 스타일 유틸리티
│ ├── assets/ # 이미지, 폰트 등
│ └── App.js / App.tsx
├── public/
│ ├── index.html # HTML 템플릿 파일
│ └── ...
├── package.json # 프로젝트 설정 및 의존성
├── .eslintrc.json # ESLint 설정 파일
├── .prettierrc # Prettier 설정 파일
└── ...
```
