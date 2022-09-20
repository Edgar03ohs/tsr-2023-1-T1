# tsr-2023-1-T1
# Practica de documentación en Markdown

Entrega de la tarea No. 1 de la asignatura


| Código | Description |
| ------:| ----------- |
| ***Asignatura*** | Código del Trabajo o Número de Tarea | 
| **TSR-2023-I** | Tarea *01 |

## Contenido


1. [Introducción](#introduccion)
2. [Desarrollo](#desarrollo)

   - Clasificación de los robots móviles por configuración
   - Restricciones cinemáticas
   - Conceptos de localización, ruta, odometría y planeación de ruta.
   - Diferencias entre sistemas holonómicos y no-honolomicos.

    - Caracterización de la plataforma móvil TurtleBot3:

    - Modelo cinemático
   - Sensores y actuadores que lo integran.
   - Nodos y Tópicos de ROS utilizados por la plataforma Turtlebot3 y sus sensores

1. [Conclusiones](#conclusiones)
2. [Autor](#autor)
3. [Referencias](#referencias)

## Introducción

La extensión de Markdown y Markdown Enhanced permite la creación de documentos con formato presentable y estético, teniendo disponible una previsualización del documento ya con apariencia final. Una buena práctica para introducirse a esta herramienta es utilizarla para una investigación de conceptos relacionados a lo que ya se conoce, dividiendo todo el documento en secciones bien delimitadas y haciendo uso de recursos que pueden encontrarse en plantillas de trabajo.

## Desarrollo

#### Clasificación de los robots móviles por configuración

Según su tipo de locomoción, es decir el cómo se desplazan de un punto a otro, se encuentran los robots terrestres, aéreos, acuáticos, flotantes y submarinos.

Según cómo se guían en el ambiente, se encuentran los robots guiados y los no guiados. Los primeros siguen un camino predeterminado, por ejemplo, los que siguen líneas sobre el suelo para desplazarse. Los no guiados no siguen ningún patrón predeterminado de movimiento, se desplazan de acuerdo a la información que captan del entorno.[[1]](#1)

Pero la configuración del robot hace referencia a la manera en que están distribuidos los principales elementos que lo componen: ruedas, motores, encorders. De ella depende en gran medida la precisión del robot.

En cuanto a las ruedas, las configuraciones típicas son: diferencial, triciclo, Ackerman, sincronizada, omnidireccional, con múltiples grados de libertad y movimiento mediante orugas. Por ejemplo, en la diferencial, dos ruedas con motor, situadas diametralmente opuestas en un eje perpendicular a la dirección del robot,dan a este un giro, según las diferentes velocidades que tenga cada una. Los motores son elegidos tomando en cuenta la fuerza y el ahorro de energía requeridos.[[2]](#2)

#### Restricciones cinemáticas

Por lo que entiendo de lo recabado en distintos sitios web y trabajos de tesis de distintos niveles y lo que resulta de mi intuición, en general, los robots móviles siempre tienen restricción en cuanto a movimientos sobre un eje vertical perpendicular al plano principal en el que se desplazan, además de su rotación sobre los otros dos ejes que involucran que el robot traspase el plano mencionado.

Las variaciones o diferencias entre las restricciones de movimiento de un robot móvil a otro dependen o están directamente relacionadas con el tipo de ruedas que tenga. Por ejemplo, un robot que tiene ruedas omnidireccionales tendrá menor cantidad de restricciones de movimiento que uno diferencial simple, pues el diferencial, para moverse en la dirección del eje de sus ruedas tiene que cambiar su posición, girando con la asignación de diferente velocidad a cada rueda y poder cambiar la dirección de su avance; el omnidireccional, por tener rodillos con inclinación en sus ruedas puede desplazarse de orma directa sobre el eje de las ruedas.

Así sucede con los diferentes tipos de ruedas, cada una, ya sea fija, orientable centrada, orientable descentrada (castor) y sueca (también denominada universal, Mecanum ó Ilon) tiene diferntes restricciones.[[3]](#3)

#### onceptos de localización, ruta, odometría y planeación de ruta.

##### Localización

Consiste en determinar la posición de un robot respecto a un sistema de referencia o mapa del entorno. Dicha posición no se puede medir directamente, sino que se infiere a partir de datos sensoriales integrados a lo largo del tiempo con distintas mediciones. En función del conocimiento de la posición inicial del robot, se distinguen las siguientes dos tareas:

- Seguimiento de la posición: Se asume que la posición inicial del robot es conocida.
- Localización global: Se desconoce la ubicación inicial del robot en el entorno.

##### Ruta

Es el camino determinado que llevará al robot de un sitio de partida a otro destino. Se busca que la ruta o trayectoria sea óptima, evitando obstáculos y, dependiendo de los sensores y capacidades del robot, esta podría cambiar en el transcurso.

##### Odometría

Estudio de la estimación de la posición de vehículos con ruedas durante la navegación. Se usa información sobre la rotación de las ruedas para estimar cambios en la posición a lo largo del tiempo.
Los robots móviles usan la odometría para estimar (y no determinar) su posición relativa a su localización inicial, integrando la información incremental del movimiento a lo largo del tiempo.

##### Planeación de ruta

Encontrar una ruta óptima transitable, libre de obstáculos, entre una posición de origen o punto de partida y una posición objetivo o punto de llegada que el robot pueda seguir y cumplir físicamente.

Existen distintos métodos de planificación de trayectorias, tales como los Grafos de visibilidad, diagramas de Voronoi, roadmap probabilístico, modelado del espacio libre, descomposición en celdas o campos potenciales.


#### Diferencias entre sistemas holonómicos y no-honolomicos.

Esta clasificación está relacionada con la movilidad de los sistemas en cuestión. Los sistemas holonómicos son aquellos capaces de modificar su dirección instantáneamente, sin tomar en cuenta la masa del sistema y lo que pueda costar ponerla en movimiento, y sin necesidad de rotar previamente. Los no holonómicos son los incapaces de hacerlo.

#### Caracterización de la plataforma móvil TurtleBot3:




##### Modelo cinemático

Se trata de un robot diferencial

$$
\mathbb{q^°} \ =\ \begin{bmatrix}
	Φ & x^° & y^°
\end{bmatrix} \ =\ \begin{bmatrix}
-r/d2 & r/2d \\
r/2 cosΦ & r/2 cosΦ \\
r/2 isnΦ & r/2 sinΦ
\end{bmatrix} * \ \begin{bmatrix}
ωL\\
ωR
\end{bmatrix}
$$

donde: 
- Φ: Ángulo de giro con respecto al origen 
- r: Radio de las ruedas 
- d: Distancia del eje hacia el centro del eje del robot 
- ωL y ωR : Velocidades angulares de las ruedas del robot 



##### Sensores y actuadores que lo integran.

Motores DYNAMIXEL XL430.
Características:

| Motor | Húmedo |
| ------:| ----------- |
| ***Velocidad de transmisión 9600[bps]*** | 4.5 [Mbps] | 
| **TResolución** | 4096[pulso/rev] |
| **Temperatura de funcionamiento** | -5 ~ +72 [°C] |
| **Voltaje de entrada** | 6.5 ~ 12 [V] (recomendado: 11.1V) |
| **Conexión** | Bus multipunto TTL |

Sensor Laser LDS-01

Capaz de recopilar información alrededor del robot gracias a que gira 360°, además es accesible gracias a su fácil conexión y configuración.

CARACTERISTICAS

| Voltaje de operación  | 5V DC |
| ------:| ----------- |
| ***Consumo de corriente*** | 400mA o menos | 
| **Corriente de acometida** | 1A |
| **Tasa de muestreo** | 1.8KHz |
| **Distancia de detección** | 120mm ~ 3500mm |
| **Exactitud de distancia (120mm ~ 499mm)** | ±15mm |
| **Exactitud de distancia (50mm ~ 3500mm)** | ±5% |
| **Precisión de distancia (120mm ~ 499 mm)** | ±10mm |
| **Precisión de distancia (500mm ~ 3500mm)** | ±3.5% |
| **Rango angular** | 360° |
| **Resolución** | 1° |

##### Nodos y Tópicos de ROS utilizados por la plataforma Turtlebot3 y sus sensores

Nodos: SLAM, Teleoperation
Tópicos: cmd_vel (Para velocidad), odom (Para la odometría), LaserScan

## Conclusiones

Esta práctica resultó ser de gran utilidad para la familiarización con esta herramienta de Markdown y Markdown enhanced, así como de los recursos que se encuentran en las plantillas puestas a nuestra disposición relacionadas. Sobre todo considero de utilidad y practicidad que, específicamente la entrega consistiera en la investigación de conceptos relacionados con los temas que ya se han tocado a lo largo del curso para plasmarlos en un documento con secciones bien delimitadas.
Además de que la entrega es por medio de GitHub, otra herramienta que se nos incentiva a conocer y utilizar y que es un gran aliado para nuestra presentación como profesionales y profesionistas. Es un buen momento para que, si no teníamos cuenta, la creáramos y comenzaramos también a familiarizarnos con los comandos para el control de versiones y para que nos creemos la costumbre o buena práctica de almacenar en la plataforma todo nuestro trabajo que pueba hablar de nosotros.

## Autor

**Autor** Hernández Sosa Edgar Omar [GitHub profile](https://github.com/Edgar03ohs)

## Referencias

**Notas**

formato **IEEE**.[^nota] ← ***insertada al pie del documento con el no. 4***

[^nota]:
    Listado de referencias documentales consultadas para realizar el trabajo, consultar el siguiente [vínculo](https://www.bath.ac.uk/publications/library-guides-to-citing-referencing/attachments/ieee-style-guide.pdf) para el formato de referencia estilo **IEEE**.
    > `[^Num Ref]` Iniciales del autor. Apellido del autor, Título del libro, edicion (si no es la primera).
	>
    > Lugar de publicación: Publicador, Año.

<a id="1">[1]</a> Robótica Móvil: ¿Qué es y sus aplicaciones, recuperado el 14 de septiembre de 2022 de https://openwebinars.net/blog/robotica-movil-que-es-y-sus-aplicaciones/
<a id="2">[2]</a> http://www.mecamex.net/anterior/cong08/articulos/32.pdf
<a id="3">[3]</a> https://riunet.upv.es/bitstream/handle/10251/1840/tesisUPV2519.pdf
<a id="4">[4]</a> http://www.kramirez.net/Robotica/Material/Presentaciones/Odometria.pdf
<a id="5">[5]</a> https://intranet.ceautomatica.es/old/actividades/jornadas/XXIV/documentos/ro/201.pdf
<a id="6">[6]</a> Localización y planificación de trayectorias. (s/f). Tekniker.es. Recuperado el 16 de septiembre de 2022, de https://www.tekniker.es/es/localizacion-y-planificacion-de-trayectorias
<a id="7">[7]</a> https://bibdigital.epn.edu.ec/bitstream/15000/4913/1/Planeaci%C3%B3n%20y%20seguimiento%20de%20trayectorias.pdf
<a id="8">[8]</a> http://blog.electricbricks.com/2010/07/sistemas-holonomicos/360°
<a id="9">[9]</a> https://repository.udistrital.edu.co/bitstream/handle/11349/24883/CaperaCuellarCamila2020.pdf?sequence=2&isAllowed=y