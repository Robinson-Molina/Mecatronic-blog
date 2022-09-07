---
layout: post
author: Robinson Molina
title: Apuntes Javascript
---
# Javascript

### Programacion
La programación es el acto de construir un programa—un conjunto de instrucciones precisas que le dicen a una computadora qué hacer. Porque las computadoras son bestias tontas y pedantes, la programación es fundamentalmente tediosa y frustrante.
### Valores, tipos y Operadores

#### Valores 
Para crear un valor, solo debemos de invocar su nombre. Esto es conveniente. No tenemos que recopilar materiales de construcción para nuestros valores, o pagar por ellos. Solo llamamos su nombre, y woosh
#### Numeros
Para una cantidad de N dígitos decimales, la cantidad de números que pueden ser representados es 10^n. Del mismo modo, dados 64 dígitos binarios, podemos representar 2^64 números diferentes, lo que es alrededor de 18 mil trillones (un 18 con 18 ceros más).
#### Números especiales

Existen 3 valores especiales en JavaScript que son considerados números pero que no se comportan como números normales.

Los primeros dos son Infinity y -Infinity, los cuales representan las infinidades positivas y negativas. Infinity - 1 aun es Infinity, y asi sucesivamente.

A pesar de esto, no confíes mucho en computaciones que dependan de infinidades. Estas no son matemáticamente confiables, y puede que muy rápidamente nos resulten en el próximo número especial: NaN.

NaN significa “no es un número” (“Not A Number”), aunque sea un valor del tipo numérico.


#### Strings
El próximo tipo de dato básico es el string. Los Strings son usados para representar texto. Son escritos encerrando su contenido en comillas:

>`Debajo en el mar`
>"Descansa en el océano"
>'Flota en el océano'

Los Newlines (los caracteres que obtienes cuando presionas la tecla de Enter) solo pueden ser incluidos cuando el string está encapsulado con comillas invertidas (\‘).

Para hacer posible incluir tales caracteres en un string, la siguiente notación es utilizada: cuando una barra invertida (\) es encontrada dentro de un texto entre comillas, indica que el carácter que le sigue tiene un significado especial.

Esto se conoce como escapar el carácter. Una comilla que es precedida por una barra invertida no representará el final del string sino que formara parte del mismo. Cuando el carácter n es precedido por una barra invertida, este se interpreta como un Newline (salto de linea). De la mima forma, t después de una barra invertida, se interpreta como un character de tabulación. 

Asi es como el string “Un carácter de salto de linea es escrito así: "\n".” puede ser expresado:

> Un carácter de salto de linea es escrito así: \"\\n\"."

Y eso es lo que hace JavaScript. Pero hay una complicación: La repre sentación de JavaScript usa 16 bits por cada elemento string, en el cual caben 2^16 números diferentes. Pero Unicode define mas caracteres que aquellos aproximadamente el doble, en este momento. 

Entonces algunos caracteres, como muchos emojis, necesitan ocupar dos “posiciones de caracteres” en losstrings de JavaScript.

Los strings no pueden ser divididos, multiplicados, o substraidos, pero el operador + puede ser utilizado en ellos. No los agrega, sino que los `concatena` pega dos strings juntos.

Los strings de comillas inversas, usualmente llamados
plantillas literales, pueden realizar algunos trucos más. Mas alla de permitir saltos de lineas, pueden también incrustar otros valores.
> `la mitad de 100 es ${100 / 2}`
Cuando escribes algo dentro de ${} en una plantilla literal, el resultado será computado, convertido a string, e incluido en esa posición. El ejemplo anterior produce “la mitad de 100 es 50”.

La forma en la que los strings son ordenados, es aproximadamente alfabético, aunque no realmente de la misma forma que esperaríamos ver en un diccionario: las letras mayúsculas son siempre “menores que” las letras minúsculas, así que "Z" < "a", y caracteres no alfabéticos (como !, - y demás) son también incluidos en el ordenamiento. Cuando comparamos strings, JavaScript evalúa los caracteres de izquierda a derecha, comparando los códigos Unicode uno por
uno.

#### Operadores unarios
No todo los operadores son simbolos. Algunos se escriben como palabras. Un ejemplo es el operador typeof, que produce un string con el nombre del tipo de valor que le demos.

```js
console.log(typeof 4.5)
// → number
console.log(typeof "x")
// → string
```

Los operadores que usan dos valores son llamados `operadores binarios`, mientras que aquellos operadores que usan uno son llamados `operadores unarios`. El operador menos puede ser usado tanto como un operador binario o como un operador unario.

Los signos > y < son tradicionalmente símbolos para “mayor que” y “menor que”, respectivamente. Ambos son operadores binarios.

#### Valores Booleanos
Es frecuentemente util tener un valor que distingue entre solo dos posibilidades, como “si”, y “no”, o “encendido” y “apagado”. Para este propósito, JavaScript tiene el tipo Boolean, que tiene solo dos valores: true (verdadero) y false (falso) que se escriben de la misma forma.

> operadores similares son >= (mayor o igual que), <= (menor o igual que), == (igual a), y != (no igual a).

>Solo hay un valor en JavaScript que no es igual a si mismo, y este es NaN (“no es un número”).
```js
console.log(NaN == NaN)
// → false
```

