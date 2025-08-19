## Next.js notes

Nextjs is a react framework for building full stack applications with server-side rendering and static site generation.

Image and fonts optimization is built-in to provide faster load times and improved user experience.

It provides file-based routing where folders and files correspond to routes in the application. `page.tsx` files are used to define the content for each route.

Layouts can be defined to provide a consistent structure across different pages, and components can be shared easily between them. `layout.tsx` files are used to define the layout for a specific route or group of routes that share the same layout.

One benefit of using layouts in Next.js is that on navigation, only the page components update while the layout won't re-render. This is called partial rendering which preserves client states in the layout when transitioning between pages.

Link component can be used to link different pages in the application. It allows us to do client side navigation using javascript.

## Automatic code-splitting and prefetching

To improve the navigation experience, Next.js automatically code splits your application by route segments.
This is different from a traditional React SPA, where the browser loads all your application code on the initial page load.

Splitting code by routes means that pages become isolated. If a certain page throws an error, the rest of the application will still work. This is also less code for the browser to parse, which makes your application faster.

Furthermore, in production, whenever <Link> components appear in the browser's viewport, Next.js automatically prefetches the code for the linked route in the background. By the time the user clicks the link, the code for the destination page will already be loaded in the background, and this is what makes the page transition near-instant!

## Ways to fetch data

1.  Api layer (Creating api endpoints)

    APIs are an intermediary layer between your application code and database. You can create a dedicated API layer using Next.js API routes or external APIs to fetch data. This allows you to separate your data fetching logic from your UI components and provides a clear structure for managing API calls.

    There are a few cases where you might use an API:

    - If you're using third-party services that provide an API.
    - If you're fetching data from the client, you want to have an API layer that runs on the server to avoid exposing your database secrets to the client.

```
Client (Browser)
↓ fetch("/api/users")
API Route (/api/users)
↓ query
Database
```

2.  Skipping api layer and talking directly to database

```
Client (Browser)
  ↓ request page
Next.js Server Function (getServerSideProps / Server Action / Loader) or Server components
  ↓ query
Database
```

**Summary**
API Layer → Indirect: frontend calls API → API hits DB.

Database Queries → Direct: query DB in server-side functions.

Server Components → A specific place where we can do those direct queries.

Using SQL → The actual query language (we can use raw SQL instead of ORM).

## Waterfall request

Requests are made in a sequential manner, where each request depends on the previous one. This can lead to performance bottlenecks if not managed properly.

## Static rendering

With static rendering, data fetching and rendering happens on the server at build time (when you deploy) or when revalidating data.

Whenever a user visits your application, the cached result is served.

Benefits:

- Faster Websites - Prerendered content can be cached and globally distributed when deployed to platforms like Vercel. This ensures that users around the world can access your website's content more quickly and reliably.
- Reduced Server Load - Because the content is cached, your server does not have to dynamically generate content for each user request. This can reduce compute costs.
- SEO - Prerendered content is easier for search engine crawlers to index, as the content is already available when the page loads. This can lead to improved search engine rankings.

Static rendering is **useful for UI with no data or data that is shared across users, such as a static blog post or a product page.** It might not be a good fit for a dashboard that has personalized data which is regularly updated.

The opposite of static rendering is dynamic rendering.

## Dynamic rendering

Dynamic rendering in Next.js means generating the page content on the server at request time, so each user gets up-to-date or personalized data. This is done using server-side rendering (SSR), server components, or API routes, instead of serving pre-built static HTML.

`loading.tsx` is a special Next.js file built on top of React Suspense. It allows you to create fallback UI to show as a replacement while page content loads.
