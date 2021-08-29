# Recommended Folder Structure

I recommend the following folder structure for your React app:

```
/src
  /components
  /contexts
  /mocks
  /models
  /pages
  /services
  /styles
  /test
  /utils
```

### pages

Let's start with the `pages` folder because it is important for understanding
the overall concepts. This folder contains the top-level pages offered by the
app. Pages are generally associated with high-level business features. A
"feature" is defined as a distinct business function supported by the app. For
example, a newspaper site might support features like Headlines, Politics,
Business, and Sports.

From an implementation perspective, it is important to keep each feature
independent of the others. This implies that any models (data structures),
components, contexts and services needed by the feature should be contained
within the associated page folder. For example, the diagram below shows some
files that may be contained in the `HeadlinesPage` folder:

```
/src
  /pages
    /HeadlinesPage
      headlines page components
      headlines page contexts
      headlines page models
      ...
```

Any artifact that is used by multiple features should be kept in the appropriate
global folder under `src`. For example,

```
/src
  /components
    /Header
      Header.tsx
      Header.css
  /contexts
    UserContext.tsx
  /models
    User.ts
  /utils
    Constants.ts
    StringUtils.ts
```

### components

Contains React components used by multiple features.

### contexts

Contains React contexts used by multiple features.

### mocks

Contains service mocks for [Mock Service Worker](https://mswjs.io/).

### models

Contains models (data structures) used by multiple features.

### services

Contains service functions (api calls, hooks etc.) used by multiple features.

### styles

Contains global styles for styling the app. If you are not using global or
custom CSS for styling, this folder can be deleted (e.g. when using CSS-in-JS or
utility-based frameworks like tailwind.css).

### test

Contains utility classes for unit testing. The actual tests are kept in the same
folder as the component under test.

### utils

Contains basic utility classes used in the entire app.

## Tips

(Based on
[Angular Style Guide](https://angular.io/guide/styleguide#application-structure-and-ngmodules))
structure your app such that you can

1. Locate code quickly
2. Identify the code at a glance
3. Keep the flattest structure you can
4. Try to be DRY.

Emphasizing point #3 above, keep the folder structure as flat as possible. No
one wants to search for a file through seven levels of folders! Consider
creating sub-folders when a folder reaches seven or more files.
