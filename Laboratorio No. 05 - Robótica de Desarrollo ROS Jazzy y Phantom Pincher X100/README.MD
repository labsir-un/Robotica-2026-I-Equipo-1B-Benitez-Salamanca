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
