# Parallel Routes and Route Grouping in Next.js

## Parallel Routes Example
Imagine you have a website with both a basic and a professional version of a service. You can structure your directories to reflect these options using parallel routes:

- `/pages/products/index.tsx` - Main product listing.
- `/pages/products/@basic/[productId].tsx` - Handles specific product details for basic users.
- `/pages/products/@pro/[productId].tsx` - Handles specific product details for professional users.

In this setup, the `@basic` and `@pro` tags create parallel routes under the same base URL `/products`, but each serves different content based on the user's subscription level.

## Route Grouping Example
Route grouping allows you to organize related pages or components together in a directory without affecting the URL path. For instance:

- `/pages/events/(archive)/index.tsx` - Lists all archived events.
- `/pages/events/(archive)/[year].tsx` - Shows events from a specific year within the archive.

Although the files are inside the `(archive)` folder, the URLs accessed by users would be `/events` and `/events/[year]`, not showing the `(archive)` part. This grouping is purely for organizational purposes within the codebase, making it easier to manage and understand the structure, especially in larger projects.
