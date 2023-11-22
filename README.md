# LearningNextJs

## Description

This is a repo tracking my personal progress of learning the Next.js and React web frameworks. It mostly includes basic examples found within these tutorials:

* React Foundations
  * https://nextjs.org/learn/react-foundations
* Next.js Foundations
  * https://nextjs.org/learn-pages-router/foundations/about-nextjs
* Create a Next.js App
  * https://nextjs.org/learn-pages-router/basics/create-nextjs-app

## Notes

DOM methods
- getElementById
  - Select HTML element by it’s `id` attribute
- createElement
  - Creates an HTML element, by tag name (e.g. “h1”)
- createTextNode
  - Creates text between some tags (e.g. between `<h1>` and `</h1>`
- appendChild
  - Adds a child element to a parent element (e.g. puts a `<h1 />` between `<div>` and `</div>`

Important libraries
- react
  - the core React library.
- react-dom
  - provides DOM-specific methods that enable you to use React with the DOM.
- babel
  - Transform JSX into JavaScript
  - Babel can find JSX when you use JSX in a script tag, like this: `<script type="text/jsx">`
- gray-matter
  - Parse “YAML Front Matter” (blog posts example) 
- remark, remark-html
  - Render markdown content
  - remark may require using `await`
- date-fns
  - Formatting date

Other cool libraries for CSS stuff
- CSS stuff = https://nextjs.org/learn-pages-router/basics/assets-metadata-css/styling-tips
- clsx
  - Write CSS class names that vary: `className={clsx({[styles.success]: type === 'success', [styles.error]: type === 'error', })}`
- Tailwind
  - `npm install -D tailwindcss autoprefixer postcss`

Terms
- JSX
  - A JavaScript language for React that lets you write HTML
    - e.g. `ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app);`
- object destructuring
  - Instead of naming props as the only argument in a component, you can name the item passed in to props that you wish to access
    - function Header(props) —> function Header({ title })

React code
- `ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app);`
  - Adds the JSX in the first argument to the app - just like how `appendChild` works
- React.useState();
  - Use this hook to maintain state

React Concepts
- Components
  - A Javascript/JSX component that returns UI elements
    - e.g. `function Header() { return (<h1>Develop. Preview. Ship. 🚀</h1>) }`
  - Naming
    - React Components should be capitalized
    - They can have any name, but must `export default` the main component of that page
  - Don’t call it like a regular function: `<Header />` over `Header()`
- Props
  - Enables passing data: like the href or src attributes in HTML tags, but for Components
  - Declared by setting function parameters in Component signature declarations
    - e.g. function Header(props)
- Hooks/State
  - Enables maintaining state…
    - React.useState();
  - the logic for updating the state should be kept within the component where state was initially created

JSX Concepts
- Use variable names in curly braces { }
  - Javascript land is within these curlies

Next.js
- Use NPM to manage react libraries
  - npm install react react-dom next
- It automatically creates the HTML and body tags for you
- Next.js has built-in support for code splitting. Each file inside your pages/ directory will be automatically code split into its own JavaScript bundle during the build step.
- Files and folders under the `/pages` directory can be linked to by their relative path

Next.js Components
- Use `Link from 'next/link'` over `a` tag
  - <Link> allows you to do client-side navigation and accepts props
  - a href does a full refresh, and should be used for external page navigation (e.g. my website to apple.com)
  - in a production build of Next.js, whenever Link components appear in the browser’s viewport, Next.js automatically prefetches the code for the linked page in the background 
- Use Image from next/image over img
  - Features
    - Ensuring your image is responsive on different screen sizes
    - Optimizing your images with a third-party tool or library
    - Only loading images when they enter the viewport
  - Images loaded when they enter the viewport
- Head over head
- Script over script

Static assets
- Images, robots.txt, favicon,ico, etc should be placed in the /public directory. Files in /public should have different names than files in /pages
- A file called me.png in /public can be accessed anywhere in the app at src="/me.png

Pre-rendering and Data Fetching
- Fetch external data at build time with `export async function getStaticProps()`
  - getStaticProps can only be exported from a page
- Use `getServerSideProps` to fetch data at request time (server-side rendering)
- `useSWR` for client side rendering (dashboards, non-SEO, etc.)

Dynamic Routes
- `getStaticPaths`
- ￼
- There are options for catch-all routes
  - “pages/posts/[...id].js matches /posts/a, but also /posts/a/b, /posts/a/b/c and so on.”
- You can create a statically generated custom 404 page, with pages/404.js

API Routes
- `pages/api` can include a handler function (e.g. “hello.js”)
  - http://localhost:3000/api/hello
  - req is an instance of http.IncomingMessage, plus some pre-built middlewares.
  - res is an instance of http.ServerResponse, plus some helper functions.
- Do not fetch an API route from getStaticProps or getStaticPaths
- API Route code is not part of the client bundle
- API Routes can be dynamic
  - https://nextjs.org/docs/pages/building-your-application/routing/api-routes

Search Engine Optimization 
Crawling and Indexing
- Use a 308 (preferred over 301) to redirect if a page has been moved
  - https://nextjs.org/learn-pages-router/seo/crawling-and-indexing/status-codes
- Use robots.txt to request some route to be accessed or not accessed
- Sitemaps are recommended
  - Sitemaps can be statically created and updated manually, or
  - Can be dynamically generated (pages/sitemap.xml.js), using getServerSideProps to help generate the xml page
- Robots meta tag can indicate whether you want a specific page to be indexed or links on that page to be followed
  - <meta name="robots" content="noindex,nofollow" />
  - These tags can be inserted in the <Head> component, imported from ‘next/head’

### TODO:
- Continue learning about SEO here:
  - https://nextjs.org/learn-pages-router/seo/rendering-and-ranking/rendering-strategies
