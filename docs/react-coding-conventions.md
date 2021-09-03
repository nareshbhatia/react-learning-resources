# React Coding Conventions

# Import order

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

# Naming of event props and event handlers

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
