[`Sesión 01`](../Readme.md) > `Ejemplo 2`

## Ejemplo 2: Loaders 101 

<div style="text-align: justify;">

### 1. Objetivos :dart:

- Instalar y utilizar los *loaders* para procesar estilos de CSS
- Ver nuestra aplicación web corriendo en el navegador

### 2. Requisitos :clipboard:

1. Node.js
2. npm
3. Un editor de texto
4. El ejemplo anterior terminado

### 3. Desarrollo :rocket:

Vamos a trabajar con los mismos archivos que en el ejemplo anterior. 

1. Dentro de la carpeta `src` crear una hoja de estilos con el nombre `styles.css`

    ```bash
    touch src/styles.css
    ```

2. Agregar los siguientes estilos a la hoja de estilos que acabamos de crear

    ```css
    body {
    	background-color : red;
    }
    ```

3. Hasta ahora tenemos una aplicación que utiliza <b>Webpack</b> y que hace absolutamente nada. Vamos a darle funcionalidad a la aplicación, para esto modificamos el archivo `index.js` que creamos en el ejemplo 1 dentro de la carpeta `src`. Agregamos lo siguiente:

    ```javascript
    import './styles.css'

    console.log('Hola Mundo')
    ```

	Primero importamos la hoja de estilos y luego simplemente escribimos en la consola 'Hola Mundo'.

4. Ahora vamos a hacer que <b>Webpack</b> reconozca los estilos, para esto primero instalamos las siguientes dependencias usando `npm`: 
	- css-loader
	- style-loader 

   Estas dependencias corresponden a los *loaders* que le indican a <b>Webpack</b> como procesar los archivos CSS y agregar estilos a nuestro *bundle*.
    ```bash
    npm i css-loader --save-dev

    npm i style-loader --save-dev
    ```
5. Ya tenemos los *loaders* instalados, ahora tenemos que modificar la configuración de <b>Webpack</b> para que los utilice. Recordemos que la configuración de <b>Webpack</b> se encuentra en el archivo `webpack.config.js` lo modificamos de la siguiente forma:

    ```javascript
    const path = require('path');

    module.exports = {
    	entry: './src/index.js',
  		output: {
    		path: path.resolve(__dirname, 'dist'),
    		filename: 'bundle.js'
  		},
  		module: {
    		rules: [
      			{
        			test: /\.css$/,
        			use: [
          				'style-loader',
          				'css-loader'
        			]
      			}
    		]
  		}
	};
    ```
    En este caso se agrega un nuevo módulo y se definen las reglas de este, el atributo `test` corresponde a una expresión regular que se usa para representar los archivos que se procesaran según estas reglas, en este caso todos los que terminen en `.css` es decir hojas de estilo de CSS.

    Mientras que el atributo `use` le indica a <b>Webpack</b> qué *loaders* debe utilizar para procesar estos archivos.

    Si se quisiera especificar como procesar otro formato de archivo se tendría que agregar una nueva regla que defina estos mismos campos (`test` y `use`) dentro del mismo arreglo y en el caso de que el *loader* no corresponda al formato de los archivos o no esté instalado la aplicación regresará un error.


6. Ahora vamos a correr el proyecto y dejar que <b>Webpack</b> haga su magia.

    ```bash
    npm run build
    ```

7. Dentro de la carpeta `dist` se creo el archivo `index.html` este archivo es nuestra aplicación web generada por <b>Webpack</b> a partir de los módulos de JavaScript que definimos. Lo abrimos en un navegador y vemos que en efecto cargo los estilos como esperábamos.

[`Anterior`](../Readme.md#loaders) | [`Siguiente`](../ejemplo-03/Readme.md)

</div>


