# Laboratorio No. 02 — Robótica Industrial
### Análisis y Operación del Manipulador Motoman MH6.
**Universidad Nacional de Colombia · Robótica 2026-I**

---

## Integrantes

| Nombre | URL del Repositorio |
|--------|-------------------|
| Julian Benitez | https://github.com/JulianI3 |
| Juan Salamanca | https://github.com/JuanSalan |

---

## Descripción de la Solución

En este laboratorio se trabajó en una breve caracterización de operación del robot manipulador Motoman MH6 programado mediante el software RoboDK. A partir de código desarrollado en lenguaje Python, se le ordenó al manipulador, tanto en el entorno virtual como físico, la ejecución de trayectorias correspondientes a la escritura de los nombres de los integrantes del equipo y al trazado de una figura en coordenadas polares. Adicionalmente, se estudiaron aspectos básicos de operación manual, configuraciones iniciales y control de movimiento del manipulador.

---
## Tabla comparativa de especificaciones entre robot manipulador Motoman MH6 y IRB 140

La siguiente tabla muestra las características técnicas de los 2 Robots manipuladores utilizados en los últimos laboratorios

| Característica | Motoman MH6 | IRB 140 |
|---|---|---|
| Carga útil | 6 kg | 6 kg |
| Alcance | 1422 mm | 800 mm |
| Número de grados de libertad | 6 | 6 |
| Peso | 130 kg | 98 kg |
| Repetibilidad | ±0,08 mm | ±0,08 mm |
| Velocidad eje S / A | 140 °/sec | 200 °/sec |
| Velocidad eje L / B | 130 °/sec | 200 °/sec |
| Velocidad eje U / C | 135 °/sec | 260 °/sec |
| Velocidad eje R / D | 270 °/sec | 360 °/sec |
| Velocidad eje B / E | 270 °/sec | 360 °/sec |
| Velocidad eje T / F | 400 °/sec | 450 °/sec |

<div align="center">

<table>
<tr>
<td align="center">
<img src="Diagramas/Imagenes/Ejes%20manipulador%20Motoman%20MH6.png"
     width="340"
     height="400">
<br>
<b>(a)</b> Notación de ejes para el manipulador Motoman MH6
</td>

<td align="center">
<img src="Diagramas/Imagenes/Ejes%20manipulador%20IRB%20140.png"
     width="320"
     height="400">
<br>
<b>(b)</b> Notación de ejes para el manipulador IRB 140
</td>

</tr>
</table>

</div>

---

## Descripción de las 2 posiciones de Home del manipulador Motoman MH6

La configuración Home 1 del Motoman MH6 corresponde a una postura “guardada” o recogida del manipulador, en la cual el brazo permanece agachado y compacto. Esta posición se utiliza normalmente al finalizar una rutina o cuando el robot se encuentra fuera de operación, ya que reduce el espacio ocupado y disminuye el riesgo de interferencias en el área de trabajo.

Por otro lado, la configuración Home 2 corresponde a una postura vertical, donde el manipulador queda elevado y con mayor libertad de movimiento. Esta posición se emplea antes de montar piezas o realizar tareas de manipulación, facilitando el desplazamiento manual y el acceso al espacio de trabajo del robot.


<div align="center">

<table>
<tr>
<td align="center">
<img src="Diagramas/Imagenes/Home1.png"
     width="340"
     height="400">
<br>
<b>(a)</b> Posición Home 1
</td>

<td align="center">
<img src="Diagramas/Imagenes/Home2.png"
     width="320"
     height="400">
<br>
<b>(b)</b> Posición Home 2
</td>

</tr>
</table>

</div>