Se supone que NaN denota el resultado de una computación sin sentido, y como tal, no es igual al resultado de ninguna otra computación sin sentido.

#### Operadores Logicos 
El operador && representa el operador lógico and. Es un operador binario, y su resultado es verdadero solo si ambos de los valores dados son verdaderos.

```js
console.log(true && false)
// → false
console.log(true && true)
// → true
```

El operador || representa el operador lógico or. Lo que produce es verdadero si cualquiera de los valores dados es verdadero.

```js
console.log(false || true)
// → true
console.log(false || false)
// → false
```

Not se escribe como un signo de exclamación (!). Es un operador unario que voltea el valor dado—!true produce false y !false produce true.

operadores que hemos visto hasta ahora, || tiene la menor precedencia, luego le sigue &&, luego le siguen los operadores de comparación (>, ==, y demás), y luego el resto.

El ultimo operador lógico que discutiremos no es unario, tampoco binario,
sino ternario, esto es, que opera en tres valores. Es escrito con un signo de
interrogación y dos puntos.

```js
console.log(true ? 1 : 2);
// → 1
console.log(false ? 1 : 2);
// → 2
```

#### Valores vacíos
Existen dos valores especiales, escritos como `null y undefined`, que son usados para denotar la ausencia de un valor significativo. Son en si mismos valores, pero no traen consigo información.

Cuando un operador es aplicado al tipo de valor “incorrecto”, JavaScript silenciosamente convertirá ese valor al tipo que necesita, utilizando una serie de reglas que frecuentemente no dan el resultado que quisieras o esperarías. Esto es llamado `coercion de tipo`.

Este comportamiento es frecuentemente util. Cuando queremos probar si un valor tiene un valor real en vez de null o undefined, puedes compararlo con null usando el operador == (o !=).

#### Corto circuito de operadores lógicos
Esto tiene el efecto esperado cuando los valores son Booleanos, pero se comporta de una forma algo análoga con valores de otros tipos.

console.log(null || "usuario")
// → usuario
console.log("Agnes" || "usuario")
// → Agnes

### EStructura de programa
Un fragmento de código que produce un valor se llama una expresión. Cada valor que se escribe literalmente (como 22 o "psicoanálisis") es una expresión.

Si una expresión corresponde al fragmento de una oración, una declaración en JavaScript corresponde a una oración completa.

Un programa es una lista de declaraciones

El tipo más simple de declaración es una expresión con un punto y coma después ella. Esto es un programa:
>1;
>!false;

Para atrapar y mantener valores, JavaScript proporciona una cosa llamada vinculación, o variable

Vinculaciones

La palabra especial (palabra clave) `let` indica que esta oración va a definir una vinculación. Le sigue el nombre de la vinculación y, si queremos darle un valor inmediatamente, un operador = y una expresión.

```js
let diez = 10, dos=2;
console.log(diez * diez);
// → 100
```
`var` (abreviatura de “variable”), es la forma en la que se declaraban las vinculaciones en JavaScript previo al 2015.

`const` representa una constante. Define una vinculación constante, que apunta al mismo valor por el tiempo que viva.

```js
var nombre = "Ayda";
const saludo = "Hola ";
console.log(saludo + nombre);
// → Hola Ayda
```

#### Nombres de vinculaciones
Los nombres de las vinculaciones pueden ser cualquier palabra. Los dígitos pueden ser parte de los nombres de las vinculaciones pueden—catch22 es un nombre válido, por ejemplo—pero el nombre no debe comenzar con un dígito.
El nombre de una vinculación puede incluir signos de dólar ($) o caracteres de subrayado (_), pero no otros signos de puntuación o caracteres especiales

> La lista completa de palabras clave y palabras reservadas es bastante larga

La colección de vinculaciones y sus valores que existen en un momento dado se llama `entorno`. Cuando se inicia un programa, est entorno no está vacío. Siempre contiene vinculaciones que son parte del estándar del lenguaje

Una función es una pieza de programa envuelta en un valor.Dichos valores pueden ser aplicados para ejecutar el programa envuelto.

Ejecutar una función tambien se conoce como invocarla, llamarla, o aplicarla.

La ejecución condicional se crea con la palabra clave if en JavaScript. En el caso simple, queremos que se ejecute algún código si, y solo si, una cierta
condición se cumple.

``` Javascript
let elNumero = Number(prompt("Elige un numero"));
if (!Number.isNaN(elNumero)) {
console.log("Tu número es la raiz cuadrada de " +
elNumero * elNumero);
}
else {
console.log("Ey. Por qué no me diste un número?");
}

```
Necesitamos es una forma de ejecuta una pieza de código multiples veces. Esta forma de flujo de control es llamada un ciclo (o “loop”):

``` Javascript
let numero = 0;
while (numero <= 12) {
console.log(numero);
numero = numero + 2;
}
// → 0
// → 2
// … etcetera
```

### Funciones

``` Javascript
prompt("Introducir contraseña"); //crea una caja de dialogo
console.log("salida") //para dar salida a los valores.

console.log(Math.max(2, 4));
// devuelve el mayor de ellos.

Number("7") // convierte en una numero

Number.isNaN("4") // función estándar de JavaScript que retorna true solo si el argumento que se le da es NaN.
```

