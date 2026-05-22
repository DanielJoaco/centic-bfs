# Informe Preliminar del Proyecto Final

## Titulo

Analisis de conectividad en la red del CENTIC de la UIS mediante teoria de grafos y el algoritmo BFS

## Integrantes

- Por definir

## Introduccion

La teoria de grafos es una rama de las matematicas discretas que permite modelar relaciones entre distintos elementos por medio de vertices y aristas. Esta herramienta resulta especialmente util para representar redes de comunicacion, ya que los dispositivos pueden interpretarse como nodos y sus enlaces como conexiones dentro de una estructura formal.

En este proyecto se propone analizar un caso aplicado al CENTIC de la Universidad Industrial de Santander, tomando como problema de estudio la conexion de distintos dispositivos a un servidor central. El interes principal consiste en determinar si existe una ruta valida entre un dispositivo de origen y el servidor, considerando requerimientos minimos de seguridad en las conexiones de la red.

Para abordar este problema se plantea el uso del algoritmo Breadth First Search (BFS), el cual permite recorrer un grafo por niveles y encontrar rutas validas con el menor numero de saltos posibles dentro de las conexiones que cumplan ciertas restricciones.

## Planteamiento del problema

En una red institucional como la del CENTIC, distintos equipos como computadores, switches, routers, impresoras o camaras requieren comunicarse con un servidor central para acceder a servicios, almacenar informacion o intercambiar datos. Sin embargo, no todas las conexiones disponibles entre estos dispositivos presentan las mismas condiciones tecnicas o de seguridad.

En este contexto surge la necesidad de modelar la red como un grafo que permita estudiar la conectividad entre los nodos y establecer si un dispositivo puede alcanzar el servidor a traves de una ruta que satisfaga condiciones minimas previamente definidas. Estas condiciones pueden estar asociadas al nivel de seguridad del enlace, al ancho de banda disponible o a la latencia aceptable para la comunicacion.

El problema central del proyecto consiste en determinar, mediante teoria de grafos y el uso de BFS, si existe una ruta valida entre un dispositivo y el servidor central, considerando un conjunto de restricciones minimas sobre las conexiones de la red.

## Justificacion

Este proyecto permite relacionar conceptos teoricos de matematicas discretas con una situacion cercana al entorno tecnologico universitario. La representacion de una red institucional mediante grafos facilita el analisis formal de la conectividad y muestra una aplicacion concreta de los recorridos sobre grafos.

Ademas, el uso de BFS resulta pertinente porque permite identificar rutas validas en terminos de conectividad, recorriendo la red por niveles y priorizando caminos con menor numero de saltos. Esto aporta una base clara para comprender como una herramienta matematica puede apoyar el analisis de problemas reales en infraestructura de redes.

## Objetivo general

Modelar la red de dispositivos del CENTIC de la UIS mediante un grafo y analizar la existencia de rutas validas hacia un servidor central usando el algoritmo BFS bajo restricciones minimas de seguridad.

## Objetivos especificos

- Representar la red del caso de estudio mediante vertices y aristas.
- Identificar los dispositivos y conexiones relevantes dentro del modelo.
- Definir restricciones minimas para validar una conexion entre nodos.
- Aplicar el algoritmo BFS para determinar si existe una ruta valida hacia el servidor.
- Analizar la utilidad del modelo de grafos en el estudio de redes institucionales.

## Marco teorico

La teoria de grafos estudia estructuras compuestas por vertices y aristas. Los vertices representan entidades, mientras que las aristas modelan relaciones o conexiones entre ellas. En el contexto de redes de computadores, cada dispositivo puede ser representado por un vertice y cada enlace de red por una arista.

Un grafo puede utilizarse para estudiar conectividad, rutas posibles, alcances entre nodos y propiedades estructurales de una red. En este proyecto interesa especialmente la nocion de camino, entendida como una secuencia de vertices conectados por aristas que permite desplazarse desde un nodo de origen hasta un nodo destino.

El algoritmo Breadth First Search, conocido como BFS, es un metodo de recorrido que explora el grafo por niveles. Primero visita los vecinos inmediatos del nodo inicial, luego los vecinos de estos, y asi sucesivamente. Una de sus principales ventajas es que, en grafos no ponderados, permite encontrar rutas con el menor numero de saltos entre un origen y un destino.

