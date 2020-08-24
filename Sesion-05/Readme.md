## Sesión 05: useEffect y Renderizado condicional

### OBJETIVOS
- Convertir los 3 ciclos de vida a hooks.
- Buenas practicas para useEffect.
- Renderizado condicional.


## Hook de Efectos

El Hook de efecto te permite llevar a cabo efectos secundarios en componentes funcionales. Es decir nos permite simular el manejo de los ciclos de vida en componentes stateless.

En ciertas ocasiones, queremos ejecutar código adicional después de que React haya actualizado el DOM. Peticiones de red, mutaciones manuales del DOM y registros, son ejemplos comunes de efectos.

En los componentes de React con clases, el método render no debería causar efectos secundarios por sí mismo. Sería prematuro. Normalmente queremos llevar a cabo nuestros efectos después de que React haya actualizado el DOM. Y es por eso que en las clases de React ponemos los efectos secundarios en componentDidMount y componentDidUpdate.

Recordemos que los Hooks nos permiten simular comportamiento de componentes statefull en componentes funcionales, como se vio en la sesión pasada con el hook `useState`. El hook que se usa para tener efectos secundarios es `useEffect`.

### ¿Cómo funciona useEffect? 

- <b>¿Qué hace useEffect? </b> Al usar este Hook, le estamos indicando a React que el componente tiene que hacer algo después de renderizarse. React recordará la función que le hemos pasado (nos referiremos a ella como nuestro “efecto”), y la llamará más tarde después de actualizar el DOM. 

- <b>¿Por qué se llama a useEffect dentro del componente?</b> Poner useEffect dentro del componente nos permite acceder a las variables de estado, o a cualquier prop directamente desde el efecto. No necesitamos una API especial para acceder a ella, ya que se encuentra en el ámbito de la función. Los Hooks aprovechan los closures de JavaScript y evitan introducir APIs específicas de React donde JavaScript ya proporciona una solución.

- <b>¿Se ejecuta useEffect después de cada renderizado?</b> ¡Sí! Por defecto se ejecuta después del primer renderizado y después de cada actualización. Más tarde explicaremos cómo modificar este comportamiento. En vez de pensar en términos de “montar” y “actualizar”, puede resultarte más fácil pensar en efectos que ocurren “después del renderizado”. React se asegura de que el DOM se ha actualizado antes de llevar a cabo el efecto.

### ¿Cómo se usa useEffect? 

Consideremos el siguiente ejemplo, para entender mejor el funcionamiento de este Hook. 

````javascript
	function Example() {
	  const [count, setCount] = useState(0);

	  useEffect(() => {
	    document.title = `You clicked ${count} times`;
	  });
	}
```` 

En el código anterior se define un componente funcional y luego haciendo uso del hook de estado se crea una variable en el estado llamada `count`.

Declaramos la variable de estado `count` y le indicamos a React que necesitamos usar un efecto. Le pasamos una función al Hook `useEffect`. Esta función que pasamos es nuestro efecto. Dentro de nuestro efecto actualizamos el título del documento usando la API del navegador `document.title`. Podemos leer el valor más reciente de `count` dentro del efecto porque se encuentra en el ámbito de nuestra función. Cuando React renderiza nuestro componente, recordará este efecto y lo ejecutará después de actualizar el DOM. Esto sucede en cada renderizado, incluyendo el primero.

Ahora aprendamos como simular los ciclos de vida usando `useEffect`.

[`Ejemplo 01: Capitán Garfio`](Ejemplo-01/Readme.md)

[`Reto 01: Extraño la tarea`](Reto-01/Readme.md)

El uso de efectos es muy poderoso pero también puede llegar a afectar el desempeño de nuestra aplicación. Así que es recomendado usarlos solo en casos que sea estrictamente necesario.


## Reglas de los Hooks

Los Hooks son funciones de JavaScript, pero necesitas seguir dos reglas cuando los uses.

- <b>Llama Hooks solo en el nivel superior</b> No llames Hooks dentro de ciclos, condicionales o funciones anidadas. En vez de eso, usa siempre Hooks en el nivel superior de tu función en React. Siguiendo esta regla, te aseguras de que los hooks se llamen en el mismo orden cada vez que un componente se renderiza. Esto es lo que permite a React preservar correctamente el estado de los hooks entre multiples llamados a `useState` y `useEffect`.

- <b>Llama Hooks solo en funciones de React</b> No llames Hooks desde funciones JavaScript regulares. En vez de eso, puedes: Llama Hooks desde componentes funcionales de React o Llama Hooks desde Hooks personalizados. Siguiendo esta regla, te aseguras de que toda la lógica del estado de un componente sea claramente visible desde tu código fuente.

Existe un  plugin de linter para hacer cumplir estas reglas automáticamente, llamado `esLint`, si te interesa conocer mas de él puedes consultar el siguiente enlace hacía la [documentación oficial](https://www.npmjs.com/package/eslint-plugin-react-hooks).

Siguiendo estas reglas siempre tendrás la certeza de que tus componentes funcionan de la forma esperada.


## Renderizado condicional

En React, puedes crear distintos componentes que encapsulan el comportamiento que necesitas. Entonces, puedes renderizar solamente algunos de ellos, dependiendo del estado de tu aplicación.

El renderizado condicional en React funciona de la misma forma que lo hacen las condiciones en JavaScript. Usa operadores de JavaScript como if o el operador condicional para crear elementos representando el estado actual, y deja que React actualice la interfaz de usuario para emparejarlos. 

Existen 3 formas de lograr un renderizado condicional:

### Directa 

Puedes incluir expresiones en JSX envolviéndolas en llaves. Esto incluye el operador lógico && de JavaScript. Puede ser útil para incluir condicionalmente un elemento.

````javascript
{true && <h1> Hola Mundo!!</h1>}
````
Esto funciona porque en JavaScript, true && expresión siempre evalúa a expresión, y false && expresión siempre evalúa a false.

Por eso, si la condición es true, el elemento justo después de && aparecerá en el resultado. Si es false, React lo ignorará.

### Ternaria 

Otro método para el renderizado condicional de elementos en una línea es usar el operador ternario `condition ? true : false` de JavaScript.

En el siguiente ejemplo, lo usaremos para renderizar de forma condicional un pequeño bloque de texto.

````javascript
{condition ? 'currently' : 'not'}
````
### Por función

Este método consiste en definir una función que regrese el elemento a renderizar, y hacer que la lógica de la función genere este elemento dependiendo de los parámetros que reciba o del valor de algunas variables en el estado.

Puedes usar variables para almacenar elementos. Esto puede ayudarte para renderizar condicionalmente una parte del componente mientras el resto del resultado no cambia.

En casos excepcionales, es posible que desees que un componente se oculte a sí mismo aunque haya sido renderizado por otro componente. Para hacer esto, devuelve null en lugar del resultado de renderizado.



Ahora probemos estas tres formas de renderizado condicional. 

[`Ejemplo 02: Simulando llamadas condicionales`](Ejemplo-02/Readme.md)

[`Reto 02: ¿Niño o niña?`](Reto-02/Readme.md)

<!-- #### ORGANIZACION DE LA CLASE
- componentDidMount a hook.
- componentWillUnmount a hook.
- componentDidUpdate a hook.
- Buenas prácticas.
- 3 maneras de renderizado condicional. -->

### [Buenas prácticas para `useEffect`](../BuenasPracticas/useEffect/Readme.md).
