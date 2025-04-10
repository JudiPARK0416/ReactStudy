# What are Babel, Webpack, ESLint, Jest, PostCSS and Tailwind?

`#React` `#Babel` `#Webpack` `#ESLint` `#Jest` `#PostCSS` `#Tailwind` `#Today-I-Learned`  
**Judy Park, 1 April 2025**

With CRA (Create React App) now deprecated, many developers are turning to Vite to start their React projects. But while CRA came with many tools and configurations set up for you, Vite requires you to be more hands-on when it comes to setup.

So, can you still use the tools that CRA automatically configured when you're starting a project with Vite? And if not, are there any alternatives or plugins built into Vite? If not, how can you integrate them yourself?

Today, we’ll go over what Babel, Webpack, ESLint, Jest, PostCSS, and Tailwind actually do — and how to use or replace them in a Vite-based project.

---

## 1. Babel
**Babel is a JavaScript compiler that allows you to use next-gen JavaScript syntax while ensuring compatibility with older browsers.** It also transforms JSX into regular JavaScript.
바벨은 자바스크립트 트랜스컴파일러이다. 최신 브라우저를 사용하지 않거나 자바스크립트가 지원되지 않는 브라우저를 사용하는 사용자를 위해 예전 문법으로 변환해주는 것이 바벨이다. 그래서 사용자의 브라우저 버전을 고려하지 않고 마음껏 최신 버전으로 개발하거나, 타입스크립트로 타입이 강력하게, 그래서 더 안전한 개발을 하도록 도와주는 것이 바벨임.

### 1.1 Can I still use Babel with Vite?
Vite doesn’t use Babel by default. Instead, it uses faster alternatives like [esbuild](https://esbuild.github.io/) and [SWC](https://swc.rs/). That said, if you really need Babel, you can still use it — `@vitejs/plugin-react` internally uses Babel for JSX transforms, and you can manually add your own Babel config if needed.

**In short: Babel is not default in Vite, but it's still usable if necessary.**

---

## 2. Webpack
**Webpack is a JavaScript bundler that takes your modules and bundles them into optimized files for the browser.**
우리 코드를 잘 번들링 해서 사용자에게 배포할 수 있도록 도와준다. 포장하기. 그래서 프로젝트를 만드는 와중에 많은 파일을 만들게 되더라도 결국 가장 처음 사용자에게 가야하는 html, img 파일은 뭐가 있는지, 어떤 것들을 그룹지어 사용자에게 전송해야 하는지 번들링을 해주는 것이 웹팩이다. 번들링 외에도 쓰이지 않는 코드들을 다 제거하고 압축하고, 코멘트를 제거하고 사용자에게 보여주고 css 를 축약해서 파일 사이즈를 줄이도록 도와줌

### What about Webpack in Vite?
Vite does **not** use Webpack. It uses **native ESM (ECMAScript Modules)** during development and [Rollup](https://rollupjs.org/) for production builds.

If you need something similar to Webpack's capabilities, you can explore Vite plugins or Rollup equivalents.

---

## 3. ESLint
**ESLint is a linter for JavaScript that helps you catch syntax errors and enforce code style rules.**
코드를 올바르게 사용하고 있는지.

### How to use ESLint with Vite
CRA included ESLint out of the box, but with Vite, you need to set it up yourself:

```bash
npm install eslint --save-dev
npx eslint --init
```

To integrate ESLint with the Vite dev server:

```bash
npm install vite-plugin-eslint --save-dev
```

Then add it to your Vite config.

---

## 4. Jest
**Jest is a popular testing framework for JavaScript, especially in the React ecosystem.**

### Does Vite support Jest?
Jest is not built into Vite. Instead, Vite recommends using [Vitest](https://vitest.dev/), which is faster and designed to work seamlessly with Vite.

```bash
npm install -D vitest
```

Vitest has an API very similar to Jest, making migration pretty easy.

---

## 5. PostCSS
**PostCSS is a tool for transforming CSS with JavaScript plugins. It’s commonly used for things like autoprefixing.**

CRA includes PostCSS by default. In Vite, you need to configure it manually:

```bash
npm install postcss autoprefixer --save-dev
```

Then create a config file:

```js
// postcss.config.js
module.exports = {
  plugins: {
    autoprefixer: {},
  },
};
```

---

## 6. Tailwind CSS
**Tailwind CSS is a utility-first CSS framework that lets you build modern, responsive UIs quickly.**

### How to set up Tailwind with Vite
Tailwind works great with Vite. Here's how to set it up:

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

Then configure the content paths:

```js
// tailwind.config.js
module.exports = {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

---

## ✨ Summary
| Tool         | Included in CRA | Included in Vite?     | How to Use or Replace in Vite         |
|--------------|------------------|------------------------|----------------------------------------|
| Babel        | Yes              | No (optional)          | Use @vitejs/plugin-react or add Babel manually |
| Webpack      | Yes              | No                     | Vite uses Rollup instead               |
| ESLint       | Yes              | No                     | Install manually + vite-plugin-eslint  |
| Jest         | Yes              | No                     | Use Vitest                             |
| PostCSS      | Yes              | No                     | Install manually + postcss.config.js   |
| Tailwind CSS | No (manual setup)| No                     | Install manually + config              |

While CRA offered a magical zero-config setup, using Vite means you gain more insight and control over your tooling. It’s fast, modern, and gives you the flexibility to tailor your stack.

Welcome to the era of React + Vite — where you're in control 🚀
