# Coding Conventions and Patterns

There is plenty of content out there on coding conventions and best practices. I
am going to highlight a few items that I have found useful when working by
myself or with large teams.

## TypeScript Best Practices

- Don't use `any` - it defeats the purpose of using TypeScript. In case you are
  using a 3rd party library that doesn't provide typedefs, it may be ok to use
  `any` for unknown complex types, but avoid it as much as possible.

- Let the TypeScript compiler enforce strong type checking for you. Here's a
  [sample tsconfig file](https://github.com/tsconfig/bases/blob/main/bases/node16-strictest.combined.json)
  with the strictest type checking. Start with this. You may want to relax some
  rules if your existing codebase generates hundreds (or thousands!) of errors,
  but you should be striving for something close to this.

## Import order

The import order guidelines below are intended to keep your imports organized
and easier to scan.

- Start with an import from 'react', if needed.
- Follow by other external imports, sorted by module name. For example, an
  import from `@apollo/client` goes before the import from `react-router-dom`.
- Follow by internal imports, starting with parent directories and ending with
  the current directory. For example, an import from `../../components` goes
  before the import from `./AccountContext`.
- Sort named imports by name. For example,
  `import { Loading, SideBar } from '../../components';`.

**Example**

```tsx
import React, { useEffect } from 'react';
import { useQuery } from '@apollo/client';
import { useNavigate } from 'react-router-dom';
import { Loading, SideBar } from '../../components';
import { useAccountContext } from './AccountContext';
```

## React Components

- Use PascalCase for both file names and component names.
- Structure your component as a traditional function (vs. a const function
  expression). This is much easier to read and has the advantage of getting
  hoisted.
- Always export your components by name (named exports) (vs. default exports).
  Named exports provide tighter control over the name and also better
  refactoring support by most IDEs. Note that some libraries force you to use
  default exports (e.g. Storybook), in which case you don't have a choice.

**Example: Header.tsx**

```tsx
export function Header() {
  <h1>Catalog</h1>;
}
```

- To pass in props, use an interface (vs. a type). It is easier to extend. If
  you'd like a heuristic, use interface until you need to use features from
  type.
- The name of the interface should be `[ComponentName]Props`. Don't take any
  shortcuts - it's easier to just follow this rule and keep your codebase
  consistent.

**Example with props**

```tsx
interface HeaderProps {
  children?: React.ReactNode;
}

export function Header({ children }: HeaderProps) {
  <h1>{children}</h1>;
}
```

Note: Stop using `React.FC` and `React.FunctionComponent`. React 18 removed the
implicit children property in these types. Use the above construct instead.

**Should I define a return type?**

It is customary to NOT specify the return type from a component and simply rely
on type inference. Technically it could be `React.ReactElement` or even wider
such as `JSX.Element`, but better to let TypeScript infer it than mistakenly
typing it too wide.

**References**

- [How to write a React Component in TypeScript](https://kentcdodds.com/blog/how-to-write-a-react-component-in-typescript)
  by Kent C. Dodds
- [Differences Between Type Aliases and Interfaces](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces) -
  TypeScript docs
- [Removal Of Implicit Children](https://solverfox.dev/writing/no-implicit-children/)
  by Sebastian Silbermann

## Event props and event handlers

Name event props as `onXyz` and event handlers as `handleXyz`. Intent is that
handler names are verbs - they _handle_ an event.

**Example**

In this example, the `AccountDetails` component uses the `AccountSelector`
component which expects to receive a handler. Note that the prop is named
`onAccountSelected` and the handler is named `handleAccountSelected`.

```tsx
// ----- AccountSelector -----
interface AccountSelectorProps {
  onAccountSelected: (accountId: string) => void;
}

function AccountSelector({ onAccountSelected }: AccountSelectorProps) {
  ...
}

// ----- AccountDetails -----
function AccountDetails() {
  const handleAccountSelected = (accountId: string) => {
    // hanle account selection
  };

  return <AccountSelector onAccountSelected={handleAccountSelected} />;
}
```

## Structuring content inside function components

Sequence the code in function components as follows:

1. Float all your hooks to the top.
2. Next write your handlers and other functions.
3. Then write any executable logic.
4. Finally, return your markup.

Reason for the first bullet above can be found in React docs
[here](https://reactjs.org/docs/hooks-rules.html). According to these docs,
don't call Hooks inside loops, conditions, or nested functions. Instead, always
use Hooks at the top level of your React function, before any early returns. In
other words, float all Hooks to the top of your component. This will avoid
breaking the rule of Hooks.

**Example**

In the example below, note that 4 hooks are floated to the top.

```tsx
function SignUpPage() {
  // ---------- hooks ----------
  const { authState, setAuthState } = useAuthContext();
  const navigate = useNavigate();
  const [signUp, { error }] = useMutation(SignUpDocument);

  // redirect if user is already logged in
  useEffect(() => {
    if (authState.user) {
      navigate('/accounts');
    }
  }, [authState.user, navigate]);

  // ---------- handlers and other functions ----------
  const handleSubmit = async (formEntity: FormEntity) => {};

  // ---------- any executable code ----------
  // e.g. if (loading) { ... }

  // ---------- return markup ----------
  return <SignUpForm signUpError={error?.message} onSubmit={handleSubmit} />;
}
```

## State Management

- When state is needed only by one component, keep it in that component and use
  `useState` for it.
- If you find a component keeping state, but only its child needs it (passed
  using props), then move the state down to the child ("colocate" with the
  child). This is more performant because when state changes only the child is
  rerendered.
- If a component is housing some state which is also needed by the parent and/or
  a sibling, then "lift state" up to the parent.
- If you find that the state in a component is being sent deep down into the
  component tree using props (prop drilling), then move the state into a context
  provider and have the nested components consume it using `useContext`.
- Use React Context for state management

The diagram below nicely summarizes these rules (courtesy Kent C. Dodds):

![State Management Decision Tree](../assets/state-management-decision-tree.jpg)

**References**

- [State Colocation - Where to Put State](https://kentcdodds.com/blog/state-colocation-will-make-your-react-app-faster) -
  explains when to lift state up (so that multiple components can access it) vs.
  push it down, i.e. colocate it (because only one component needs it)
- [Application State Management with React](https://kentcdodds.com/blog/application-state-management-with-react) -
  makes a case for using React Context and Hooks to manage state vs. external
  libraries like Redux
- [Lifting State Up](https://reactjs.org/docs/lifting-state-up.html#lessons-learned) -
  Summary of state sharing best practices

## React Context Pattern

When using React Context, it is convenient to package the provider and the hook
in a single file. This pattern is suggested by Kent C. Dodds in his blog
[How to use React Context effectively](https://kentcdodds.com/blog/how-to-use-react-context-effectively).

**Example**

```tsx
import React, { useContext, useState } from 'react';

// ---------- ViewStateContext ----------
type ViewState = { isEditing: boolean };
type ViewStateSetter = (viewState: ViewState) => void;

/** ViewStateContext contains ViewState and ViewStateSetter */
const ViewStateContext = React.createContext<
  { viewState: ViewState; setViewState: ViewStateSetter } | undefined
>(undefined);

// ---------- ViewStateContextProvider ----------
interface ViewStateContextProviderProps {
  children?: React.ReactNode;
}

function ViewStateContextProvider({ children }: ViewStateContextProviderProps) {
  console.log('ViewStateContextProvider.render');
  const [viewState, setViewState] = useState<ViewState>({
    isEditing: false,
  });

  const value = { viewState, setViewState };
  return (
    <ViewStateContext.Provider value={value}>
      {children}
    </ViewStateContext.Provider>
  );
}

// ---------- useViewStateContext ----------
function useViewStateContext() {
  const viewStateContext = useContext(ViewStateContext);
  if (viewStateContext === undefined) {
    throw new Error(
      'useViewStateContext must be used within a ViewStateContextProvider'
    );
  }
  return viewStateContext;
}

export { ViewStateContextProvider, useViewStateContext };
```
