# Next.js 14 Overview

## Routing
- Next.js uses a file-based routing system.
- The `Link` component is used for client-side routing, which prevents full page reloads.
- Use the `useRouter` hook for programmatic navigation between components.
- For dynamic segments, name files or folders with brackets, e.g., `[:id]`.
- Special naming conventions include `(stuff)` for route grouping and `@pro`, `@basic` for parallel routes, read more [here](https://github.com/Prathyusha-Guduru/next-js-14/blob/main/special-routing-cases.md) 
- Keeping the routing structure simple is advisable for clarity and usability.

## Route Handlers
- Route handlers manage requests and responses.
- Use `routes.ts` to define server-side logic, which runs in the Node.js environment.

## Layouts
- The root layout contains global components like navigation bars and footers and uses a `children` prop for different pages.
- Nested layouts can be used for specific application sections, such as a dashboard with its own navigation components.
- Layouts handle their own data fetching
- Layouts are efficient because they help us avoid re-rendering of commonly used components
- Layouts do not re-mount with route changes. To enable re-mounting, rename `layout.tsx` to `template.tsx`.
