# Linter + Formatter

Este repositorio sirve para dar instrucciones y archivos de partida para implementarlo en los proyectos. Se usan las herramientas [ESLint](https://eslint.org/) y [Prettier](https://prettier.io/).

Inicialmente se tendrán los settings para proyectos de:

1. React
2. React Native
3. Node

## Pasos generales
Se recomiendan los siguientes pasos, independiente de la plataforma en la que se vaya a programar (react, node, etc...)

* Instalar [extension ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) para VSCode de Dirk Baeumer
* Instalar las dependecias de desarrollo correspondiente a cada plataforma, las cuales son las siguientes.
* En el root del proyecto, crear directorio  `.vscode/` y adentro archivo `settings.json` con el siguiente contenido. Esto sirve el proposito de hacer compatible el vscode con eslint y prettier.
```json
{
  "editor.formatOnSave": false,
  "javascript.format.enable": false,
  "eslint.autoFixOnSave": true,
  "eslint.alwaysShowStatus": true,
  "eslint.options": {
    "extensions": [
      ".html",
      ".js",
      ".vue",
      ".jsx"
    ]
  },
  "eslint.validate": [
    {
      "language": "html",
      "autoFix": true
    },
    {
      "language": "vue",
      "autoFix": true
    },
    {
      "language": "javascript",
      "autoFix": true
    },
    {
      "language": "javascriptreact",
      "autoFix": true
    }
  ]
}
```
* Crear el archivo `.prettierrc` en el root del proyecto con el siguiente contenido. Esto sirve el proposito de definir reglas generales de estilo.
```js
{
  printWidth: 80,
  singleQuote: true,
  trailingComma: 'all',
  bracketSpacing: true,
  jsxBracketSameLine: false,
  tabWidth: 2,
  semi: false,
}
```
* Crear el archivo `.eslintignore`en el root del proyecto con el siguiente contenido. Esto sirve el proposito de no analizar ni formatear directorios irrelevantes.
```
/.git
/.vscode
node_modules
```

