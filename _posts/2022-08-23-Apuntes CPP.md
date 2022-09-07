---
layout: post
author: Robinson Molina
title: Apuntes C++
---
# C++

#### Operadores de bits y lógicos
Operador |Significado
& |conjunción (Y) de bits
^ |(O) exclusivo de bits
| |(O) inclusivo de bits


#### Operador Significado
&& conjunción lógica (Y)
| | disyunción lógica (O)


#### Precedencia de operadores


Símbolo | Significado
:: | resolución de alcance
---|---
++ | incremento sufijo
-- | decremento sufijo
( ) | llamada a función
[ ] | elemento de tabla
-> | acceso a miembro desde un puntero
. | acceso a miembro
---|---
++ | incremento prefijo
-- | decremento prefijo
! | negación lógica
~ | complemento a uno
- | cambio de signo (operador unario)
+ | identidad (operador unario)
& | dirección
* | seguir un puntero
sizeof | tamaño en bytes
new | reserva de memoria
delete | liberación de memoria
(tipo) |conversión explícita de tipos

.*  | acceso a miembros de clase
->* | acceso a miembros de clase desde puntero
* | multiplicación
/ | división
% | resto de la división entera
+ | suma
- | resta 
<< | desplazamiento de bits a la izquierda
>> | desplazamiento de bits a la derecha
< | menor que
<= |menor o igual
> | mayor que
>= | mayor o igual
== | igual
!= | desigual
& | conjunción (Y) de bits
^ | O exclusivo de bits
| | O inclusivo de bits
&& | conjunción (Y) lógica
| | |disyunción (O) lógica
= | asignación simple
*=, /=, %=, +=, - =, <<=, >>=,&=, ^=, |= |asignaciones compuestas
?: | expresión condicional
trhow | Lanzamiento de excepción
,| separador de expresiones


### Entrada y Salida

Con `cout` Estamos enviando una cadena de caracteres (“Mensaje a la pantalla”) al dispositivo de salida estándar (la pantalla). Luego, el manipulador de flujo endl da el efecto de la secuencia de escape ‘\n’.

> cout<<"Mensaje de pantalla"<< endl;

`cin` es el flujo de entrada asociado al teclado, cout es el flujo de salida estándar asociado a la pantalla, y existe otro

> cin>>otroNumero;

`cerr`, que es el flujo de error estándar asociado a la pantalla.

Transformar salida `(tipo)(dato)`
A esto se le llama hacer un `cast`, y es muy común hacerlo cuando no queremos que
se pierdan determinadas propiedades en los resultados de las operaciones.

> cout<<(int)(3.141592+2)<< endl; // Transformar a entero

Otra de las herramientas para la especificación de formatos son los manipuladores de flujos, así como el manipulador de flujo `“endl”` da una secuencia de escape, los manipuladores `dec, oct y hex`, hacen que la variable a la que le anteceden sea presentada en formato decimal, octal o hexadecimal respectivamente.

```c++
#include <iostream.h>
int main(){
int numero=6;
int leido;
cout<<"numero es en octal: "<<oct<<numero<<endl;
cout<<"en hexadecimal: "<<hex<<numero<<endl;
cout<<"en decimal: "<<dec<<numero<<endl;
cout<<"ahora teclea un numero"<<endl;
cin>>hex>>leido;
cout<<"el leido vale: "<<hex<<leido<<endl;
cout<<"y en decimal: "<<dec<<leido<<endl;
cout<<"y en octal: "<<oct<<leido<<endl;
return 0;
}
```

> Imprimir en pantalla un número de tipo flotante, sólo aparecerán 6 números después del punto, y la
ultima cifra será redondeada en caso de pasar los 6 dígitos.

Cuando se quieren resultados más exactos, nos es muy útil la librería `iomanip.h` que contiene el manipulador setprecision() con el que podemos determinar la precisión con la que queremos que aparezcan esos datos en la pantalla.

`setw` que se encarga de hacer aparecer el texto alineado determinados espacios a la derecha, si el numero de espacios solicitados para su alineación es menor que el numero de caracteres que se imprimirán, no tendrá un efecto.

`setfill` se ocupa del carácter de relleno, el carácter por defecto es el espacio en
blanco, pero nosotros podemos especificar el que queramos.

