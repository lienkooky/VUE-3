# frontend 24.01.30

## Repository 초기화

```
/* .git 디렉터리 삭제 / 상태확인 */
$ rm -rf .git
$ git status (fatal: not a git repository)

/* git 초기화 후 새로운 git 설정 */
$ cd <생성할 디렉터리>
$ git init
$ git add .
$ git branch -M main
$ git commit -m "commit message"

/* github 저장소 연결후 강제 push */
$ git remote add origin <연결할 url>
$ git push --force --set-upstream origin main
```

## vscode setting.json 설정

```
"prettier.trailingComma": "all",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit",
    "source.formatDocument": "explicit"
  },
  // Set the default
  "editor.formatOnSave": false,
  // Enable per-language
  "[javascript]": {
    "editor.formatOnSave": true
},
"[vue]": {
    "editor.formatOnSave": true
},
```

## .eslintrc.js

```
module.exports = {
  root: true,
  env: {
    browser: true,
    node: true,
  },
  extends: ["plugin:vue/vue3-essential", "@vue/airbnb", "eslint:recommended", "prettier"],
  parserOptions: {
    parser: "@babel/eslint-parser",
  },
  rules: {
    "no-console": process.env.NODE_ENV === "production" ? "warn" : "off",
    "no-debugger": process.env.NODE_ENV === "production" ? "warn" : "off",
  },
};

```

## package.json

```
 "dependencies": {
    "core-js": "^3.8.3",
    "vue": "^3.2.13",
    "vue-router": "^4.0.3",
    "vuex": "^4.0.0"
  },
  "devDependencies": {
    "@babel/core": "^7.12.16",
    "@babel/eslint-parser": "^7.12.16",
    "@vue/cli-plugin-babel": "~5.0.0",
    "@vue/cli-plugin-eslint": "~5.0.0",
    "@vue/cli-plugin-router": "~5.0.0",
    "@vue/cli-plugin-vuex": "~5.0.0",
    "@vue/cli-service": "~5.0.0",
    "@vue/eslint-config-airbnb": "^6.0.0",
    "eslint": "^7.32.0",
    "eslint-plugin-import": "^2.25.3",
    "eslint-config-prettier": "^8.3.0",
    "eslint-plugin-prettier": "^4.0.0",
    "eslint-plugin-vue": "^8.0.3",
    "eslint-plugin-vuejs-accessibility": "^1.1.0",
    "prettier": "^2.4.1"
  }
```

## vue.config.js 설정

```
const { defineConfig } = require("@vue/cli-service");

module.exports = defineConfig({
  transpileDependencies: true,

  // build 할 때 타켓 디렉토리 (백앤드쪽)
  outputDir: "../backend/src/main/resources/static", // Build Directory

  // npm run serve 개발 진행시 포트가 다르기 때문에 프록시 설정해줘야 함.
  // target : 백엔드 port가 들어감
  // changeOrigin -> true로 해야 cors 문제 해결할 수 있음

  // devServer: {
  //   proxy: {
  //     "/": {
  //       target: "http://localhost", // Spring Boot Server
  //       changeOrigin: true,
  //     },
  //   },
  // },
});

```