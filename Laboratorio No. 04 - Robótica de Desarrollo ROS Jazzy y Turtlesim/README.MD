# Laboratorio No. 04 — Robótica de Desarrollo
###  Intro a ROS2 Jazzy Jalisco - Turtlesim.
**Universidad Nacional de Colombia · Robótica 2026-I**

---

## Integrantes

| Nombre | URL del Repositorio |
|--------|-------------------|
| Julian Benitez | https://github.com/JulianI3 |
| Juan Salamanca | https://github.com/JuanSalan |

---

## Descripción de la Solución

En este laboratorio se desarrolla un sistema de control para el simulador turtlesim utilizando ROS 2 Jazzy Jalisco y el lenguaje de programación Python. El objetivo principal es aplicar los conceptos básicos de comunicación mediante nodos, tópicos y servicios para controlar el movimiento de una tortuga tanto de forma manual como automática.

Inicialmente se implementa el control de velocidad lineal y angular mediante el teclado, permitiendo el desplazamiento de la tortuga en distintas direcciones. Posteriormente, se incorporan funciones modulares para ejecutar trayectorias automáticas, dibujar figuras geométricas y representar las iniciales de los integrantes del grupo. Adicionalmente, se implementan acciones complementarias como el reinicio de la simulación, la activación o desactivación del lápiz de dibujo y la detención del movimiento.

Finalmente, se desarrolla un sistema líder-seguidor conformado por dos tortugas, en el cual una segunda tortuga sigue automáticamente la trayectoria de la primera mediante el intercambio de información a través de tópicos de ROS 2 y el cálculo de la posición y orientación relativas entre ambas.

---

## Explicación del control manual de la tortuga


## Explicación de las funciones automáticas implementadas
El nodo incorpora un conjunto de funciones automáticas que permiten ejecutar movimientos predefinidos y acciones complementarias sin necesidad de controlar continuamente la tortuga mediante el teclado. Cada función fue implementada de manera modular para facilitar su mantenimiento y reutilización.

### mover(linear, angular, tiempo)

Esta función constituye la base de todas las trayectorias automáticas. Recibe como parámetros la velocidad lineal, la velocidad angular y el tiempo durante el cual deben mantenerse dichas velocidades. Durante el intervalo especificado actualiza continuamente las variables de control que posteriormente son publicadas por el temporizador en el tópico /turtle1/cmd_vel. Al finalizar el tiempo de ejecución, la función detiene completamente la tortuga.

### orientar(angulo_objetivo)

Permite orientar la tortuga hacia un ángulo absoluto específico utilizando la orientación medida por el tópico /turtle1/pose. En lugar de girar durante un tiempo fijo, calcula continuamente el error angular entre la orientación actual y la deseada, ajustando la velocidad angular de forma proporcional hasta que el error sea suficientemente pequeño. Esto proporciona una orientación considerablemente más precisa para el dibujo de figuras.

### dibujar_cuadrado()

Genera automáticamente un cuadrado mediante cuatro desplazamientos rectilíneos de igual longitud. Después de completar cada lado, la orientación de la tortuga se corrige utilizando la función orientar(), realizando un giro absoluto de 90° respecto a la orientación inicial del dibujo.

<div align="center">
    <img src="Diagramas-Imagenes/Square.png" width="300">
</div>

### dibujar_triangulo()

Implementa el dibujo de un triángulo equilátero. La función realiza tres desplazamientos rectos de igual longitud y, al finalizar cada lado, utiliza orientar() para establecer la siguiente orientación, separada 120° de la anterior. 

<div align="center">
    <img src="Diagramas-Imagenes/Triangule.png" width="300">
</div>

### reiniciar()

Realiza una llamada al servicio /reset de turtlesim, restaurando la simulación a su estado inicial. Como resultado, la tortuga vuelve a la posición central con orientación inicial y se elimina cualquier trazo previamente dibujado.

### cambiar_lapiz()

Permite activar o desactivar el lápiz de dibujo mediante el servicio /turtle1/set_pen. La función conserva internamente el estado del lápiz (pen_on) para alternar entre ambas condiciones cada vez que el usuario presiona la tecla correspondiente. 

### detener()

Detiene inmediatamente cualquier trayectoria automática en ejecución. Para ello desactiva el modo automático, establece en cero las velocidades lineal y angular e indica a las funciones de movimiento que finalicen su ejecución mediante la variable stop_requested.

### trayectoria_automatica()

Activa un modo de navegación autónoma en el que la tortuga avanza continuamente por el escenario. Cuando detecta que se aproxima a alguno de los límites de la ventana de turtlesim, modifica automáticamente su velocidad angular para cambiar de dirección y evitar salir del área de trabajo. Este comportamiento se ejecuta de manera continua dentro de la función move_turtle().

<div align="center">
    <img src="Diagramas-Imagenes/Automatic_movement.png" width="300">
</div>

move_turtle()

Corresponde a la función ejecutada periódicamente por el temporizador del nodo. Su responsabilidad es construir y publicar el mensaje Twist con las velocidades lineal y angular actuales hacia el tópico /turtle1/cmd_vel. Cuando el modo automático está habilitado, también calcula los cambios de dirección necesarios para evitar que la tortuga alcance los límites del entorno de simulación. De esta manera, actúa como el lazo principal de control encargado de enviar continuamente los comandos de movimiento a la tortuga.
---

## Explicación del dibujo de letras personalizadas

---

## Explicación del sistema líder-seguidor con dos tortugas

---

## Descripción de los nodos, tópicos y servicios utilizados
