# project setup 

  "path-intellisense.mappings": {
    "@": "${workspaceFolder}/front/src/",
    "@config": "${workspaceFolder}/front/src/@config/",
    "@components": "${workspaceFolder}/front/src/@components/",
    "@types": "${workspaceFolder}/front/src/@types/",
    "@services": "${workspaceFolder}/front/src/@services/",
    "@store": "${workspaceFolder}/front/src/@store/",
    "@hooks": "${workspaceFolder}/front/src/@hooks/",
    "@utils": "${workspaceFolder}/front/src/@utils/",
    "@mocks": "${workspaceFolder}/front/mocks/"
  }, 
 
# react

- no default imports
- HOOKS: use<Entity> name, not useCalculate
- sort imports
- move hooks from index to external file

# typescript

- use PartialDeep
- https://google.github.io/styleguide/tsguide.html
- https://www.itwinjs.org/learning/guidelines/typescript-coding-guidelines/

# plugins 
SonarCloud linting IDE plugin
https://docs.sonarcloud.io/improving/sonarlint/