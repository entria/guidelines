# Flow using ReactNavigation

### Type your Navigation Params

- [ ] use NavigationScreenProp

this will make easier to other developers reuse this component

```jsx
import type { NavigationScreenProp } from 'react-navigation';

type NavigationState = {
  params: {
     userId: string,
  }
};

type Props = {
  navigation: NavigationScreenProp<NavigationState>,
};

class MyRootComponent extends React.Component<Props> { ... }
```
