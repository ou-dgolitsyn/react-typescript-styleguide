# Overview

This repo contains a source of an opinionated style guide for developing complex web applications using ReactJS and Typescript. 

Guide exists in a form of a jupyter-book published on a github-pages. 

[START READING ▶️ ](https://ou-dgolitsyn.github.io/react-typescript-styleguide)

# Develop

For the first time check the [brilliant docs](https://jupyterbook.org/start).

To compile the jupyter-book from markdown run:
> jupyter-book build --all ./src --path-output ./output

To preview the compiled book run:
> http-server ./output/_build/html

To publish the book to the github pages run:
> ghp-import -n -p -f ./output/_build/html