[`Sesión 01`](../README.md) > `Ejemplo 3`

## Ejemplo 4: Plugins 101 

<div style="text-align: justify;">

### 1. Objetivos :dart:

- Aprender a instalar y configurar *plugins*
- Observar la utilidad de los *plugins*.
- Extender las funcionalidades de la configuración hecha hasta el momento.

### 2. Requisitos :clipboard:

1. Node.js
2. npm
3. Un editor de texto
4. El ejemplo anterior terminado

### 3. Desarrollo :rocket:

Vamos a trabajar con los mismos archivos que en el ejemplo anterior. Si se desea conservar todos los ejemplos se recomienda guardar cada uno como un commit en git.

1. La instalación de *plugins* es a través de `npm` de la misma forma que se instalan *loaders*. Instalamos las siguientes dependencias: 

- clean-webpack-plugin: este *plugin* sirve para mantener el proyecto limpio, es decir sin *trash-files* que son generados como archivos intermedios en el proceso de construcción.
- html-webpack-plugin: que simplifica la creación de archivos HTML.

    ```bash
    npm i clean-webpack-plugin --save-dev

    npm i html-webpack-plugin --save-dev
    ```

2. Una vez instalados los *pligins* se deben configurar dentro del archivo de configuración de <b>Webpack</b>. 

 	Para poder usar un *plugin* se debe importar con una instrucción `require()`.

    ```javascript
    const HtmlWebpackPlugin = require('html-webpack-plugin');
    ``` 

 	y agregar una instancia de estos al arreglo `plugins` de los atributos de exportación del módulo, esto es con la instrucción `new` que construye la instancia. 

    ```javascript
	plugins: [
		new HtmlWebpackPlugin({
		    title: 'Hello From webpack!!!!'
		})
	]
	```
	los parámetros que reciben los constructores dependen del *plugin* y deben consultarse en la documentación de estos. Por ejemplo en el <a href="https://webpack.js.org/plugins/html-webpack-plugin/">link</a> se puede consultr la documentación de este *plugin*.

	El código completo después de la configuración de ambos *plugins* es: 

    ```javascript
    const path = require('path');
    const HtmlWebpackPlugin = require('html-webpack-plugin');
    const { CleanWebpackPlugin } = require('clean-webpack-plugin');

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
  		},
  		plugins: [
    		new CleanWebpackPlugin(),
    		new HtmlWebpackPlugin({
      			title: 'Hello From webpack!!!!'
    		})
  		]
	};
    ```
3. Observemos como en esta ocasión el archivo `index.html` fue generado automáticamente después de la construcción.


[`Anterior`](../README.md) | [`Siguiente`](../README.md) 

</div>


