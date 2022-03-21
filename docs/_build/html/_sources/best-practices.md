# Best practices

## 2.1 Meaningless function names

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

## 2.2 Using location.pathname based logic
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
```ts
<Routes>
    <Route path="/properties/*" element={<PropertySearch />} />    
    <Route path="/admin/*" element={<AdminConsole />} />
    <Route path="/" element={<Navigate to="/properties" />} />
</Routes>
```

## 2.3 Using lots of useState

Combine to single state for better performance

## 2.4 Using useState for reference types

shallow copy with useState

## 2.5 shallow copy for easy-peasy

## 2.6 named export + memo

## 2.7 avoid props in favor of direct store access

## 2.8 wrap components to facades