```c++
#include <iostream.h>
#include <iomanip.h>
int main(){
cout<<setw(5)<<setfill('%')<<"hola"<<endl;
cout<<setw(5)<<89;
cout<<setw(8)<<"centavo"<<endl;
return 0;
}
```
get
getline
read
write
ignore
gcount

```c++
#include <iostream.h>
    int main(){
    char caracter,nombre[20], apellido[20];
    char seg_apellido[20];
    cout<<"Teclea tu nombre por favor"<<endl;
    cin.get(caracter);
    cin.get(nombre,20,' ');
    cin.get();
    cin.get(apellido,20,' ');
    cin.get();
    cin.get(seg_apellido,20);
    cout<<caracter<<"Tu letra inicial es:"<<caracter<<endl;
    cout<<"tu nombre es: "<<caracter<<nombre<<endl;
    cout<<"tu apellido paterno es: "<<apellido<<endl;
    cout<<"tu apellido materno es: "<<seg_apellido<<endl;
    cout<<"Escribe el nombre de tu empresa: "<<endl;
    cin.ignore();
    cin.getline(nombre,20);
    cout<<"el nombre de tu empresa: "<<nombre<<" tiene "
    <<cin.gcount()<<" caracteres"<<endl;
    cin.get();
    //espera que oprimas enter para terminar
    return 0;
}
```

### Estructuras de Control


#### if
Se trata de una estructura de selección. Es decir que si se cumple el condicional se ejecutarán varias instrucciones más. Podemos añadir un else a la sentencia if, de manera que controlamos las opciones en caso de que la condición resulte false.

> if(condicion){caso verdadero;} else{caso falso;}

```c++
    if((examen[0]=='s')&&(semestre[0]=='s')){
        cout<<"estas en la universidad"<<endl;
    }
    else{
        cout<<"no estas en la universidad"<<endl;
    }
```

#### ? :
Este se trata de un operador del tipo condicional al estilo if/else. Se utiliza para condicionales cortos (de una sola línea).

> condición ? acción a ejecutar en caso verdadero : acción a ejecutar en caso falso ;

```c++
#include <iostream.h>
int main(){
    int calificacion;
    cout<<"Cual fue tu calificacion del semestre?"<<endl;
    cin>>calificacion;
    cout<<(calificacion>=6 ? "pasaste" : "reprobaste");
    cin.ignore();
    cin.get();
    return 0;
}
```
#### Switch

La estructura de selección múltiple switch, cuando hay muchas opciones que pudiese tomar el usuario

switch (parámetro a evaluar o comparar){
    case a : //cuando el parámetro tiene un valor a
        Acciones a ejecutar;
    case b: //cuando el parámetro tiene un valor b
        Acciones a ejecutar
    caso por default;
}


```c++
#include <iostream.h>
int main(){
    int opcion;
    cout<<"Menu de opciones"<<endl;
    cout<<"1.­ Opcion 1"<<endl;
    cout<<"2.­ Opcion 2"<<endl;
    cout<<"3.­ Opcion 3"<<endl;
    cout<<"elige una opcion"<<endl;
    cin>>opcion;
    switch(opcion){
        case 1:
            cout<<"ejecucion 1"<<endl;
            break;
        case 2:
            cout<<"ejecucion 2"<<endl;
            break;
        case 3:
            cout<<"ejecucion 3"<<endl;
            break;
        default:
            cout<<"es una opcion no valida"<<endl;
            break;
    }
    cout<<"presiona enter para salir"<<endl;
    cin.ignore();
    cin.get();
    return 0;
}
```

#### while

La sentencia de control while se encarga de repetir un bloque de código mientras se cumpla una condición. El bloque de código se debe de encontrar entre llaves,
excepto si es una sola línea.

> while (condición) {acciones a ejecutar;}

```c++
#include <iostream.h>
int main(){
    int calificacion, suma=0, iteracion=1;
    float promedio;
    while(iteracion<=10){
        cout<<"teclea tu calificacion "<<iteracion<<endl;
        cin>>calificacion;
        suma+=calificacion;
        ++iteracion;
    }
    promedio=(float)suma/(iteracion­1);
    cout<<"el promedio de calificaciones es: " <<promedio<<endl;
    cin.ignore();
    cin.get();
    return 0;
}
```
#### do while
Cuando necesitamos que un ciclo se ejecute por lo menos una vez, es necesaria esta sentencia.

