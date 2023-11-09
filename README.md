# Next.js Dashboard - TUTORIAL

This is a repo containing the [official Next.js tutorial](https://nextjs.org/learn)

## Index

- [Next.js Dashboard - TUTORIAL](#nextjs-dashboard---tutorial)
  - [Index](#index)
  - [1. Getting Started](#1-getting-started)
  - [2. CSS Styling](#2-css-styling)
  - [3. Optimizing Fonts and Images](#3-optimizing-fonts-and-images)
  - [4. Creating Fonts and Images](#4-creating-fonts-and-images)
  - [5. Navigating Between Pages](#5-navigating-between-pages)
  - [6. Setting Up Your Database](#6-setting-up-your-database)
  - [7. Fetching Data](#7-fetching-data)
  - [8. Static and Dynamic Rendering](#8-static-and-dynamic-rendering)
  - [9. Streaming](#9-streaming)
  - [10. Partial Prerendering](#10-partial-prerendering)
  - [11. Adding Search and Pagination](#11-adding-search-and-pagination)
  - [12. Mutating Data](#12-mutating-data)
  - [13. Handling Errors](#13-handling-errors)
  - [14. Improving Accessibility](#14-improving-accessibility)
  - [15. Adding Authentication](#15-adding-authentication)
  - [16. Adding Metadata](#16-adding-metadata)

## 1. Getting Started

To create a Next.js project:

```bash
npx create-next-app
```

To install the project's packages:

```bash
npm i
```

To run the project:

```bash
npm run dev
```

Folder Structure:

- `/app/` - Routes, Components, Logic
  - `/lib/` - Functions
  - `/ui/` - UI Components
- `/public/` - assets
- `/scripts` - scripts (e.g. populate database)

## 2. CSS Styling

- How to add a global CSS file to your application.
- How to add a global CSS file to your application.
- How to conditionally add class names with the `clsx` utility package.

The `global.css` file affects the style of the whole app.
Tailwind is usually used in Next.js but CSS Modules can also be used.
`clsx` allows for conditional styles.

## 3. Optimizing Fonts and Images

- How to add custom fonts with `next/font`.
- How to add images with `next/image`.
- How fonts and images are optimized in Next.js.

By using Next's native fonts the client doesn't have to fetch them, leading to
better performance and UX. Next's native images are automatically responsive and
prevent layout shift/lazy load.

## 4. Creating Fonts and Images

- Create the dashboard routes using file-system routing.
- Understand the role of folders and files when creating new route segments.
- Create a nested layout that can be shared between multiple dashboard pages.
- Understand what colocation, partial rendering, and the root layout are.

Folder structure and routes:

- 📁 app
  - 📁 dashboard
    - 📁 invoices -> app/dashboard/invoices/
  - 📄 page.tsx -> app/

`layout.tsx` creates a component that is common to all child pages, usually a navbar.
`child` inside `layout.tsx` is the main page without the navbar.

Next.js supports partial rendering, meaning that some components, like the layout, aren't
re-rendered when the child is updated.

## 5. Navigating Between Pages

- How to use the `next/link` component.
- How to show an active link with the `usePathname()` hook.
- How navigation works in Next.js.

Whereas usually the browser is reloaded whenever you change pages, with `<Link>`
component uses client-side navigation.
`usePathname()` returns the current pwd.
In Next.js, the browser only fetches the code for the page your on rather than the
whole app, which is faster and more secure.

## 6. Setting Up Your Database

- Push your project to GitHub.
- Set up a Vercel account and link your GitHub repo for instant previews and deployments.
- Create and link your project to a Postgres database.
- Seed the database with initial data.

Vercel supports easy database integration. You can easily browse your DB and
query it from Vercel. To set it up, simply follow the instructions.

## 7. Fetching Data

- Learn about some approaches to fetching data: APIs, ORMs, SQL, etc.
- How Server Components help us access our back-end resources more securely.
- What network waterfalls are.
- How to implement parallel data fetching using a JavaScript Pattern.

Server Components allow you to query the DB securely (from the server) and
directly (without an API). It also supports promises (`async/await`).

Vercel/postgres is protected against SQL injections.

A request waterfall happens when you fetch a piece of data at a time. To solve that,
we can parallel data fetch with `Promise.all()`

## 8. Static and Dynamic Rendering

- What static rendering is and how it can improve your application's performance.
- What dynamic rendering is and when to use it.
- Different approaches to make your dashboard dynamic.
- The limitation of fetching data at request time.

Static Rendering is when the data being displayed is static. It's faster and less
resource intenseful, helps with SEO(search engine optimization).

Dynamic Rendering is ideal for when data is constantly changing. It's good for
real-time data, user specific content, better request times.

`noStore()` opts iyt if static rendering.

In an app using Dynamic Rendering, it's as fast as the slowest fetch.

## 9. Streaming

- What streaming is and when you might use it.
- How to implement streaming with `loading.tsx` and Suspense.
- What loading skeletons are.
- What route groups are, and when you might use them.
- Where to place Suspense boundaries in your application.

Streaming is fetching data and displaying it in chunks (components). `loading.ts`
is a file that is displayed while data is not yet fetched. A loading skeleton is a preview
of the page while it's loading. Folders surronded by `()` don't interfere with the path.

`<Suspense>` allows for streaming for a single component.

## 10. Partial Prerendering

- What Partial Prerendering is.
- How Partial Prerendering works.

Some parts of the same page are static and the others are dynamic, using `<Suspense>`

Data fetching and optimisation:

1. DB and App on the same region
2. React Server Components
3. SQL fetches only needed data
4. Parallelize data fetching with js
5. Streaming
6. Data fetching by component

## 11. Adding Search and Pagination

- Learn how to use the Next.js APIs: `searchParams`, `usePathname`, and `useRouter`.
- Implement search and pagination using URL search params.

Search with URL params allows for:

1. Bookmarks and shareable URL
2. Server-side rendering
3. Analytics and Tracking

The 3 hooks in question allow you to dynamically change the URL with user input.
Use `useSearchParams()`(hook) on the client-side, `searchParams`(prop) on the server-side

Debouncing is useful to not overwelm the DB: Trigger -> Wait -> Execution

The same hooks are used for pagination, URL needs to be updated with user input.

## 12. Mutating Data

- What React Server Actions are and how to use them to mutate data.
- How to work with forms and Server Components.
- Best practices for working with the native `formData` object, including type validation.
- How to revalidate the client cache using the `revalidatePath` API.
- How to create dynamic route segments with specific IDs.
- How to use the React’s `useFormStatus` hook for optimistic updates.

## 13. Handling Errors

- How to use the special `error.tsx` file to catch errors in your route segments, and show a fallback UI to the user.
- How to use the notFound function and not-found file to handle 404 errors (for resources that don’t exist).

## 14. Improving Accessibility

- How to use `eslint-plugin-jsx-a11y` with Next.js to implement accessibility best practices.
- How to implement server-side form validation.
- How to use the React `useFormState` hook to handle form errors, and display them to the user.

## 15. Adding Authentication

- What is authentication.
- How to add authentication to your app using NextAuth.js.
- How to use Middleware to redirect users and protect your routes.
- How to use React's `useFormStatus` and `useFormState` to handle pending states and form errors.

## 16. Adding Metadata

- What metadata is.
- Types of metadata.
- How to add an Open Graph image using metadata.
- How to add a favicon using metadata.
