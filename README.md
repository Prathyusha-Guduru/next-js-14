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

## Data Fetching 

Each page in Next.js can directly access server-side resources as they are inherently server-side rendered components. This integration simplifies fetching data from backend APIs without the need to pass props for initial data loading.

#### Simultaneous Data Fetching
When using nested layouts, Next.js optimizes data fetching by performing requests simultaneously across the layouts rather than sequentially. This parallel data fetching significantly improves page loading times, enhancing the 'time to interact' for users.

#### Automatic Deduping
Next.js automatically deduplicates identical data requests made by different components during the same rendering cycle. This optimization prevents unnecessary API calls, reducing network load and speeding up rendering.


## Streaming in Next.js

#### Process Flow
Next.js enhances the performance of web applications by streamlining the way data and UI are managed:

1. **Fetch Data**: Server-side data fetching to gather all necessary data before rendering.
2. **Render React Components**: Converts React components into HTML on the server.
3. **Send HTML to Browser**: Transmits the static HTML to the browser for quick first paint.
4. **Render Non-Interactive Pages**: Displays content to users while JavaScript is still loading.
5. **Execute JavaScript (React Hydration)**: Activates interactive features of the page by attaching event handlers and additional JavaScript-driven functionality.

#### Progressive Loading
Next.js components are loaded progressively, each with its own lifecycle for data fetching, rendering, and streaming:

- Components are loaded simultaneously and independently, enhancing the user experience by progressively revealing the UI.
- To manage loading states, you can add a `loading.tsx` file alongside each `page.tsx` file. Next.js will automatically display this component while the page is loading.

Under the hood, Next.js leverages React Suspense to handle asynchronous operations within components. Suspense wraps components performing asynchronous tasks, showing a fallback UI until the operation completes. This mechanism is crucial for maintaining a responsive and smooth user experience during data loading phases.


