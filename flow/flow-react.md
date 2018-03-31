# Flow in React

## Always type your Props

```jsx
type Props = {
   isLoading: boolean,
   children: React.Node,
}

const TextWithLoading = ({ isLoading, children }: Props) => {
   if (isLoading) return <Loading />

   return children;
}
```

### Type your State if needed

```jsx
type Props = {};
type State = {
   isFetching: boolean,
};

class ItemList extends React.Component<Props, State> {
   state = {
      isFetching: false,
   };

   onEndReached = () => {
      this.setState({ isFetching: true });
   }

   render() { ... }
}
```
