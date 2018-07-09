# FlatList guideline

A very common pattern is to render a list of items, or a Relay cursor using a FlatList or SectionList.

like this one:

```jsx
<FlatList
  data={notifications.edges}
  keyExtractor={item => item.node.id}
  renderItem={this.renderItem}
  onEndReached={this.onEndReached}
  onRefresh={this.onRefresh}
  refreshing={this.state.isFetchingTop}
/>
```

1. Define 2 states to handle `onEndReached` and `onRefresh`

- isFetchingTop - should be true when is doing a force fetch onRefresh call (refreshing data)
- isFetchingEnd - should be true when onEndReached is called (loading more data)


# onRefresh Relay Modern

I think we can abstract this into a function

```jsx
onRefresh = () => {
    const { isFetchingTop } = this.state;

    if (isFetchingTop) return;

    this.setState({ isFetchingTop: true });

    const refetchVariables = fragmentVariables => ({
      ...fragmentVariables,
    });
    this.props.relay.refetch(
      refetchVariables,
      null,
      () => {
        this.setState({
          isFetchingTop: false,
          isFetchingEnd: false,
        });
      },
      {
        force: true,
      },
    );
};
```

# onEndReached Relay Modern (createRefetchContainer)

```jsx
onEndReached = () => {
    const { isFetchingEnd } = this.state;

    if (isFetchingEnd) return;

    const { notifications } = this.props.query.me;

    if (!notifications.pageInfo.hasNextPage) return;

    this.setState({
      isFetchingEnd: true,
    });

    const { endCursor } = notifications.pageInfo;

    const total = notifications.edges.length + TOTAL_REFETCH_ITEMS;
    const refetchVariables = fragmentVariables => ({
      ...fragmentVariables,
      first: TOTAL_REFETCH_ITEMS,
      after: endCursor,
    });
    const renderVariables = {
      first: total,
    };

    this.props.relay.refetch(
      refetchVariables,
      renderVariables,
      () => {
        this.setState({
          isFetchingEnd: false,
          isFetchingTop: false,
        });
      },
      {
        force: false,
      },
    );
};
```
