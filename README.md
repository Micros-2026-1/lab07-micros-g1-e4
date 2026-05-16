[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/rb0M7Pn8)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23812035&assignment_repo_type=AssignmentRepo)
# Lab07: Visualización en LCD 16x2 usando módulo I²C con microcontrolador PIC

## Integrantes
* [Joused Danilo Forero Rodriguez](https://github.com/jouseddanilo)
* [Laura Ximena Rojas Pachon](https://github.com/LauXRS)
## INTRODUCCIÓN
La práctica se centra en la configuración y uso del módulo I²C (Inter-Integrated Circuit) en el microcontrolador PIC18F45K22 para controlar una pantalla LCD 16x2 mediante un adaptador PCF8574. El objetivo es enviar datos y comandos a la pantalla LCD a través del protocolo I²C, lo que simplifica la conexión y reduce la cantidad de pines necesarios.

## OBJETIVOS 
* Configurar el módulo I²C (MSSP) del PIC18F45K22 en modo maestro.
* Comunicar el PIC con una LCD 16x2 utilizando el adaptador basado en PCF8574.
* Implementar funciones para enviar comandos y caracteres vía I²C.
* Mostrar mensajes en la pantalla LCD desde el programa principal.

## MATERIALES
* Microcontrolador: PIC18F45K22 o compatible.
* Programador/Debugger: PICkit 3/4.
* Fuente de alimentación (o PICkit 3/4).
* Pantalla LCD 16x2.
* Módulo I²C PCF8574.
* Entorno de programación: MPLAB X IDE con compilador XC8.
Documentación

## FUNDAMENTO TEÓRICO
El protocolo I²C es un sistema de comunicación serial que utiliza dos líneas: SDA (Serial Data Line) y SCL (Serial Clock Line). Este protocolo permite la conexión de múltiples dispositivos esclavos en el mismo bus de comunicación, facilitando la interacción entre ellos.

### Ventajas de uso de I²C
* Reducción de pines: Sin I²C, la LCD requiere de 6 a 8 pines del microcontrolador. Con I²C, solo se necesitan 2 pines (SDA y SCL).
* Comunicación half-duplex: Solo un dispositivo puede enviar datos a la vez, lo que simplifica la gestión de la comunicación.

El módulo MSSP del PIC18F45K22 permite operar en modo I²C, utilizando buffers y registros de control para gestionar la comunicación. La dirección del módulo PCF8574 es 0x27, pero para la transmisión en el bus I²C se utiliza 0x4E.

## PROCEDIMIENTO 
### Montaje del Circuito
Realizar el montaje del circuito según el esquema proporcionado, conectando el módulo I²C a la LCD y al microcontrolador.


https://github.com/user-attachments/assets/3c5cceda-314a-4f67-9e76-356b493beb1a

## Evidencias de implementación


https://github.com/user-attachments/assets/1eb57cb4-06fc-47ed-881b-4d59540ba528


## Preguntas

1. ¿Por qué I²C se clasifica como half-duplex mientras que SPI es full-duplex? ¿Qué implicación práctica tiene esa diferencia para el control de una LCD?.
2. En I2C_init() se asigna SSPCON1 = 0x28. Desglose ese valor bit a bit e identifique qué modo de operación del MSSP se está seleccionando y por qué se elige ese valor.
3. Las funciones I2C_start(), I2C_stop() e I2C_write() comparten el mismo patrón: activar un bit de control y luego esperar con while(!PIR1bits.SSPIF). ¿Qué representa la bandera SSPIF y por qué se limpia después de cada operación?.
4. El fuse PBADEN = OFF está presente en la configuración. ¿Qué efecto tendría dejarlo en ON sobre los pines del puerto B, y por qué podría causar problemas si se usan esos pines como salidas digitales?.
5. Compare el control de la LCD en modo paralelo (lab04) con el modo I²C de este laboratorio. Mencione ventajas y desventajas de cada enfoque en términos de: cantidad de pines usados, velocidad de actualización y complejidad del código.
6. El bus I²C permite conectar múltiples esclavos con solo dos hilos. Si se quisiera agregar un segundo módulo PCF8574 al mismo bus (por ejemplo, para controlar un segundo LCD), ¿qué cambio mínimo sería necesario en el hardware y en el código?

## Conclusiones

## Referencias
