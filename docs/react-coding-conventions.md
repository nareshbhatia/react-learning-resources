# React Coding Conventions

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

## Float all Hooks to the top of your function component

As discussed in [React docs](https://reactjs.org/docs/hooks-rules.html), don't
call Hooks inside loops, conditions, or nested functions. Instead, always use
Hooks at the top level of your React function, before any early returns. In
other words, float all Hooks to the top of your component. This will avoid
breaking the rule of Hooks.

**Example**

The example below shows 4 hooks floated to the top of the component.

```tsx
const SignUpPage = () => {
  const { authState, setAuthState } = useAuthContext();
  const navigate = useNavigate();
  const [signUp, { error }] = useMutation(SignUpDocument);

  // redirect if user is already logged in
  useEffect(() => {
    if (authState.user) {
      navigate('/accounts');
    }
  }, [authState.user, navigate]);

  const handleSubmit = async (formEntity: FormEntity) => {};

  return <SignUpForm signUpError={error?.message} onSubmit={handleSubmit} />;
};
```