> do{ Acciones a ejecutar; } while(condicion);

```c++
#include <iostream.h>
int main(){
    int opcion;
    do{
        cout<<"elije una opcion de la lista"<<endl;
        cout<<"1.­opcion 1"<<endl;
        cout<<"2.­opcion 2"<<endl;
        cout<<"3.­opcion 3"<<endl;
        cin>>opcion;
    }while((opcion<1)||(opcion>3));
    cout<<"esta opcion si fue valida"<<endl;
    cin.ignore();
    cin.get();
    return 0;
}
```

#### for
El ciclo for es al que más se recurre cuando se requiere realizar operaciones secuenciales, en donde se conoce el número de iteraciones o la condición a
comprobar.


> for(asignación inicial ; condición ; instrucción ) { bloque de instrucciones; }
ó, si se trata de una instrucción muy corta podría ponerse:

> for(asignación inicial ; condicion ; instrucción1 , instrucción 2)
```c++
#include <iostream.h>
#include <math.h> // libreia de matematica
int main (){
    int t;
    float x=0,y=0,ang,vi, grav=9.81;
    cout<<"cual es el angulo de lanzamiento?"<<endl;
    cin>>ang;
    cout<<"cual es la velocidad inicial?"<<endl;
    cin>>vi;
    ang=((ang*3.141592)/180); //necesario convertir a radianes
    for(t=0;t<=10;t++){
        x=(vi*cos(ang)*t);
        y=(vi*sin(ang)*t)­(0.5*grav*t*t);
        
        cout<<"t= "<<t<<" x= "<<x<<" y= "<<y<<endl;
    }
    cout<<"fin del programa"<<endl;
    cin.ignore();
    cin.get();
    return (0);
}
```

### Funciones

Cuando tratamos de resolver un problema, resulta muy útil utilizar la filosofía de “divide y vencerás”. Esta estrategia consiste en dividir nuestro problema en otros más sencillos.

#### PROTOTIPOS
El prototipo de una función se refiere a la información contenida en la declaración de una función. Una función debe de estar definida o al menos declarada antes de hacer uso de ella.

Cuando se declara una función debe de especificarse el tipo de dato que va a devolver, el nombre de la función, y los parámetros.

> int suma(int a, int b);
> int main ( int argc, char *argv[], char *envp[]);


#### PASO DE ARGUMENTOS
Cuando hablamos de argumentos, nos referimos a los valores que aparecen en la llamada a la función.

> suma(dato1, dato2)

>> Notemos que el prototipo de la función pueden los nombres de los parámetros distintos a los de la prototipo, esto no afectará el comportamiento del programa, pero se vería mejor si fueran iguales. Lo que no puede cambiar es el tipo de datos que va a recibir.

#### VALORES DE RETORNO
Una función puede regresar cualquier tipo de valor excepto tablas u otras funciones.

#### MACROS
Una macro es una parte del código que puede parecer y actuar como una función, se define después de las librerías mediante un #define.

Se denominan instrucciones de preproceso, porque se ejecutan al comienzo de la compilación.

Sin embargo, no hay que abusar de ellas, porque podrían entorpecer el código y hacer lento el programa.

```c++
#include <iostream.h>
#define mayor(a,b) (a>b)? a: b //Macros

int main(){
    int a,b;
    cout<<"teclea 2 numeros distintos"<<endl;
    cin>>a;
    cin>>b;
    cout<<"el mayor de esos numeros es: " <<(mayor(a,b))<<endl;
    cin.ignore();
    cin.get();
    return 0;
}
```

>> Debemos tener cuidado si vamos a usar macros, las macros, al compilar el programa, se sustituyen directamente en donde se invocan, es decir, que en este ejemplo, es como si se introdujera directamente los condicionales dentro del cout.

//    #define curva(a) 1+2*a+a*a
si en nuestro código colocamos una instrucción
//    curva(1+3)
se sustituye por
//    1+2*1+3+1+3*1+3

