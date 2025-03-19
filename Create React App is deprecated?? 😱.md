# Create React App is Deprecated 🤯?

`#React` `#Deprecated` `#Create-React-App` `#Why` `#Today-I-Learned`

*If you don’t have time, you can jump to the conclusion:* [⏩ Skip to Conclusion](#4-so-what-exactly-do-you-want-to-say)

**Create React App** used to be an officially supported way to create single-pag React applications. I offered a modern build setup with no configuration. (2022 Toromo, _Getting Started_ https://create-react-app.dev/docs/getting-started/) However, on 14th February 2025, React anoounced that they are now sunsetting the Create React App.

## 1. What is Create React App?

Create React App was first released back in 2016, to ease the developers by resolving all the hustles when building a new React app such as basic featues like JSX, linters and hot reloading. It was a combination of several tools replacing the community boilerplates that often were difficult to update. (2025 Matt and Ricky, _Sunsetting Create React App_ https://react.dev/blog/2025/02/14/sunsetting-create-react-app)

Basically, anyone could start/build a React application and not worry about everything else by just one line of command;
`npx create-react-app@latest my-app`

## 2. Why is it deprecated?

Although CRA made it easy to get started, there were some limitations that made it difficult to build high performant production apps. In principle, they could solve these problems by essentially evolving it into a framework.

### 2.1. What were the limitations of CRA?

While Create React App (CRA) was an easy way to start a new React project, it had several limitations that made it less suitable for modern web development:

**🚀 Performance Issues**

- CRA used Webpack under the hood, which resulted in slow build times, especially for large applications.
- The default configuration lacked server-side rendering (SSR), making it difficult to optimize for SEO and performance.

**⚙️ Lack of Built-in Features**

- CRA did not support Server Components, which are now an important part of the React ecosystem.
- No built-in support for static site generation (SSG) or incremental static regeneration (ISR).
- While Next.js and other frameworks evolved, CRA remained relatively stagnant.

**📦 Large Bundle Sizes**

- CRA included a lot of dependencies by default, making bundle sizes larger than necessary.
- Tree-shaking and code-splitting were not as efficient as other modern tools like Vite or Next.js.

**🔄 Difficult to Customize**

- CRA abstracted the configuration away, which was great for beginners but frustrating for developers who wanted more control.
- Ejecting the CRA setup (npm run eject) was irreversible and made the project difficult to maintain.

### 2.2. Does that mean React was not a framework?

React itself is _NOT a full-fledged framework_ like Next.js or Angular—**it is a UI library for building component-based user interfaces**. However, React can be used within frameworks like Next.js, Remix, or Gatsby, which provide additional features like routing, data fetching, and SSR.

**Why isn’t React a framework?**

- React only focuses on **rendering UI components.**
- It doesn’t provide built-in solutions for **routing, state management, SSR, or API handling**—these require additional libraries.
- Compared to frameworks like **Next.js**, which handle SSR, routing, and data fetching out-of-the-box, React alone is more of a **library** than a framework.

That’s why the React team encourages developers to use **Next.js**, **Remix**, or **Vite** instead of **CRA** for better performance and a richer development experience.

## 3. How do I start a project now?

Since Create React App (CRA) is deprecated, it's important to use modern tools for starting a React project. The right choice depends on what you're building.

### 3.1. What do you need the project for?

Before choosing a tool, ask yourself:

✔ Do you need Server-Side Rendering (SSR) or Static Site Generation (SSG)? → Use a framework like **Next.js**.

✔ Are you building a React Native mobile app? → Use **Expo**.

✔ Do you just need a simple, fast setup for a React app? → Use **Vite**.

### 3.2. Start a project using Framework

Frameworks provide opinionated setups with routing, data fetching, and performance optimizations built-in.

#### 3.2.1. Next.JS

Next.js is a full-stack React framework with SSR, SSG, API routes, and routing support out of the box.

👉 Best for: Web apps, SEO-friendly pages, blogs, and e-commerce.

To create a Next.js app: https://nextjs.org/docs/app/getting-started/installation

```bash
npx create-next-app@latest my-next-app
cd my-next-app
npm run dev
```

#### 3.2.2. React Router's Framework

Remix is a modern framework built around React Router that focuses on fast-loading, data-driven applications with great UX.

👉 Best for: Apps with complex navigation, form handling, and data fetching.

To create a Remix app: https://remix.run/docs/en/main/start/tutorial

```bash
npx create-remix@latest my-remix-app
cd my-remix-app
npm run dev
```

#### 3.2.3. Expo (For React Native Apps)

If you're building a mobile app using React Native, Expo provides an easy way to start without worrying about native configurations.

👉 Best for: Mobile apps (iOS, Android).

To create an Expo app: https://docs.expo.dev/tutorial/create-your-first-app/

```bash
npx create-expo-app my-expo-app
cd my-expo-app
npm start
```

### 3.3. Start a project using Build Tool

If you just need a fast, simple setup for a React project, you can use a build tool instead of a full framework.

#### 3.3.1. Vite (Fastest and Most Popular)

Vite is the best alternative to CRA, offering super-fast builds and a great development experience.

👉 Best for: Any React project that doesn’t require SSR or SSG.

To create a Vite React app: https://vite.dev/guide/

```bash
npm create vite@latest my-vite-app --template react
cd my-vite-app
npm install
npm run dev
```

#### 3.3.2. Parcel

Parcel is another fast bundler like Vite but focuses on zero-config setup.

👉 Best for: Quick prototyping, small projects.

To create a Parcel React app:

```bash
mkdir my-parcel-app && cd my-parcel-app
npm init -y
npm install react react-dom parcel
echo 'import React from "react"; import { createRoot } from "react-dom/client"; const App = () => <h1>Hello Parcel!</h1>; createRoot(document.getElementById("root")).render(<App />);' > index.js
echo '{"presets": ["@babel/preset-react"]}' > .babelrc
npm start
```

#### 3.3.3. RS Build

RSBuild is a Rust-based build tool designed for ultra-fast JavaScript bundling.

👉 Best for: Large-scale applications that need extreme build performance.

To set up RSBuild: https://rsbuild.dev/guide/start/quick-start

```bash
npm create rspack@latest my-rsbuild-app
cd my-rsbuild-app
npm install
npm start
```

## 4. So what exactly do you want to say?

💡 If you're just starting out, go with Vite – it's simple and fast.
💡 If you're building a full web app, Next.js is the best choice.
💡 If you're making a mobile app, use Expo.

## ⚖️ Comparison Table  

| Tool      | Type        | Best For                        | Pros                        |
|----------|------------|--------------------------------|----------------------------|
| **Vite**  | Build Tool | Fast setup, small projects     | 🚀 Super fast, 🔧 Easy to configure |
| **Parcel** | Build Tool | Zero-config bundling          | 🛠 No config needed, ⚡ Fast builds |
| **Next.js** | Framework  | Full web apps, SEO, SSR       | 🌎 SEO-friendly, 🏗 Full-stack support |
| **Remix**  | Framework  | Data-driven, dynamic apps     | ⚡ Fast loading, 🔄 Great routing |
| **Expo**   | Framework  | React Native mobile apps      | 📱 Easy mobile dev, 🚀 Quick setup |


If you're a junior developer like me, without immediate plans to build a complex web service, **Vite is more than enough for personal projects**. You only need to consider a framework (such as Next.js or Remix) when you encounter challenges that a build tool alone cannot solve—such as **SEO optimization, server-side rendering (SSR), or API route integration**. In other words, diving deep into a framework only becomes necessary **when SSR is required or when working on a large-scale application.** Until then, it's more practical to get comfortable with React using Vite. 🚀

✅ **Summary**: Start with Vite, and learn a framework when the need arises! 😃