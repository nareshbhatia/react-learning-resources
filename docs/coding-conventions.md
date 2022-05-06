# Coding Conventions

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

To pass in props, use an interface (vs. a type). It is easier to extend. If
you'd like a heuristic, use interface until you need to use features from type.

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

**References**

- [How to write a React Component in TypeScript](https://kentcdodds.com/blog/how-to-write-a-react-component-in-typescript)
  by Kent C. Dodds
- [Differences Between Type Aliases and Interfaces](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces) -
  TypeScript docs
- [Removal Of Implicit Children](https://solverfox.dev/writing/no-implicit-children/)
  by Sebastian Silbermann

## Import order

- Sort imports by module name. It's ok to place the `react` import always at the
  top.
- Sort named imports by name.

**Example**

```tsx
import React, { useEffect } from 'react';
import { useQuery } from '@apollo/client';
import { useNavigate } from 'react-router-dom';
import { Loading, SideBar } from '../../components';
import { useAccountContext } from './AccountContext';
```

## Naming of event props and event handlers

Name event props as `onXyz` and event handlers as `handleXyz`.

**Example**

```tsx
const AccountDetails = () => {
  const handleAccountSelected = (accountId: string) => {
    // hanle account selection
  };

  return <AccountSelector onAccountSelected={handleAccountSelected} />;
};
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
const SignUpPage = () => {
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
};
```
