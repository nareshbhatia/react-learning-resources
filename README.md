# React Learning Resources

A curated list of resources to learn React and related web technologies as fast
as possible. The goal is to help you create production quality React apps even
if you are starting from scratch. Just bring plenty of motivation and
perseverance :smile:

If you are curious, this is my preferred React stack:

**Core**

- [TypeScript](https://www.typescriptlang.org/docs/) for type safety
- [React](https://reactjs.org/) - for building component-based UIs
- [React Context](https://reactjs.org/docs/context.html) &
  [hooks](https://reactjs.org/docs/hooks-intro.html) for state management

**Foundational libraries**

- [React Router](https://reactrouter.com/) for navigation
- [React Query](https://react-query.tanstack.com/) for fetching data using REST
- [Apollo GraphQL](https://www.apollographql.com/docs/) for fetching data using
  GraphQL
- [React Hook Form](https://react-hook-form.com/get-started) for form handling
- [ag-Grid](https://www.ag-grid.com) - a feature-packed JavaScript grid
- [Highcharts](https://www.highcharts.com) for interactive charts

**Essential tools**

- [Storybook](https://storybook.js.org/) to develop UI components in isolation
- [React Testing Library](https://testing-library.com/) for unit testing
- [Cypress](https://www.cypress.io/) for end-to-end testing
- [Mock Service Worker](https://mswjs.io/) to mock HTTP requests
- [Prettier](https://prettier.io/) to format code consistently

I have created the
[React Accelerate template](https://github.com/PublicisSapient/cra-template-accelerate)
to kick-start React apps using the above stack.

P.S. If you find this content useful, please show your appreciation by starring
this repository.

## Contents

- [The React Crash Course](#the-react-crash-course)
- [Developer Machine Setup](#developer-machine-setup)
- [CSS](#css)
- [TypeScript](#typescript)
- [React](#react)
- [React Router](#react-router)
- [React Hook Form](#react-hook-form)
- [GraphQL](#graphql)
- [Highcharts](#highcharts)
- [ag-Grid](#ag-grid)
- [Testing Best Practices](#testing-best-practices)
- [Jest](#jest)
- [React Testing Library](#react-testing-library)
- [Storybook](#storybook)
- [Mock Service Worker](#mock-service-worker)
- [Cypress](#cypress)
- [Git and Code Reviews](#git-and-code-reviews)
- [Visual Design](#visual-design)
- [Domain-Driven Design](#domain-driven-design)

## The React Crash Course

This crash course is designed to teach you React and related web technologies as
fast as possible. Feel free to skip any topic that you already know. For video
tutorials, I highly recommend to type along with the instructor to have it sink
in faster.

- [HTML Crash Course For Absolute Beginners](https://www.youtube.com/watch?v=UB1O30fR-EE)
  (1:00) by Brad Traversy
- [CSS Crash Course For Absolute Beginners](https://www.youtube.com/watch?v=yfoY53QXEnI)
  (1:25) by Brad Traversy
- [Flexbox CSS In 20 Minutes](https://www.youtube.com/watch?v=JJSoEo8JSnc)
  (20:00) by Brad Traversy
- [JavaScript Crash Course For Beginners](https://www.youtube.com/watch?v=hdI2bqOjy3c)
  (1:40) by Brad Traversy
- [TypeScript Crash Course](https://www.youtube.com/watch?v=BCg4U1FzODs) (0:53)
  by Brad Traversy
- [React Crash Course](https://www.youtube.com/watch?v=w7ejDZ8SWv8) (1:49) by
  Brad Traversy
- [Jest Crash Course](https://www.youtube.com/watch?v=7r4xVDI2vho) (0:57) by
  Brad Traversy (does not cover mocking, see below for mocking)
- [Jest Crash Course](https://www.youtube.com/watch?v=ajiAl5UNzBU) (start at
  0:50 for mocking) by Laith Harb

Once done, you can test your understanding by taking
[this practice exercise](https://github.com/nareshbhatia/react-takeout-exercise).

## Developer Machine Setup

- [MacOS setup](./docs/dev-machine-setup-macos.md)
- [Windows setup](./docs/dev-machine-setup-windows.md)

## CSS

- [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Pixels vs. Relative Units in CSS](https://www.24a11y.com/2019/pixels-vs-relative-units-in-css-why-its-still-a-big-deal/)
- [When to Use Em vs. Rem](https://webdesign.tutsplus.com/tutorials/comprehensive-guide-when-to-use-em-vs-rem--cms-23984)
- [EM vs REM vs PX – Why you shouldn't “just use pixels”](https://engageinteractive.co.uk/blog/em-vs-rem-vs-px)
- [Learn CSS Variables in 5 minutes](https://www.freecodecamp.org/news/learn-css-variables-in-5-minutes-80cf63b4025d/)
- [Difference between CSS variables and preprocessor variables](https://css-tricks.com/difference-between-types-of-css-variables/)
- [CSS Variables - Lea Verou](https://www.youtube.com/watch?v=2an6-WVPuJU)
- [MindBEMding – getting your head ’round BEM syntax](https://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)
- [Get BEM - Naming](http://getbem.com/naming/)

## TypeScript

- [Official TypeScript documentation](https://www.typescriptlang.org/docs/)
- [TypeScript Deep Dive](https://basarat.gitbook.io/typescript/getting-started)
- [Understanding TypeScript - Udemy](https://www.udemy.com/course/understanding-typescript/)

## React

- [React documentation](https://reactjs.org/docs/getting-started.html)
- [Recommended Folder Structure](./docs/folder-structure.md)
- [React Coding Conventions](./docs/react-coding-conventions.md)
- [Epic React by Kent C. Dodds](https://epicreact.dev/) - detailed hands-on
  training in React
- [React - The Complete Guide - Udemy](https://www.udemy.com/course/react-the-complete-guide-incl-redux/)
- [React and Typescript - Udemy](https://www.udemy.com/course/react-and-typescript-build-a-portfolio-project/)
- [Dan Abramov's Blog](https://overreacted.io/)
  - [A Complete Guide to useEffect](https://overreacted.io/a-complete-guide-to-useeffect/)
  - [Writing Resilient Components](https://overreacted.io/writing-resilient-components/)
- [Kent C. Dodd's Blog](https://kentcdodds.com/)
  - [How to use React Context effectively](https://kentcdodds.com/blog/how-to-use-react-context-effectively)
  - [State Colocation - Where to Put State](https://kentcdodds.com/blog/state-colocation-will-make-your-react-app-faster)
  - [useState lazy initialization and function updates](https://kentcdodds.com/blog/use-state-lazy-initialization-and-function-updates)
- [React+TypeScript Cheatsheets](https://github.com/typescript-cheatsheets/react)

## React Router

- [Version 6 docs](https://github.com/remix-run/react-router/tree/dev/docs) -
  Note that v6 is in beta. The only up-to-date docs are here in the dev branch.

## React Hook Form

- [React Hook Form documentation](https://react-hook-form.com/get-started)
- [React Hook Form example with Yup validation](https://react-hook-form.com/get-started/#SchemaValidation)
- [Complex form example](https://github.com/nareshbhatia/form-examples)

## GraphQL

- [GraphQL concepts I wish someone explained to me a year ago](https://medium.com/naresh-bhatia/graphql-concepts-i-wish-someone-explained-to-me-a-year-ago-514d5b3c0eab)
- [Introduction to GraphQL](https://graphql.org/learn/)
- [Apollo GraphQL Tutorial](https://odyssey.apollographql.com/)
- [Apollo Documentation](https://www.apollographql.com/docs/)
- [GraphQL Schema Design](https://blog.apollographql.com/graphql-schema-design-building-evolvable-schemas-1501f3c59ed5)
- [GraphQL Code Generator](https://www.graphql-code-generator.com/)
- [GraphQL Scalars](https://www.graphql-scalars.dev/docs/introduction/)
- [Apollo Link Scalars](https://github.com/eturino/apollo-link-scalars)
- [AWS AppSync](https://aws.amazon.com/appsync/)

## Highcharts

- [Documentation](https://www.highcharts.com/docs/index)
- [API](https://api.highcharts.com/highcharts/)
- [Examples](https://www.highcharts.com/demo)
- [Pie chart with drilldown](https://www.highcharts.com/demo/pie-drilldown)

## ag-Grid

ag-Grid supports multiple frameworks. We use the React version of ag-Grid along
with some concepts (like `columnDefs`) from the JavaScript version.

- [JavaScript Grid Documentation](https://www.ag-grid.com/javascript-grid/)
- [React Grid Documentation](https://www.ag-grid.com/react-grid/)

## Testing Best Practices

- [React Testing Techniques](https://github.com/nareshbhatia/react-testing-techniques)
- [How to know what to test](https://kentcdodds.com/blog/how-to-know-what-to-test)
- [Write tests. Not too many. Mostly integration.](https://kentcdodds.com/blog/write-tests)
- [Write fewer, longer tests](https://kentcdodds.com/blog/write-fewer-longer-tests)
- [Making your UI tests resilient to change](https://kentcdodds.com/blog/making-your-ui-tests-resilient-to-change)
- [Testing Implementation Details](https://kentcdodds.com/blog/testing-implementation-details)

## Jest

- [Documentation](https://jestjs.io/docs/getting-started)

## React Testing Library

- [Introduction](https://testing-library.com/docs/)
- [Guiding Principles](https://testing-library.com/docs/guiding-principles)
- [Example](https://testing-library.com/docs/react-testing-library/example-intro)
- [Cheatsheet](https://testing-library.com/docs/react-testing-library/cheatsheet)
- [Common mistakes with React Testing Library](https://kentcdodds.com/blog/common-mistakes-with-react-testing-library)

## Storybook

- [Introduction to Storybook](https://storybook.js.org/docs/react/get-started/introduction)

## Mock Service Worker

- [Documentation](https://mswjs.io/docs/)

## Cypress

- [Documentation](https://docs.cypress.io/guides/overview/why-cypress)

### Git and Code Reviews

- [How to Make Your Code Reviewer Fall in Love with You](https://mtlynch.io/code-review-love/) -
  Must read! Shows how to raise good PRs.
- [git - the simple guide](https://rogerdudler.github.io/git-guide/)
- [Trunk Based Development](https://trunkbaseddevelopment.com/)
- [Trunk-based Development vs. Git Flow](https://www.toptal.com/software/trunk-based-development-git-flow)
- [OneFlow – a Git branching model and workflow](https://www.endoflineblog.com/oneflow-a-git-branching-model-and-workflow) -
  OneFlow is just another name for Trunk-based Development.

## Visual Design

- [Refactoring UI](https://www.refactoringui.com/) (written by the authors of
  Tailwind CSS)
- [Foundations of Design Systems - Emma Wedekind](https://www.youtube.com/watch?v=pXb2jA43A6k)

## Domain-Driven Design

- [Naresh Bhatia's Blog](https://archfirst.org/domain-driven-design/)
