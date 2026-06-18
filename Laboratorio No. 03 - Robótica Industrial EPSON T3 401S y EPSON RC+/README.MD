# Laboratorio No. 03 — Robótica Industrial
### Análisis y Operación del Manipulador EPSON T3-401S.
**Universidad Nacional de Colombia · Robótica 2026-I**

---

## Integrantes

| Nombre | URL del Repositorio |
|--------|-------------------|
| Julian Benitez | https://github.com/JulianI3 |
| Juan Salamanca | https://github.com/JuanSalan |

---

## Descripción de la Solución

En este laboratorio se trabajó con el simulador EPSON RC+ 7.0 para la programación y validación de tareas de manipulación utilizando el robot SCARA EPSON T3-401S. Mediante el desarrollo de un programa en lenguaje SPEL+, se implementó una estrategia de paletizado para el transporte de dos huevos en una cubeta, empleando un manipulador neumático como elemento de agarre. Para definir la secuencia de posiciones de depósito, se generó un pallet basado en el recorrido del caballo en ajedrez, garantizando que los huevos fueran ubicados en posiciones diferentes sin repetir casillas previamente ocupadas. La solución fue validada en el entorno de simulación, permitiendo verificar el correcto funcionamiento de las rutinas de pick-and-place.

---
## Tabla comparativa de especificaciones entre robot manipulador Motoman MH6 y IRB 140

La siguiente tabla muestra las características técnicas de los 2 Robots manipuladores utilizados en los últimos laboratorios
<table align="center">
  <tr>
    <th align="center">Característica</th>
    <th align="center">Motoman MH6</th>
    <th align="center">IRB 140</th>
  </tr>

  <tr>
    <td align="center">Fabricante</td>
    <td align="center">Yaskawa Motoman</td>
    <td align="center">ABB</td>
  </tr>

  <tr>
    <td align="center">Controlador</td>
    <td align="center">DX100</td>
    <td align="center">IRC5</td>
  </tr>

  <tr>
    <td align="center">Carga útil</td>
    <td align="center">6 kg</td>
    <td align="center">6 kg</td>
  </tr>

  <tr>
    <td align="center">Alcance</td>
    <td align="center">1422 mm</td>
    <td align="center">800 mm</td>
  </tr>

  <tr>
    <td align="center">Número de grados de libertad</td>
    <td align="center">6</td>
    <td align="center">6</td>
  </tr>

  <tr>
    <td align="center">Peso</td>
    <td align="center">130 kg</td>
    <td align="center">98 kg</td>
  </tr>

  <tr>
    <td align="center">Repetibilidad</td>
    <td align="center">±0,08 mm</td>
    <td align="center">±0,08 mm</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje S / A</td>
    <td align="center">140 °/sec</td>
    <td align="center">200 °/sec</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje L / B</td>
    <td align="center">130 °/sec</td>
    <td align="center">200 °/sec</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje U / C</td>
    <td align="center">135 °/sec</td>
    <td align="center">260 °/sec</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje R / D</td>
    <td align="center">270 °/sec</td>
    <td align="center">360 °/sec</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje B / E</td>
    <td align="center">270 °/sec</td>
    <td align="center">360 °/sec</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje T / F</td>
    <td align="center">400 °/sec</td>
    <td align="center">450 °/sec</td>
  </tr>

  <tr>
    <td align="center">Aplicaciones típicas</td>
    <td align="center">Soldadura por arco, corte y manipulación de materiales</td>
    <td align="center">Ensamblaje de precisión, pick and place y educación</td>
  </tr>
</table>
<div align="center">
