# Flow-typed

[flow-typed](https://github.com/flowtype/flow-typed) provides type definition for a lot of packages.

## How to add a typedef from flow-typed:

```sh
flow-typed install redux
```

Commit the typedef to your codebase (git)

## Should I add stubs?

No, stubs does not help at all. It will be `any` anyway.

## How to write a typedef for flow-typed

Create a <module-name>.js inside flow-typed of your projects, and start adding typedefs that you need for your project.
Feel free to send a partial typedef to flow-typed and let others improved, that's how open source is done.
Also follow this guide https://flow.org/en/docs/libdefs/creation/
