[`Sesión 01`](../README.md) > `Ejemplo 1`

## Ejemplo 1: Estructurar la aplicación

<div style="text-align: justify;">

### 1. Objetivos :dart:

- Comenzar de cero un proyecto que utilice <b>Webpack</b>
- Recordar como instalar dependencias usando `npm`

### 2. Requisitos :clipboard:

1. Node.js
2. npm
3. Un editor de texto

### 3. Desarrollo :rocket:

1. Desde la terminal, posiciónate en la carpeta correspondiente a el proyecto (que este vacía) que vamos a crear. 
2. Inicializa un proyecto usando `npm`

    ```bash
    npm init 
    ```

3. Configura el proyecto aceptando las elecciones por default.
4. Crea una carpeta `src` 

    ```bash
    mkdir src  
   ```
5. Crea un archivo con el nombre `index.js` dentro de `src`
    ```bash
    touch src/index.js
    ```
6. Crea un archivo con el nombre `webpack.config.js` este será el archivo de configuración de <b>Webpack</b>
    ```bash
    touch webpack.config.js
    ```
7. Instalar las siguientes dependencias usando `npm`: 
	- webpack
	- webpack-cli 

   Estas dependencias son para utilizar <b>Webpack</b> y la interfaz de línea de comando de <b>Webpack</b> respectivamente.
    ```bash
    npm i webpack --save-dev

    npm i webpack-cli --save-dev
    ```
Recordemos que la bandera `--save-dev` sirve para que estas dependencias se agreguen a la configuración del proyecto en el archivo `package.json` y sean cargadas automáticamente al hacer la instalación por default de `npm`.

8. Verificar el archivo `package.json` el objeto `scripts` debe contener el siguiente atributo `"build": "webpack"` de no ser así agregarlo.

9. Ahora solo resta configurar <b>Webpack</b> para eso modificaremos el archivo `webpack.config.js` que acabamos de crear agregándole lo siguiente:

    ```javascript
    const path = require('path')

    module.exports = {
      	entry: './src/index.js',
      	output: {
      		path: path.resolve(__dirname, 'dist'),
      		filename: 'bundle.js'
      	}
    }

    ``` 

En esta configuración se están definiendo los atributos de exportación del módulo, en este se pueden observar dos atributos `entry` y `output`.

El atributo `entry`define el *entry point* que es el archivo principal de mi aplicación, en archivo en donde se definen (se hace el `build`) de los módulos que se van a definir en el proyecto.

Mientras que el atributo `output` indica el archivo de salida, es decir el archivo en el cual se va a crear el *bundle* del proyecto. Este es el archivo que el navegador va a leer y que será capaz de interpretar y mostrar. El archivo en donde todo el proyecto está empaquetado. 

Dentro de `output` tenemos a su vez dos atributos más `path` que va a definir la ruta en donde se encuentra el archivo y `filename`que es simplemente el nombre del archivo. En este ejemplo vamos a guardar el *bundle* en una carpeta `dist` con el nombre `bundle.js`.

[`Anterior`](../README.md#webpack) | [`Siguiente`](../README.md#loaders)

</div>

