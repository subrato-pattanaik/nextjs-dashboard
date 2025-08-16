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
