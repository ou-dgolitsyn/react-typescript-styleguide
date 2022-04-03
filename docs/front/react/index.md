# React best practices

## Meaningless function names

❌ **Not: name function like check, perform, process** 
1. Function does not check status, but validates selectedPropertiesData
2. Until you read function's code you cannot guess if true means valid or not
```ts
function checkStatus() {
  return (isEmpty(selectedPropertiesData) || !selectedPropertiesData.every((prop: any) => prop.status === selectedPropertiesData[0].status);)
}
```

✅ **Do: prefer to name functions like getSomething**

Function name is self explanatory
```ts
function getIsReadyForStatusUpdate() {
  // Allow to update status if there are selected properties
  if (!isEmpty(selectedPropertiesData)) return false;

  // And all selected properties are in the same status
  return selectedPropertiesData.every((prop: any) => prop.status === selectedPropertiesData[0].status);
}
```

## Using location.pathname based logic
❌ **Not: use location.pathname in any conditions** 
```ts
    switch (pathname) {
        case '/properties':
            tabs = ListingSearchButtons;
            searchBar = searchComp;
            break;
        case '/admin':
            tabs = null;
            break;
        default:
            if (location.includes(`${listingSearch}/`) && location.length > 12) {
                tabs = null;
            }
            break;
    }
```

✅ **Do: prefer to use routing**

Function name is self explanatory
:::{code-block} jsx
<Routes>
    <Route path="/properties/*" element={<PropertySearch />} />    
    <Route path="/admin/*" element={<AdminConsole />} />
    <Route path="/" element={<Navigate to="/properties" />} />
</Routes>
:::

## Using lots of useState

Combine to single state for better performance

## Using useState for reference types

shallow copy with useState

## shallow copy for easy-peasy

## named export + memo

## avoid props in favor of direct store access

## Do not use functions to generate html, prefer child components

❌ **Not: use getContent, buttonsFactory or similar**

```{code-block} jsx
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

```{code-block} jsx
type TProps = {
  title: string;
};
const TooltipContentItem: FC<TProps> = ({ title }) => (
  <div className={`text-base flex nowrap justify-between items-center`}>
    {title}
  </div>
);
```
```{code-block} jsx
const Component: FC = () => (
  <div>
    {["one", "two", "three"].map((option) => (
      <TooltipContentItem option={option} />
    ))}
  </div>
);
```

## Remove all store state/actions mappings to mapState/mapActions
// TODO: add shallowCopy to mappings

❌ **Not:**

```ts
const Component: FC = () => {
  const userName = useStore((state: TStoreState) => authentication.userName);
  const price = useStore((state: TStoreState) => offer.price);
  ...
}
```

✅ **Do:**

```ts
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