# Overview

This repo contains a source of an opinionated style guide for developing complex web applications using ReactJS and Typescript. 

Guide exists in a form of a jupyter-book published on a github-pages. 

[START READING ▶️ ](https://ou-dgolitsyn.github.io/react-typescript-styleguide)

# Compilation

For the first time check the [brilliant docs](https://jupyterbook.org/start).

To compile the jupyter-book from markdown & publish it to gh-pages do the following:

- Fix the content of the .md files in /docs
- Check /docs/_toc.yml for the book structure changes
- Run **jupyter-book build --all ./docs**
- Run **ghp-import -n -p -f ./docs/_build/html**