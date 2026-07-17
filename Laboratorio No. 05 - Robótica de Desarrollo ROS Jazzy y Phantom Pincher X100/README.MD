# Laboratorio No. 05 — Robótica de Desarrollo
###  Phantom X Pincher X100 – ROS 2 Jazzy – RViz.
**Universidad Nacional de Colombia · Robótica 2026-I**

---

## Integrantes

| Nombre | URL del Repositorio |
|--------|-------------------|
| Julian Benitez | https://github.com/JulianI3 |
| Juan Salamanca | https://github.com/JuanSalan |

---

## Actividades
### Actividad 2 Identificación de motores y articulaciones

| Articulación | ID DYNAMIXEL | Referencia | Sentido positivo | Función |
|--------------|--------------|------------|------------------|---------|
| Base (Waist) | N.A. | 0 rad | Giro antihorario del robot respecto al eje vertical, visto desde arriba. | Rotar toda la cadena cinemática alrededor de la base. |
| Hombro (Shoulder) | N.A. | 0 rad  | La rotación positiva del hombro hace descender el primer eslabón, desplazando toda la cadena cinemática. | Posicionar el primer eslabón y modificar la posición de toda la cadena cinemática. |
| Codo (Elbow) | N.A. | -π rad | La rotación positiva del codo hace descender la cadena cinemática a partir del segundo eslabón. | Modificar la configuración del segundo eslabón y del efector final sin afectar el primer eslabón. |
| Muñeca (Wrist) | N.A. | 0 rad | La rotación positiva de la muñeca hace descender la pinza. | Orientar el efector final mediante la rotación de la muñeca. |
| Pinza (Gripper) | N.A. | Gripper cerrado | La rotación positiva produce la apertura de la pinza. | Sujetar y liberar objetos mediante la apertura y cierre de las mordazas. |


Nota: La columna ID DYNAMIXEL se omitió debido a que no se contaba con el modelo físico que nos permitía conocer esta característica.



Se pueden centrar estas tablas?
### Actividad 3. Medición del robot

Las dimensiones del robot fueron obtenidas a partir de la medición de los archivos STL del modelo tridimensional disponible en el repositorio.  Las dimensiones estructurales se obtienen a partir de la altura de la base y la distancia entre articulaciones para las demás medidas solicitadas.

#### Dimensiones estructurales

| Parámetro | Valor (mm) |
|:----------|-----------:|
| Altura de la base | 48 |
| Distancia Base – Hombro | 44,5 |
| Distancia Hombro – Codo | 105,7 |
| Distancia Codo – Muñeca | 100,0 |
| Distancia Muñeca – TCP | 113,6 |

Luego la longitud de los eslabones se mide como el alto o largo de cada eslabón y no como la distancia entre articulaciones.

#### Longitud de los eslabones

| Eslabón | Longitud (mm) |
|:---------|--------------:|
| Eslabón 1 | 157,0 |
| Eslabón 2 | 114,2 |
| Eslabón 3 | 66,0 |

#### Dimensiones de la pinza

| Parámetro | Valor (mm) |
|:----------|-----------:|
| Longitud útil | 38,15 |
| Ancho útil | 29,0 |

El esquema que permite conocer con mayor facilidad las distancias entre juntas, orientación y tipo de juntas se muestra a continuación.

<p align="center">
  <img src="Diagramas-Imágenes/Esquema.png" alt="Esquema del robot" width="550"><br>
  <em>Figura 1. Esquema del robot PhantomX100.</em>
</p>
<h3>Actividad 4. Determinación de límites seguros</h3>
para realizar esta actividad se creo un script el cual funciona como un menú donde por consola se escoge la articualción que se va a mover, luego de esto se le da el angulo que se quiere mover en radianes, esto se puede ver en el sigueinte video:

<h3>Actividad 6. Determinación de límites seguros</h3>

<p>
Los siguientes límites fueron determinados experimentalmente a partir de la simulación en RViz.
Los valores corresponden a aproximaciones visuales obtenidas considerando el mejor caso, es decir,
evaluando cada articulación de manera independiente y sin interferencias ocasionadas por la
configuración instantánea de las demás articulaciones. Para garantizar una operación segura, el
programa debe impedir el envío de comandos fuera de estos rangos.
</p>

