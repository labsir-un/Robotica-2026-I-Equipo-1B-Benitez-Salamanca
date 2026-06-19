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

La siguiente tabla muestra las características técnicas de los 3 Robots manipuladores utilizados en los últimos laboratorios
<table align="center">
  <tr>
    <th align="center">Característica</th>
    <th align="center">Motoman MH6</th>
    <th align="center">IRB 140</th>
    <th align="center">EPSON T3-401S</th>
  </tr>

  <tr>
    <td align="center">Fabricante</td>
    <td align="center">Yaskawa Motoman</td>
    <td align="center">ABB</td>
    <td align="center">EPSON</td>
  </tr>

  <tr>
    <td align="center">Controlador</td>
    <td align="center">DX100</td>
    <td align="center">IRC5</td>
    <td align="center">Controlador integrado T3 (EPSON RC+ 7.0)</td>
  </tr>

  <tr>
    <td align="center">Carga útil</td>
    <td align="center">6 kg</td>
    <td align="center">6 kg</td>
    <td align="center">3 kg</td>
  </tr>

  <tr>
    <td align="center">Alcance</td>
    <td align="center">1422 mm</td>
    <td align="center">800 mm</td>
    <td align="center">400 mm</td>
  </tr>

  <tr>
    <td align="center">Número de grados de libertad</td>
    <td align="center">6</td>
    <td align="center">6</td>
    <td align="center">4</td>
  </tr>

  <tr>
    <td align="center">Peso</td>
    <td align="center">130 kg</td>
    <td align="center">98 kg</td>
    <td align="center">16 kg</td>
  </tr>

  <tr>
    <td align="center">Repetibilidad</td>
    <td align="center">±0,08 mm</td>
    <td align="center">±0,08 mm</td>
    <td align="center">±0,02 mm</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje S / A / 1</td>
    <td align="center">140 °/s</td>
    <td align="center">200 °/s</td>
    <td align="center">3,7 m/s</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje L / B / 2</td>
    <td align="center">130 °/s</td>
    <td align="center">200 °/s</td>
    <td align="center">3,7 m/s</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje U / C / 3</td>
    <td align="center">135 °/s</td>
    <td align="center">260 °/s</td>
    <td align="center">1,0 m/s</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje R / D / 4</td>
    <td align="center">270 °/s</td>
    <td align="center">360 °/s</td>
    <td align="center">260 °/s</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje B / E / 5</td>
    <td align="center">270 °/s</td>
    <td align="center">360 °/s</td>
    <td align="center">N.A.</td>
  </tr>

  <tr>
    <td align="center">Velocidad eje T / F / 6</td>
    <td align="center">400 °/s</td>
    <td align="center">450 °/s</td>
    <td align="center">N.A.</td>
  </tr>

  <tr>
    <td align="center">Aplicaciones típicas</td>
    <td align="center">Soldadura por arco, corte y manipulación de materiales</td>
    <td align="center">Ensamblaje de precisión, pick and place y educación</td>
    <td align="center">Pick and place, ensamblaje, clasificación, manipulación de pequeñas piezas y automatización de laboratorio</td>
  </tr>
</table>
<div align="center">
