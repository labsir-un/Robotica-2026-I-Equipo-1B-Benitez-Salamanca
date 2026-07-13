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
| Base (Waist) | N.A. | 0 rad (posición inicial) | Giro antihorario del brazo alrededor del eje vertical al aumentar el ángulo. | Rotación de toda la estructura del brazo. |
| Hombro (Shoulder) | N.A. | 0 rad (posición inicial) | Elevación del primer eslabón al aumentar el ángulo. | Elevar y descender el brazo. |
| Codo (Elbow) | N.A. | 0 rad (posición inicial) | Extensión del segundo eslabón al aumentar el ángulo. | Acercar o alejar el efector final. |
| Muñeca (Wrist) | N.A. | 0 rad (posición inicial) | Rotación de la muñeca para orientar la pinza al aumentar el ángulo. | Orientar la pinza. |
| Pinza (Gripper) | N.A. | Posición inicial (cerrada o según el modelo) | Apertura de las mordazas al aumentar el comando de la pinza. | Sujetar y liberar objetos. |
