[`Sesión 01`](../README.md) > `Ejemplo 3`

## Ejemplo 3: Loaders 102 

<div style="text-align: justify;">

### 1. Objetivos :dart:

- Extender la lógica del ejemplo anterior para que nuestra aplicación reconozca mas formatos de estilos (SCSS).
- Lograr que <b>Webpack</b> procese imágenes.

### 2. Requisitos :clipboard:

1. Node.js
2. npm
3. Un editor de texto
4. El ejemplo anterior terminado

### 3. Desarrollo :rocket:

Vamos a trabajar con los mismos archivos que en el ejemplo anterior. Si se desea conservar todos los ejemplos se recomienda guardar cada uno como un commit en git.

1. Descargar la siguiente <a href="https://github.com/jaeem006/C1-React/blob/master/Sesion01-webpack/ejemplo-03/src/background-640x320.jpg">imagen</a> y guardarla en la carpeta `src` de nuestro proyecto con el nombre `background-640x320.jpg`.

2. Modificar la hoja de estilos que creamos en el ejemplo anterior para que ahora utilice SCSS para esto cambiamos la extensión del archivo a  `styles.scss`. Se modifica también el contenido del archivo 

    ```scss 
    body {
  		background-image: url('./background-640x320.jpg');
	}
    ```

3. Ahora modificamos el archivo `index.js` que creamos en el ejemplo 1 dentro de la carpeta `src` cambiando el `import` de estilos para que corresponda con las modificaciones del inciso anterior, resultando en:

    ```javascript
    import './styles.scss'

    console.log('Hola Mundo')
    ```

4. Instalamos las dependencias necesarias para reconocer archivos SCSS usando `npm`: 
	- file-loader
	- node-sass
	- sass-loader

    ```bash
    npm i file-loader --save-dev

    npm i node-sass --save-dev

    npm i sass-loader --save-dev
    ```
5. Por último cambiamos las reglas de definidas en el ejemplo anterior para procesar estilos dentro del archivo de configuración de <b>Webpack</b> 

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
        			test: /\.scss$/,
			        use: [
			          'style-loader',
			          'css-loader',
			          'sass-loader'
			        ]
      			},
      			{
			        test: /\.(png|svg|jpg|gif)$/,
			        use: [
			          'file-loader'
			        ]
			    }
    		]
  		}
	};
    ```
    Primero se modifica la regla para procesar estilos, cambiando el formato que se busca a SCSS y cambiando los *loaders* que se deben usar. Y se agrega una nueva regla para procesar imagenes en diferentes formaros y se indica que el *loader* a usar será `file-loader`


6. Ahora vamos a correr el proyecto.

    ```bash
    npm run build
    ```

7. Abrimos el archivo `index.html`  en un navegador.

La lista completa de los *loaders* disponibles se puede consultar en la siguiente <a href="https://webpack.js.org/loaders/">página</a>

[`Anterior`](../ejemplo-02/README.md) | [`Siguiente`](../README.md)

</div>