En el presente caso, BFS se aplicara sobre las conexiones que cumplan unos requisitos minimos definidos previamente. De esta manera, el algoritmo no recorrera enlaces no validos, sino solo aquellos que satisfagan las condiciones necesarias para considerar segura y aceptable la comunicacion con el servidor.

## Modelado del problema mediante grafos

Para el desarrollo del proyecto se propone representar la red del CENTIC como un grafo no dirigido.

- Los vertices representaran dispositivos de la red, tales como computadores, switches, routers, impresoras, camaras y el servidor central.
- Las aristas representaran las conexiones existentes entre dichos dispositivos.
- Cada arista tendra asociadas ciertas caracteristicas relevantes para el problema, como nivel de seguridad, ancho de banda y latencia.

Bajo este modelo, una conexion sera considerada valida si cumple con los requerimientos minimos establecidos para permitir el paso de informacion desde un nodo hasta otro. A partir de estas conexiones validas, se construira el recorrido BFS para analizar la posibilidad de llegar al servidor central.

## Propuesta de solucion con BFS

La propuesta consiste en aplicar BFS desde un dispositivo de origen dentro de la red. Antes de expandir cada conexion, se verificara si esta cumple con las condiciones minimas definidas para el estudio. Si una arista no satisface los criterios establecidos, entonces no sera tomada en cuenta dentro del recorrido.

De esta forma, BFS explorara un subgrafo compuesto unicamente por conexiones validas. Si durante el recorrido se alcanza el nodo correspondiente al servidor central, se concluira que existe una ruta valida entre el dispositivo de origen y el servidor. En caso contrario, se determinara que no existe una ruta que cumpla las restricciones del problema.

Este enfoque permite analizar de manera sencilla la conectividad segura en la red y resulta adecuado para una primera fase del proyecto, ya que se concentra en la existencia de rutas validas y en el menor numero de saltos dentro del conjunto de conexiones aceptadas.

## Variables y restricciones consideradas

Para el modelo preliminar se propone tener en cuenta las siguientes variables en cada conexion:

- Nivel de seguridad del enlace.
- Ancho de banda disponible.
- Latencia de la comunicacion.

Con base en ello, una conexion podra ser aceptada o rechazada de acuerdo con criterios como los siguientes:

- seguridad igual o superior a un minimo requerido
- ancho de banda igual o superior a un minimo establecido
- latencia igual o inferior a un maximo permitido

Estas restricciones no cambian el funcionamiento base de BFS, pero si determinan que conexiones forman parte del recorrido posible.

## Resultados esperados

Se espera obtener un modelo matematico claro de la red del CENTIC y una explicacion formal de como BFS puede utilizarse para estudiar la conectividad entre dispositivos y un servidor central. Asimismo, se espera identificar rutas validas bajo restricciones minimas y evidenciar la utilidad de la teoria de grafos como herramienta para el analisis de redes.

## Metodologia preliminar

El desarrollo del proyecto se plantea en varias etapas. Primero se definira el problema y se identificaran los elementos principales de la red a representar. Luego se construira el modelo del grafo y se estableceran las restricciones minimas para evaluar las conexiones. Posteriormente se aplicara BFS sobre el modelo planteado y finalmente se analizaran los resultados obtenidos para redactar las conclusiones del trabajo.

## Cronograma preliminar

1. Definicion detallada del problema y del caso de estudio.
2. Recoleccion de informacion sobre los dispositivos y conexiones a modelar.
3. Construccion del modelo de grafo.
4. Formulacion del recorrido mediante BFS.
5. Desarrollo del prototipo o simulacion.
6. Analisis de resultados.
7. Redaccion y ajuste del informe final.

## Bibliografia preliminar

- Rosen, K. H. Discrete Mathematics and Its Applications.
- Gross, J. L. y Yellen, J. Graph Theory and Its Applications.
- Material de clase de Matematicas Discretas.
- Documentacion introductoria sobre redes y algoritmos de recorrido en grafos.
