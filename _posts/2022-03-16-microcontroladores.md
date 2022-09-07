---
layout: post
author: Robinson Molina
title: Microcontroladores
---

Resumen de los temas tratados en la asignatura de Microcontroladores


![Microcontrolador](Web/mecatronics/imagen/micro.jpg)

## Componentes electrónicos
### Tipos de señales
La importancia de los circuitos radica en que conforme una asociacion de componetes se puede realizar un tratamiento de las señales eléctricas para almacenar informacion
- Circuitos Analogicos: La señal varian en forma continua
- Circuitos Digitales: la señal obtiene valores discretos pueden ser numeros enteros o valores booleanos
- Circuitos mixtos: contiene elementos analigicos y también digitales.

### Componentes activos
Pueden controlar el flujo de corriente o lograr ganancias.
COmponentes activos 
- Amplificadores Operacionales
- Diodos Zener
- Memoria
- Pila
- Puertas lógicas
- Triac

### Componentes pasivos
- Inductores
- Condensadores
- Resistor

## Microcontroladores
Son circuitos integrados programables que ejecuta sentencias y tareas que han sido grabadas en la memoria. pequeños contruidos generalmente el silicio, encapsulador en planstico o ceramica para su protección
###Partes Funcionales de Microcontrilasdor
- Unidad Central de Procesamiento
- Memoria
- Perifericos de entrada

> Un **MCU** (un microcontrolador) no es igual a **MPU** (Microprocesador)

Un MCU utiliza una memoria **flash** para almacenar y ejecutar un programa, de esta manera permite un arranque breve y ejecuciones mas rapidas, la limitacion es la memoria reducida

Un MPU no tiene restricion  de memoria, pues usa memoria externas para almacenar datos. En general se guarda en un memoria no volatil(NAND o Flash en serie), pero el arranque se carga en la **DRAM** 
 
 Por una parte, los MPU suelen diseñarse teniendo en cuenta la arquitectura **Von Neumann**
 Mientras, lo MCU incorporan la memoria en su interior para hacer  uso preferete de la arquitectura **Harvard**

## Algunos MCU
- Intel 4004
- intel 8008
- Z80
- 6502
- PIC
- PICAXE

## PLACA DE ARDUINO
En la placa encontramos un **Atmel AVR**, puertos analogicos, puertos digitales y un puerto USB en arduino uno (tipo A/B) 


# **Imagen de puertos**

Diversas categorias y presentaciones

- Placas
- Placas de Expasión o Shields
- Kits
- Categoria de Impresion 3D (Arduino Materia)

### Caracteristicas

Modelo | Microcontrolador |Entradas/Salidas Digitales | Entradas/Salidas Analogicas |Memoria Flash  
--------------------| --------------------- | --------------------- | --------------------- | -------------------
Arduino Leonardo             | ATmega32U4 |20     |12 |32 kb
Arduino Uno R3               | ATmega328  |14     |6  |32 kb
Arduino Mega2560 R3          | ATmega2560 |54     |16 |256 kb
Arduino Megapro 3.3v         | ATmega2560 |54     |16 |256 kb
Arduino mini 05              | ATmega328  |14     |6  |32 kb
Arduino Fio                  | ATmega328P |14     |8  |32 kb
Arduino Megapro mini 3.3v    | ATmega2560 |54     |16 |56 kb
Arduino DUE                  | AT91SAM    |54     |12 |512 kb

##Arduino UNO
> Microcontolador: ATmega328
> Voltaje: 5V
> Voltaje de entrada recomendado: entre 7V y 12V
> Limite de voltaje de entrada: entre 6V y 20 V
> Pines digitales I/O: 14 , 6 de ellos son salida PWM 
> Entragas analogicas: 6
> Memoria Flash: 32 kb, de ellos 0.5 kb son usados para el arranque
> SRAM: 2 kb
> EEPROM: 1 kb
> Velocidad de reloj: 16 MHz
> Pines analógicos soportan conversión analógica-digital de **10 bits**
> Permite comunicacion **I2C** gracias a libreria Wire
> Serial: 0 **RX** (recibir) y 1 **TX** (Transmitir)
> SPI: terminales que soporta comunicacion **SPI (interfaz serial periférica**


## Pulsadores 
### (*Pull up/ pull down*)
``` csharp
int leds[]={5,6,7,8,9,10,11};
int n=0;
int tiempo=30;

void setup() { //comienza la configuración
  for (n=0;n<7;n++) {
    pinMode(leds[n],OUTPUT);
  }
}
void loop() {
  for (n=0;n<7;n++) {
    digitalWrite (leds[n],HIGH);
    delay(tiempo);
    digitalWrite(leds[n+1],HIGH);
    delay(tiempo);
    digitalWrite (leds[n],LOW);
    delay(tiempo*2);
  }
  for (n=6;n>=0;n--) {
    digitalWrite (leds[n],HIGH);
    delay(tiempo);
    digitalWrite(leds[n-1],HIGH);
    delay(tiempo);
    digitalWrite (leds[n],LOW);
    delay(tiempo*2);
  }
}
```
## Teclado
### (*hexadecimal*)

## Potenciómetro 
### (*ADC/resolucion/map*)

## Sensores 
### (*limites de tensíon admitidos*)

## Modos de alimentación Arduino

## Digitles

## PWM 
### (*resolución/frecuencia/modificación*)

## Conexión driver *L298*

## Valores máximos de corriente 
### (*entrada/salida de Arduino*)

## Acoples 
### (*Transistores, reles,Optoacopladores (PC817)/(MOC3021)*)

## LCD 
### (*configuraciones: conexión (pines), envio/recibo, comandos de programación, desplazamientos, limpiar, mover cursor, crear caracteres*)

Alimentación (**+,-,VEE**)

Configuración (**RS,R/W,E**)

> E=0, E=1
>
> R/W=0 **escritura**, R/W=1 **lectura**
>
> RS=0 **datos**, RS=1 **instrucciones**
>
> Datos (D0 ... D8)


## Comunicación serial

## Tipos de variables

# **Maquinas de Estado**

