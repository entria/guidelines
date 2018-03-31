# How to easily type Redux Props with Flow

## Add ExtractReturn helper

```jsx
// https://hackernoon.com/redux-flow-type-getting-the-maximum-benefit-from-the-fewest-key-strokes-5c006c54ec87
// https://github.com/facebook/flow/issues/4002
// eslint-disable-next-line no-unused-vars
type _ExtractReturn<B, F: (...args: any[]) => B> = B;
export type ExtractReturn<F> = _ExtractReturn<*, F>;
```
You could also use `$Call` helper instead

## Extract return of mapStateToProps and mapDispatchToProps

```jsx
const mapStateToProps = (state: ReduxState, props: OwnProps) => ({
  user: state.user,
});
const mapDispatchToProps = (dispatch: Dispatch) => ({
  actions: {
    logout: () => dispatch(logout()),
  },
});

type ReduxProps = ExtractReturn<typeof mapStateToProps>;
type ReduxActions = ExtractReturn<typeof mapDispatchToProps>;
```

## Add ReduxProps and ReduxActions to your Component props

```jsx
type OwnProps = {
   a: string,
}
type Props = OwnProps & ReduxProps & ReduxState

class EntriaComp extends Component<Props> {}
```

## Type your Reducers State
- TODO

## Extract types of your actions
- TODO
