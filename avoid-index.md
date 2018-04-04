# Avoid index.js as much as possible

- index.js does not tell me anything about what is inside the code
- prefer ComponentName.js instead of index.js;
- index.js does not work well with Relay Compat/Modern, as each component should have a different name/filename
- if the component has the same name it should do the same thing
- react native chrome dev tools only show filename, if all files are index.js, you only see errors on index.js files

# When to use index.js

- only use index.js to export components, functions and so on in a project/package
