# Lint Staged

Use [lint-staged](https://github.com/okonet/lint-staged) to make your code uniform.

Example of Lint-staged config:

"lint-staged": {
    "*.js": [
      "prettier --write --single-quote true --trailing-comma all --print-width 100",
      "yarn lint --fix",
      "yarn lint:css"
      "flow focus-check",
      "jest --bail --findRelatedTests"
      "git add"
    ]
  },

## Prettier

Use [Prettier](https://github.com/prettier/prettier) to make your code uniform, do not fight your friends
about code style anymore.

## Eslint

Use eslint to catch some bugs before commiting code

## Stylelint

Get StyledComponents css bugs before commiting code

## Flow

Flow won't let your ship bugs to your code base

## Jest

Run related tests based on files that changed. https://benmccormick.org/2017/02/26/running-jest-tests-before-each-git-commit/

## Check GraphQL Schema Breaking Changes

Use this [cli](https://github.com/entria/graphql-find-breaking-changes-cli) to finding GraphQL Schema breaking
changes before commiting it
