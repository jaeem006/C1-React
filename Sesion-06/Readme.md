## Sesión 07: Rutas con react router dom

🎯 **Objetivos:**

+ Implementar enrutamiento en react guardando y respetando el estado, sin que la página se actualice.

<!-- ### Secciones: -->

<!-- ## 🛠 Prework

**Objetivos:**
+ Conocer que es react router dom.

**¿Qué es React Router?**

Seguramente habrás escuchado sobre React Router y si no es así el día de hoy vas aprender a trabajar con esta librería la cual nos ayuda con el manejo de rutas en nuestra aplicación...[`leer mas`](Prework) -->
## Enrutamiento

El enrutamiento es un mecanismo que reescribe las URL para simplificar su aspecto. Es el proceso por el cual la ruta, o una parte de ella, es determinada. Una de las capacidades características de la Internet, en comparación con otras arquitecturas de red, es que cada router que recibe un paquete de datos determinará de inmediato por su cuenta cuál debe ser el próximo paso en la ruta.

Cuando el usuario realiza una acción, las URL se encargan de enviar la información desde el navegador hasta el servidor. Las URL tradicionales incluyen la ruta hasta el script del servidor y algunos parámetros necesarios para completar la petición, como se muestra en el siguiente ejemplo:

````
http://www.ejemplo.com/web/controlador/articulo.php?id=123456&codigo_formato=6532
````

En la mayoría de los sitios web modernos el enrutamiento se hace de forma automática o dinámica, esto quiere decir (en React) que los componentes son los que se encargan de definir la url, para la navegación entre vistas de un mismo sitio. 

### Single Page Application 

Una SPA es una aplicación web o es un sitio web que cabe en una sola página con el propósito de dar una experiencia más fluida a los usuarios, como si fuera una aplicación de escritorio. En un SPA todos los códigos de HTML, JavaScript, y CSS se cargan una sola vez1​ o los recursos necesarios se cargan dinámicamente cuando lo requiera la página, normalmente como respuesta a las acciones del usuario. La página no tiene que cargarse de nuevo en ningún punto del proceso y tampoco es necesario transferir a otra página. 


Para poder construir SPA en React se usa una biblioteca de enrutamiento de componentes, ésta se llama React Router.

## React Router

React Router es una colección de componentes de navegación la cual podemos usar tanto en web o en móvil con React Native. Con esta biblioteca vamos a obtener un enrutamiento dinámico gracias a los componentes, en otras palabras tenemos unas rutas que renderizan un componente.  React Router se puede trabajar tanto para web como para móvil, siendo `react-router-dom` para web y `react-router-native` para móvil.

### Beneficios de usar React Router Dom

+ Establecer rutas en nuestra aplicación ej: Home, About, User
+ Crear páginas públicas y privadas
+ Realizar redirecciones
+ Acceso al historial del navegador
+ Manejo de rutas con parámetros
+ Páginas para el manejo de errores como 404

### ¿Cómo se usa Router Dom? 

React Router Dom es una biblioteca de React y puede instalarse con `npm` de la misma forma en que se instala cualquier otra dependencia. 

````
npm install --save react-router-dom
````

Una vez instalado se tienen que importar los componentes de navegación en los componentes en donde se vaya a utilizar está biblioteca.

### Componentes de Navegación  de React Router

+ **BrowserRouter**

Este componente es el encargado de envolver nuestra aplicación dándonos acceso al **API** historial de **HTML5 (pushState, replaceState y el evento popstate)** para mantener su UI sincronizada con la URL.

+ **Switch**

Este componente es el encargado de que solo se **renderice el primer hijo Route** o **Redirect** que coincide con la ubicación. 

+ **Route**

Con Route podemos definir las **rutas de nuestra aplicación**, quizás sea el componente más importante de React Router para llegar a comprender todo el manejo de esta biblioteca. Cuando definimos una ruta con Route le indicamos qué **componente debe renderizar**. Este componente cumple las siguientes propiedades.

   1. **Path:** la ruta donde debemos renderizar nuestro componente podemos pasar un string o un array de string.
   2. **Exact:** Solo vamos a mostrar nuestro componente cuando la ruta sea exacta.
   >**Ej:** /home === /home.
   3. **Strict:** Solo vamos a mostrar nuestro componente si al final de la ruta tiene un slash.
   >**Ej:** /home/ === /home/
   4. **Sensitive:** Si le pasamos true vamos a tener en cuenta las mayúsculas y las minúsculas de nuestras rutas.
   >**Ej:** /Home === /Home
   5. **Component:** Le pasamos un componente para renderizar solo cuando la ubicación coincide. En este caso el componente se monta y se desmonta no se actualiza.
   6. **Render:** Le pasamos una función para montar el componente en línea.

[`Ejemplo 01: Anatomía`](Ejemplo-01/Readme.md)

[`Reto 01: Palmera`](Reto-01/Readme.md)

## Paso de parámetros a través de la url 

En muchas ocasiones la comunicación entre las diferentes vistas de una página web se hace a través de la url, esto se debe a que en el proceso de enrutamiento se tienen control total de esta url para pasar a la siguiente vista, y una vez que se haya hecho el cambio, la nueva vista tienen también la información en la url. 

React Router nos permite realizar este intercambio de información, el paso de parámetros a través de la url de una forma sencilla.  

[`Ejemplo 02: Plan de estudios`](Ejemplo-02/Readme.md)

[`Reto 02: Buscando a Memo`](Reto-02/Readme.md)
<!-- ## 🕵 Ejemplos:

+ [`Ejemplo 01: Anatomía`](Ejemplo-01)
+ [`Ejemplo 02: Plan de estudios`](Ejemplo-02)

## 💻 Retos:

+ [`Reto 01: Palmera`](Reto-01)
+ [`Reto 02: Buscando a Memo`](Reto-02)

## 🛡 Postwork
+ Completar el Reto-01
+ Completar el Reto-02...[`leer más`](Postwork/)

## ⚛ ORGANIZACION DE LA CLASE
- react router dom.
- Componente anchor (a).
- Componente Link.
- Parámetros por url.
- Exact path.
 -->