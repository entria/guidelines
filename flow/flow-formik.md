# Flow when using Formik

- Prefer withFormik HOC instead of Formik render props

## Install formik typedefs
```bash
flow-typed install formik@x.x.x
```

## Type form *Values*

```jsx
type Values = {
  text: string,
  score: number,
};
```

## Type component props as OwnProps
```jsx
type OwnProps = {
  query: Component_query,
  requestId: string,
};
```

## Type component final props
```jsx
import type { FormikProps } from 'formik';

type Props = OwnProps & FormikProps<OwnProps, Values>;
```

### Use withFormik
```jsx
const MyForm = withFormik({
  mapPropsToValues: () => ({
    text: '',
    score: 5,
  }),
  validationSchema: Yup.object().shape({
    text: Yup.string().required(),
  }),
  handleSubmit: (values: Values, actions) => {
    const { setSubmitting, props } = actions;

    const { score, text } = values;
    const { isSubmitting } = props;

    if (isSubmitting) return;

    // TODO - call mutation
  },
})(MyComponent);
```


