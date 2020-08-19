## Sesión 05: Hooks

🎯 **Objetivos:**

- Introducción de los **hooks**.
- Porqué **usarse** y **ventajas**.
- De componente **stateful (clase) a hook**.

---

<!-- ### Secciones:

## 🛠 Prework

**Objetivos:**

- Saber que son los hooks

**Hooks**

La palabra Hook se traduce como Gancho en español, y la razón de que esta nueva API tenga este nombre, es que como indica la documentación...[`leer mas`](Prework) -->

Los *hooks* son una nueva característica implementada a partir de la versión 16.8 de React.js. Y nos permiten utilizar estado y otras funcionalidades importantes de React sin tener que escribir una clase, es decir, sin necesidad de definir nuestros componentes como clases. Son funciones que te permiten “enganchar” el estado de React y el ciclo de vida desde componentes funcionales.

## Incorporación 

Es muy importante notar que los *hooks* son:

+ Opcionales.
+ Compatibles con las versiones anteriores

Este nuevo feature de React no significa que se eliminará el modelo de clases, es simplemente otra opción para definir estado y viven en perfecta armonía con todo lo visto hasta ahora. Y nos ofrecen una nueva y poderosa forma de combinar todos los conceptos que ya conocemos de React.js.

## Motivación 

Los Hooks resuelven una amplia variedad de problemas aparentemente desconectados en React que se han encontrado durante el tiempo que React lleva en el mercado.

+ <b>Es difícil reutilizar la lógica de estado entre componentes </b>, es decir, es difícil definir componentes con características similares pero comportamientos diferentes. En la sesión anterior vimos como tratar este problema usando componentes de orden superior, es decir componentes que reciben como *prop* una función que define su comportamiento, sin embargo eso implica una reestructuración del componente que no siempre es una tarea sencilla, sobre todo cuando se trata de aplicaciones muy grandes. <b>Los *hoobks* facilitan reutilizar lógica de estado sin cambiar la jerarquía de tu componente</b>.

+ <b>Los componentes complejos se vuelven difíciles de entender</b>, como se noto la sesión anterior, algo que en el modelo se podría ver como un componente sencillo (un botón por ejemplo) puede desencadenar una serie de cambios derivados de las necesidades de la aplicación y convertirse en un componente de clase lleno de métodos auxiliares, una gran cantidad de *props* necesarios para su funcionamiento, métodos ciclos de vida, etc. En resumen un componente se vuelve complejo y eso lo hace difícil de leer y sobre todo de manipular. En muchos de los casos este problema se resuelve dividiendo el componente en otros mas pequeños pero el uso del estado nos lo impide. <b>Los *hooks* te permite dividir un componente en funciones más pequeñas basadas en las piezas relacionadas</b>.

+ <b>Las clases son mas complicadas de usar, no sólo para los desarrolladores sino también para la máquina</b>, la curva de aprendizaje de clases es mucho mas grande que la de funciones, se tiene que entender el funcionamiento de los constructores, la palabra reservada `this`, el método `render()`, el manejo de los ciclos de vida, manejo de estado, etc. Por si no fuera poco el navegador tarda mas en interpretar, renderizar y actualizar componentes de clase respecto a los funcionales. <b>Los *hooks* te permiten usar más de las funciones de React sin clases sin sacrificar el espíritu práctico de React.</b>

+ [`Ejemplo 01: Incrementando de nuevo`](Ejemplo-01/Readme.md)
+ [`Reto 01: 3 botones`](Reto-01/Readme.md)

---

## Hook de Estado

Como acabamos de ver, la forma de usar estado con *hooks* es diferente a como se hace con componentes *stateful*. En este caso para definir una variable del estado se tiene que usar la función `useState()` que es un *hook*, el único argumento para `useState` es el estado inicial, en el ejemplo anterior le pasamos `0` esto es porque el contador empieza en 0. `useState` regresa un par con el valor del estado actual y una función para actualizarlo (similar a `setState`). 

En el siguiente ejemplo se puede ver como se declara una variable de estado, con el nombre `count` y el valor incial `0`.

	const [count, setCount] = useState(0);

Ten en cuenta que a diferencia de `this.state`, el estado aquí no tiene que ser un objeto. 



Se puede utilizar el *hook* de estado mas de una vez en el mismo componente. Por ejemplo:

	const [age, setAge] = useState(42);
	const [fruit, setFruit] = useState('banana');
	const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);

En donde se declaran tres variables de estado.

Usamos la sintaxis de destrucción de un arreglo para dar nombres a las variables de estado declaradas con `useState` así como a las funciones de actualización.


+ [`Ejemplo 02: Patricio evoluciona`](Ejemplo-02/Readme.md)
+ [`Reto 02: ¡Pero quiere otro!`](Reto-02/Readme.md)

---

## Leyendo el estado

Con el uso de estado en componentes de clase para poder leerlo se hacía de la siguiente forma:

	<p>You clicked {this.state.count} times</p>

Con el uso de *hooks* las variables de estado son al mismo tiempo variables del componente por lo que leerlas se hace de la siguiente forma:

	<p>You clicked {count} times</p>


Mostrando una vez mas la principal ventaja del uso de *hooks* código mas compacto y legible.

+ [`Ejemplo 03: Escuela`](Ejemplo-03/Readme.md)
+ [`Reto 03: ¿Cómo te llamas?`](Reto-03/Readme.md)


React proporciona algunos Hooks incorporados como `useState` o `useEffect`. También puedes crear tus propios Hooks para reutilizar el comportamiento con estado entre diferentes componentes. Primero veremos los Hooks incorporados.



<!-- ## 🕵 Ejemplos:





## 💻 Retos:





## 🛡 Postwork
- Completar los ejemplo: 01, 02 y 03. 
- Completar los retos: 01, 02 y 03...[`leer más`](Postwork/)

## ⚛ ORGANIZACION DE LA CLASE
- Convertir de **stateful (clase)** a usar **hooks**.
- Usando **useState** para **creación** y **modificación** de **estado (state)**. -->
