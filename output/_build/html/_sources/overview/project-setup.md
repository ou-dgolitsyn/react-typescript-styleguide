# Project setup

## Rider setup
- run scripts
- format code with prettier (https://www.jetbrains.com/help/rider/Prettier.html)
- set up linting (https://www.jetbrains.com/help/rider/eslint.html#ws_eslint_configure_highlighting)

## VS Code setup
- run scripts
- install prettier plugin
- install eslint
- custom settings

## Eslint & Prettier

For styling & formatting of any aspect of front-end code we use ESLint with mostly airbnb presets & Prettier.

In typescript files ESLint errors & warnings will be highlighted if using VS Code extension [`ESLint extension`](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

To check eslint in all files run command

> yarn build

Or for deeper but slower test use

> yarn test:ci

Lots of useful eslint rules are turned off because of amount of fixes needed to use such rules. So to increase the code quality you can switch on some of rules listed in **toBeFixed** section in the .eslintrc file and fix lint errors.

## Project structure & imports

- use index.ts for cleaner imports from @components/hooks etc.
- place common components in @components
- do not use Helpers or any other common React files. Only pure js/ts service functions should be placed in various utils.ts files

## Component file formatting

This is the preferred code layout for react component file:

```typescript
import <es modules imports>;

const Component: FC<TProps> = () => {
  // Code of component no more than 100 lines long
}

function mapState(state: TStoreState) {
  // Pure functions used exclusively by the component
}

type TProps = {
  // Type declaration for component properties
}
```


### Place all additional code as pure functions under component or in separate file
// TODO: add example



## Naming conventions



