# Snapshot testing

## What is snapshot testing

Snapshots are string representations of html code being output by a component.

> 
> Details about snapshots
> 

Snapshots are generated automatically for each component story or manually with jest.

>
> Example of manual snapshot
>
 
Every component in app shoud be covered with at list one type of a snapshot test.

Snapshots are being placed in __snapshots__ folder
Snapshots should be reviewed

When component is changed. A single snapshot should be fixed

jest -u -t="ColorPicker"
where "ColorPicker" is name of the spec, given in describe or test blocks.

>
> Tips for snaphot review: not allow to mass remove/update snapshots if no corresponding component
> 

## Automatically generate snapshot tests in storybook

## Working with a snapshots 