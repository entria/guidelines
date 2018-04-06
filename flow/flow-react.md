# React components

### Always type your Props and State

### Stateless
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

### Stateful
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
