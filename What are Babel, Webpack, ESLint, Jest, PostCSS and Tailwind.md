# What are Babel, Webpack, ESLint, Jest, PostCSS and Tailwind?

`#React` `#Babel` `#Webpack` `#ESLint` `#Jest` `#PostCSS` `#Tailwind` `#Today-I-Learned`  
**Judy Park, 1 April 2025**

With CRA (Create React App) now deprecated, many developers are turning to Vite to start their React projects. But while CRA came with many tools and configurations set up for you, Vite requires you to be more hands-on when it comes to setup.

So, can you still use the tools that CRA automatically configured when you're starting a project with Vite? And if not, are there any alternatives or plugins built into Vite? If not, how can you integrate them yourself?

Today, we’ll go over what Babel, Webpack, ESLint, Jest, PostCSS, and Tailwind actually do — and how to use or replace them in a Vite-based project.

---

## 1. Babel
**Babel is a JavaScript compiler that allows you to use next-gen JavaScript syntax while ensuring compatibility with older browsers.** It also transforms JSX into regular JavaScript.

### 1.1 Can I still use Babel with Vite?
Vite doesn’t use Babel by default. Instead, it uses faster alternatives like [esbuild](https://esbuild.github.io/) and [SWC](https://swc.rs/). That said, if you really need Babel, you can still use it — `@vitejs/plugin-react` internally uses Babel for JSX transforms, and you can manually add your own Babel config if needed.

**In short: Babel is not default in Vite, but it's still usable if necessary.**

---

## 2. Webpack
**Webpack is a JavaScript bundler that takes your modules and bundles them into optimized files for the browser.**

### What about Webpack in Vite?
Vite does **not** use Webpack. It uses **native ESM (ECMAScript Modules)** during development and [Rollup](https://rollupjs.org/) for production builds.

If you need something similar to Webpack's capabilities, you can explore Vite plugins or Rollup equivalents.

---

## 3. ESLint
**ESLint is a linter for JavaScript that helps you catch syntax errors and enforce code style rules.**

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
