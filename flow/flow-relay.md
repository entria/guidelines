# Using Relay Flow __generated__ types in code

- [ ] type Props using generated Relay Flow fragment definitions

```jsx
import type { MyComponent_me } from './__generated__/MyComponent_me.graphql';

type Props = {
    me: MyComponent_me,
};

class MyComponent extends React.Component<Props> {
   render() { ... }
}

export default createFragmentContainer(MyComponent, {
    me: graphql`
        fragment MyComponent_me on Person {
            id
            _id
            name
    }
`,
});
``
