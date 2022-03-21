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

## Folder structure overview
```
FirstKey.Acquire.Web
├── front
│   ├── assets
│   ├── mocks
│   ├── src
│   │   ├── @components 
│   │   ├── @config
│   │   ├── @hooks
│   │   ├── @services
│   │   ├── @store
│   │   ├── @types
│   │   ├── @utils
│   │   ├── Contexts
│   │   ├── Pages
│   │   ├── Validation
│   │   ├── App.less
│   │   ├── App.tsx
│   │   ├── Content.tsx
│   │   └── index.ts
│   ├── tests
│   └── typings
├── wwwroot
└── package.json
```

## 1.1 Eslint & Prettier

For styling & formatting of any aspect of front-end code we use ESLint with mostly airbnb presets & Prettier.

In typescript files ESLint errors & warnings will be highlighted if using VS Code extension [`ESLint extension`](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

To check eslint in all files run command

> yarn build

Or for deeper but slower test use

> yarn test:ci

Lots of useful eslint rules are turned off because of amount of fixes needed to use such rules. So to increase the code quality you can switch on some of rules listed in **toBeFixed** section in the .eslintrc file and fix lint errors.

## 1.2 Project structure & imports

- use index.ts for cleaner imports from @components/hooks etc.
- place common components in @components
- do not use Helpers or any other common React files. Only pure js/ts service functions should be placed in various utils.ts files

## 1.3 Component file formatting

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

### 1.3.1 100 lines rule

Bob Martin takes the idea that “if small is good, then smaller must be better” to an extreme in Clean Code:

> The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that. Functions should not be 100 lines long. Functions should hardly ever be 20 lines long.

This can be fully applied to the components of the react.

### 1.3.2 Do not use functions to generate html, prefer child components

❌ **Not: use getContent, buttonsFactory or similar**

```typescript
const Component: FC = () => {
  const getTooltipContent = (options: string[]) => {
    return options.map((option) => {
      return;
    });
  };
  const createTooltipContentItem = (title: string): ReactNode => (
    <div className={`text-base flex nowrap justify-between items-center`}>
      {title}
    </div>
  );

  return <div>{getTooltipContent(["one", "two", "three"])}</div>;
};
```

✅ **Do: prefer create of a separate components**

```tsx 
type TProps = {
  title: string;
};
const TooltipContentItem: FC<TProps> = ({ title }) => (
  <div className={`text-base flex nowrap justify-between items-center`}>
    {title}
  </div>
);
```
```tsx 
const Component: FC = () => (
  <div>
    {["one", "two", "three"].map((option) => (
      <TooltipContentItem option={option} />
    ))}
  </div>
);
```

### 1.3.3 Place all additional code as pure functions under component or in separate file
// TODO: add example

### 1.3.4 Remove all store state/actions mappings to mapState/mapActions
// TODO: add shallowCopy to mappings

❌ **Not:**

```typescript
const Component: FC = () => {
  const userName = useStore((state: TStoreState) => authentication.userName);
  const price = useStore((state: TStoreState) => offer.price);
  ...
}
```

✅ **Do:**

```javascript
const Component: FC = () => {
  const { userName, price } = useStore(mapState);
  ...
}

function mapState(state: TStoreState) {
  return {
    userName: state.authentication.userName,
    price: state.offer.price
  }
}
```

## 1.4 Naming conventions

### 1.4.1 Enums

Enums are typescript types, named with a capital T without a plural

❌ **Not:**

```ts
export type MyStatuses = {
  NEW = 'New',
  ASSIGNED = 'Assigned',
  ...
}
```

✅ **Do:**

```ts
export type TStatus = {
  NEW = 'New',
  ASSIGNED = 'Assigned',
  ...
}
```

