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

### Actividad 6. Determinación de límites seguros

Los siguientes límites fueron determinados experimentalmente a partir de la simulación en RViz. Los valores corresponden a aproximaciones visuales obtenidas considerando el mejor caso, es decir, evaluando cada articulación de manera independiente y sin interferencias ocasionadas por la configuración instantánea de las demás articulaciones. Para garantizar una operación segura, el programa debe impedir el envío de comandos fuera de estos rangos.

| Articulación | Límite inferior (rad) | Límite superior (rad) | Margen de seguridad |
|--------------|----------------------:|----------------------:|--------------------:|
| Base | -2.618 | 2.618 | 0.10 rad |
| Hombro | -2.00 | 2.00 | 0.10 rad |
| Codo | -2.15 | 1.571 (π/2) | 0.10 rad |
| Muñeca | -2.00 | 2.30 | 0.10 rad |
| Pinza | -1.571 (-π/2) | 1.571 (π/2) | 0.10 rad |
