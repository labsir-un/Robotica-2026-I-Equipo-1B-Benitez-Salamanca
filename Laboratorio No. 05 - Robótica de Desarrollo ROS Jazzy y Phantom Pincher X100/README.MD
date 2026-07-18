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

La cinemática directa del robot Phantom X Pincher se implementó utilizando la convención clásica de Denavit–Hartenberg (DH). El anáisis se realiza mediante la siguiente convención de sistemas coordenados.

<p align="center">
  <img src="Diagramas-Imágenes/DH_esquema.jepg" width="700">
</p>



Tras analizar la geometría del manipulador y redefinir los sistemas de referencia, se obtuvo la siguiente parametrización:

<div align="center">

| i | θ<sub>i</sub> | d<sub>i</sub> (mm) | α<sub>i</sub> (°) | a<sub>i</sub> (mm) |
|:-:|:-------------:|:------------------:|:-----------------:|:------------------:|
| 1 | q₁ | 92.5 | -90 | 0 |
| 2 | q₂ − 70.67° | 0 | 0 | 105.71 |
| 3 | q₃ + 70.67° | 0 | 0 | 100.0 |
| 4 | q₄ | 0 | 0 | 66.6 |

</div>

Cada transformación homogénea se calcula mediante

```text
Aᵢ = Rz(θᵢ) · Tz(dᵢ) · Tx(aᵢ) · Rx(αᵢ)
```

obteniendo la transformación hasta el último sistema de referencia del manipulador

```text
T₀₄ = A₁ · A₂ · A₃ · A₄
```

El TCP del Phantom X Pincher no coincide con el origen del último marco DH, por lo que se definió una transformación homogénea fija entre ambos sistemas de referencia:

```text
        ┌                      ┐
        │  0   0   1   47.0    │
TNOA =  │ -1   0   0    0.0    │
        │  0  -1   0    0.0    │
        │  0   0   0    1.0    │
        └                      ┘
```

La pose final del efector se obtiene mediante

```text
T₀TCP = T₀₄ · TNOA
```

A partir de esta matriz se extraen automáticamente:

- Posición cartesiana del TCP:
  - x
  - y
  - z

- Orientación del TCP:
  - Roll
  - Pitch
  - Yaw

El programa `fk_phantom.py` recibe como entrada los ángulos articulares **q₁**, **q₂**, **q₃** y **q₄**, calcula la cinemática directa y, simultáneamente, publica dichas posiciones sobre el tópico `/pincher/command`, realizando una interpolación lineal desde la configuración actual hasta la configuración objetivo. Esto permite comparar directamente la pose calculada con la visualizada en RViz, verificando la correcta implementación del modelo cinemático.

Durante el desarrollo fue necesario redefinir los sistemas de referencia utilizados en la parametrización DH, ya que inicialmente el sistema base se había asociado al marco del mundo y no al eje de la primera articulación. Una vez corregida esta asignación y actualizada la transformación fija del TCP (`TNOA`), la posición y orientación calculadas coincidieron con el comportamiento observado en la simulación.
