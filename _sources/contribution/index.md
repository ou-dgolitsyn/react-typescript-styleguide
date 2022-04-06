# Documentation contribution

For the first time check the [brilliant docs](https://jupyterbook.org/start).

To compile the jupyter-book from markdown run:
> jupyter-book build --all ./src --path-output ./output

:::{note}
You can set up automatic build after saving content by using [RunOnSave VS Code extension](https://marketplace.visualstudio.com/items?itemName=emeraldwalk.RunOnSave)
:::

To preview the compiled book run:
> http-server ./output/_build/html

To publish the book to the github pages run:
> ghp-import -n -p -f ./output/_build/html