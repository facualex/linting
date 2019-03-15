# Linter + Formatter

Este repositorio sirve para dar instrucciones y archivos de partida para implementarlo en los proyectos. Se usan las herramientas [ESLint](https://eslint.org/) y [Prettier](https://prettier.io/).

Inicialmente se tendrán los settings para proyectos de:

1. React
2. React Native
3. Node

## Pasos generales
Se recomiendan los siguientes pasos, independiente de la plataforma en la que se vaya a programar (react, node, etc...)

* Instalar [extension ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) para VSCode de Dirk Baeumer
* En el root del proyecto, crear directorio  `.vscode/` y adentro archivo `settings.json` con el siguiente contenido. Esto sirve el proposito de hacer compatible el vscode con eslint y prettier.
```json
{
  "editor.formatOnSave": false,
  "javascript.format.enable": false,
  "eslint.enable": true,
  "eslint.autoFixOnSave": true,
  "eslint.alwaysShowStatus": true,
  "eslint.options": {
    "extensions": [
      ".html",
      ".js",
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
* Crear el archivo `.eslintignore` en el root del proyecto con el siguiente contenido. Esto sirve el proposito de no analizar ni formatear directorios irrelevantes.
```
/.git
/.vscode
node_modules
```
* Instalar dependencias de desarrollo, algunas son comunes entre proyectos, y otras son especificas para el tipo de proyecto.
  
  1. React: `npm i -D babel-eslint eslint eslint-config-airbnb eslint-plugin-babel eslint-config-prettier eslint-plugin-prettier prettier eslint-plugin-import eslint-plugin-react eslint-plugin-jsx-a11y eslint-config-kentcdodds` 
  2. React-native: `npm i -D babel-eslint eslint eslint-config-airbnb eslint-plugin-babel eslint-config-prettier eslint-plugin-prettier prettier eslint-plugin-import eslint-plugin-react eslint-plugin-jsx-a11y eslint-plugin-react-native`
  3. Node:  `npm i -D babel-eslint eslint eslint-config-airbnb-base eslint-plugin-babel eslint-config-prettier eslint-plugin-prettier prettier eslint-plugin-import eslint-config-kentcdodds` 

* Agregar los scripts del linter al `package.json` en la propiedad `"script"`. Estos sirven para ejecutar el linter y el formateador a todo el proyecto sin necesidad de ir archivo por archivo. Cambiar `app/` por el directorio donde esta el codigo a analizar, o poner `.` si se debe analizar desde el root del proyecto (tomando en cuenta que ignorara los directorios en `.eslintignore`

  1. `npm run lint` va a listar en consola todos los problemas que hay en el proyecto, archivo por archivo.
  2. `npm run lint:write` va a intentar arreglar tantos problemas como sea posible sin compremeter el funcionamiento del proyecto y listará los problemas restants, que deben ser arreglados manualmente.
  
```js
  "scripts":{
    //Sin sobrescribir los scripts previos, se ingresan despues
     "lint": "eslint --debug app/",
    "lint:write": "eslint --debug app/ --fix",
  }
```
* Crear los archivos de configuración de eslint en el root del proyecto, que pueden ser `.eslintrc.js` o `.eslintrc`. Se prefiere la extensión `.js` para tratarlo como un modulo de javascript. En este repositorio hay archivos base para las 3 plataformas previamente mencionadas, cada uno de estos en un directorio con el nombre correspondiente (por ej: react/eslintrc.js).