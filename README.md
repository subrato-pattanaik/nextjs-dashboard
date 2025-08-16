## Next.js notes

Nextjs is a react framework for building full stack applications with server-side rendering and static site generation.

Image and fonts optimization is built-in to provide faster load times and improved user experience.

It provides file-based routing where folders and files correspond to routes in the application. `page.tsx` files are used to define the content for each route.

Layouts can be defined to provide a consistent structure across different pages, and components can be shared easily between them. `layout.tsx` files are used to define the layout for a specific route or group of routes that share the same layout.

One benefit of using layouts in Next.js is that on navigation, only the page components update while the layout won't re-render. This is called partial rendering which preserves client-side React state in the layout when transitioning between pages.
