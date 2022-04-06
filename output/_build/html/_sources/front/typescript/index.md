# Typescript best practices

## Enums

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