<table>
  <thead>
    <tr>
      <th align="center">Articulación</th>
      <th align="center">Límite inferior (rad)</th>
      <th align="center">Límite superior (rad)</th>
      <th align="center">Margen de seguridad</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">Base</td>
      <td align="center">-2,618</td>
      <td align="center">2,618</td>
      <td align="center">0,10 rad</td>
    </tr>
    <tr>
      <td align="center">Hombro</td>
      <td align="center">-2,00</td>
      <td align="center">2,00</td>
      <td align="center">0,10 rad</td>
    </tr>
    <tr>
      <td align="center">Codo</td>
      <td align="center">-2,15</td>
      <td align="center">1,571 </td>
      <td align="center">0,10 rad</td>
    </tr>
    <tr>
      <td align="center">Muñeca</td>
      <td align="center">-2,00</td>
      <td align="center">2,30</td>
      <td align="center">0,10 rad</td>
    </tr>
    <tr>
      <td align="center">Pinza</td>
      <td align="center">-1,571 </td>
      <td align="center">1,571 </td>
      <td align="center">0,10 rad</td>
    </tr>
  </tbody>
</table>

### Actividad 7. Movimiento simultáneo

Se implementó el desplazamiento simultáneo de las cinco articulaciones del robot mediante el envío de comandos articulares en el tópico `/pincher/command`. Cada configuración fue ejecutada de forma secuencial y validada en la simulación de RViz. Los valores corresponden a ángulos articulares expresados en grados para las articulaciones Base, Hombro, Codo, Muñeca y Pinza, respectivamente.

#### Configuración 1
**Coordenadas:** `(0°, 0°, 0°, 0°, 0°)`

<p align="center">
  <img src="Diagramas-Imágenes/Actividad_7_E1.gif" width="700">
</p>

---

#### Configuración 2
**Coordenadas:** `(25°, 25°, 20°, -20°, 0°)`

<p align="center">
  <img src="Diagramas-Imágenes/Actividad_7_E2.gif" width="700">
</p>

---

#### Configuración 3
**Coordenadas:** `(-35°, 35°, -30°, 30°, 0°)`

<p align="center">
  <img src="Diagramas-Imágenes/Actividad_7_E3.gif" width="700">
</p>

---

#### Configuración 4
**Coordenadas:** `(85°, -20°, 55°, 25°, 0°)`

<p align="center">
  <img src="Diagramas-Imágenes/Actividad_7_E4.gif" width="700">
</p>

---

#### Configuración 5
**Coordenadas:** `(80°, -35°, 55°, -45°, 0°)`

<p align="center">
  <img src="Diagramas-Imágenes/Actividad_7_E5.gif" width="700">
</p>

## Actividad 8.  Movimiento secuencial
Para dar solución a esto se reuso el script que se uso para la actividad número 5, se escogio el desplazamiento numero 5 ( 80, −35, 55, −45, 0.) y como se puede observar en el video se haciendo el movimiento secuencial se llega al mismo lugar




## Actividad 11. Cinemática directa

La cinemática directa del Phantom X Pincher se implementó mediante la parametrización de Denavit–Hartenberg (DH), la cual permite describir la geometría del manipulador mediante una secuencia de transformaciones homogéneas entre sistemas de referencia consecutivos.

Los parámetros DH utilizados para el modelo del robot se muestran en la siguiente tabla. En las articulaciones tercera y cuarta se incluyen los desfases angulares propios de la geometría del manipulador, originados por el eslabón en forma de "L".

<div align="center">

| i | θ<sub>i</sub> | d<sub>i</sub> (mm) | α<sub>i</sub> (°) | a<sub>i</sub> (mm) |
|:-:|:-------------:|:------------------:|:-----------------:|:------------------:|
| 1 | q₁ | 48,0 | 0 | 0 |
| 2 | q₂ + 90° | 44,5 | 90 | 0 |
| 3 | q₃ + 19,33° | 0 | 0 | 105,71 |
| 4 | q₄ − 19,33° | 0 | 0 | 100,0 |
| 5 | 0 | 0 | 0 | 113,6 |

</div>

A partir de estos parámetros se implementó un programa en Python (`fk_phantom.py`) que construye las matrices de transformación homogénea de cada articulación; posteriormente, el programa calcula la transformación homogénea total del manipulador mediante el producto matricial:

```text
T₀_TCP = A₁ · A₂ · A₃ · A₄ · A₅
```

A partir de esta matriz se obtiene la posición cartesiana del TCP (`x`, `y`, `z`) y la orientación del efector final en términos de los ángulos **Roll**, **Pitch** y **Yaw**.
El programa recibe como entrada las variables articulares del brazo

- q₁: Base
- q₂: Hombro
- q₃: Codo
- q₄: Muñeca

y calcula automáticamente la pose del TCP, obteniendo como salida:

- Posición cartesiana:
  - x
  - y
  - z

- Orientación:
  - Roll
  - Pitch
  - Yaw

Adicionalmente, el programa reutiliza el controlador desarrollado en la Actividad 7 para desplazar simultáneamente las articulaciones hasta la configuración ingresada. De esta manera, la posición calculada mediante la cinemática directa puede compararse directamente con la pose observada en RViz, permitiendo validar la implementación del modelo cinemático.