>> En el lenguaje C, se acostumbra usar macros para definir constantes (porque a diferencia de C++, ahí no existe el tipo const.
> #define PI 3.141592

#### RECURSIVIDAD
La recursividad se presenta cuando una función se invoca a si misma. Distintamente a las iteraciones (bucles), las funciones recursivas consumen muchos recursos de memoria y tiempo.

```c++
#include <iostream.h>
long factorial(long numero); //prototipo
int main(){
    long numero;
    cout<<"número para calcular el factorial:"<<endl;
    cin>>numero;
    cout<<"el factorial es: "<<factorial(numero)<<endl;
    cin.ignore();
    cin.get();
    return 0;
}
// Funcion
long factorial(long numero){
    if(numero<=1)
    return 1;
    else
    return numero*factorial(numero­1);
}
```

>> La recursividad es un tema importante en el mundo de la programación, la utilidad de este tipo de funciones se aprovecha en el diseño de algoritmos de criptografía, de búsqueda, entre otros.

### Arrays

Cuando declaramos una variable estamos apartando en memoria espacio para guardar sus posibles valores dependiendo del tipo de dato que se trata. Un array o arreglo son una serie de localidades en memoria consecutivas que están asignadas a un solo nombre y un mismo tipo de datos.

|-- |Valor almacenado | Localidad en memoria
|Arreglo[0] | 60 | FFFB
|Arreglo[1] | 1550 | FFFC
|Arreglo[2] | 130 | FFFD
|Arreglo[3] | 45 | FFFE
|Arreglo[4] | 90 | FFFF


#### DECLARACIÓN
La forma de declarar un arreglo de cualquier tipo de datos es la siguiente:

> tipo nombre [tamaño] ;

#### ASIGNACIÓN DE VALORES
Al momento de declarar un arreglo de cualquier tipo, podemos inicializarlo con los valores que queramos. Para inicializar un arreglo de enteros:
> int MiArreglo[5] ={2,34,78,1,9};

``` C++
#include <iostream.h>
#include <iomanip.h> //para presentacion con formato
#include <stdlib.h>
#include <time.h>
int main(){
    const int tam_max=20;
    int aleatorios[tam_max];
    int i,suma=0;
    float promedio;
    srand((unsigned)time(NULL));
    for(i=0;i<tam_max;i++){
        aleatorios[i]=rand()%128;  // rand() genera numero aleatorio
        //asigna el numero
        cout<<"aleatorio generado: "
        //presenta el numero
        <<setw(5)<<aleatorios[i]<<endl;
    }
    for(i=0;i<tam_max;){
        suma+=aleatorios[i++]; //suma los elementos
    }
    
    promedio=(float)suma/tam_max;
    cout<<endl<<"el promedio es: "<<promedio<<endl;
    cin.get();
    return 0;
}
```

#### Paso de arreglo a funcion  
En el caso del paso de arreglos, este no se hace por valor, sino que se hace un paso por referencia simulado. Cuando se declara un arreglo, el nombre de éste es una variable que apunta al primer elemento del arreglo, es decir que contiene su dirección en memoria

> tipoRetorno MiFuncion (tipoArreglo nombre [ ] );

>> Cuando pasamos esta dirección a una función, cualquier modificación que se haga dentro de esa función de nuestro arreglo tendrá efectos en la variable original.

En ocasiones puede resultar poco conveniente que alguna de las funciones que
reciben un arreglo tenga derecho a modificarlo. Para eso podemos incluir el calificador `const` dentro del prototipo y definición de la función, de esta manera no podrá modificarse nada de este arreglo.

> tipoRetorno nombreFuncion (const tipoArreglo nombre [ ] );

#### ARREGLOS MULTIDIMENSIONALES
	
Como sabemos, se pueden crear arreglos de cualquier tipo de datos, también se pueden crear arreglos de arreglos. La forma de declararlos es con múltiples subíndices, cuantos se quieran tener, nosotros trabajaremos a lo más con dobles subíndices.

> tipoArreglo nombre [subíndice1] [subíndice2] ;
> Array1 [2] [3] = {1, 2, 3, 4, 5, 6};
> Array2 [2] [3] = {{2, 4, 6}, {8, 10, 12}};

