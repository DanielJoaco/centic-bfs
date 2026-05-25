# Informe Final del Proyecto

## Titulo

Analisis de conectividad en la red del CENTIC de la UIS mediante teoria de grafos y el algoritmo BFS

## Integrantes

- Adrian Santiago Sanchez Guerra - F2
- Daniel Joaquin Orjuela Holguin - F3
- Jose David Consuegra Medina - F3
- Cristian David Pinzón Galvis - F2

## Roles del grupo

- Lider del grupo: Jose David Consuegra Medina.
- Daniel Joaquin Orjuela Holguin: implementacion del algoritmo BFS y apoyo en el notebook de Google Colab.
- Cristian David Pinzón Galvis: apoyo en la elaboracion del poster.
- Adrian Santiago Sanchez Guerra: apoyo en la elaboracion del video.
- Jose David Consuegra Medina: liderazgo del grupo, desarrollo y redaccion del informe final.

## Enlaces del proyecto

- Notebook en Google Colab: https://colab.research.google.com/github/DanielJoaco/centic-bfs/blob/main/centic_bfs.ipynb
- Repositorio de GitHub: https://github.com/DanielJoaco/centic-bfs
- Video en YouTube: https://youtu.be/4uEC7MpZv7Q
- Poster:Archivo adjunto en pdf externo.

## 1. Sobre el proyecto

### 1.1 Descripcion del problema

En una red institucional como la del CENTIC de la Universidad Industrial de Santander, distintos dispositivos necesitan comunicarse con un servidor central. Entre estos dispositivos se encuentran computadores de aulas, computadores centrales de aula, switches, routers Wi-Fi, camaras, impresoras, computadores administrativos y equipos asociados a vigilancia. Aunque todos hacen parte de una misma infraestructura, no todas las conexiones tienen las mismas condiciones tecnicas ni el mismo nivel de seguridad.

El problema seleccionado consiste en determinar si un dispositivo de origen puede alcanzar el servidor central a traves de una ruta valida. Para que una ruta sea considerada valida, cada conexion utilizada debe cumplir unos requisitos minimos de seguridad, ancho de banda y latencia. De esta forma, el problema no se limita a saber si dos dispositivos estan conectados fisicamente, sino a verificar si existe una comunicacion aceptable bajo restricciones definidas.

La situacion puede ser abordada desde la teoria de grafos porque una red de comunicaciones puede representarse como un conjunto de nodos conectados por enlaces. En este proyecto, cada dispositivo se modela como un vertice y cada conexion fisica se modela como una arista. Las aristas tienen atributos asociados que permiten validar si pueden ser usadas dentro de una ruta hacia el servidor.

El grafo construido en el notebook es un modelo representativo y sintetico inspirado en la red del CENTIC. No se presenta como una medicion real exacta de la infraestructura, sino como una abstraccion suficiente para estudiar el problema de conectividad bajo restricciones. El modelo incluye 551 vertices y 550 aristas, distribuidos en una estructura con servidor central, core switch, switches de piso, aulas, computadores, camaras, routers Wi-Fi, impresoras, administracion y vigilancia.

### 1.2 Investigacion del problema y alternativas de solucion

El problema real se puede expresar como la necesidad de comprobar si existe una ruta aceptable entre un dispositivo de origen y el servidor central de la red. La version matematica equivalente es un problema de alcanzabilidad en grafos: dado un grafo no dirigido `G=(V,E)`, un vertice de origen `s`, un vertice destino `t` y un conjunto de restricciones sobre las aristas, se debe determinar si existe un camino desde `s` hasta `t` usando solamente aristas validas.

Formalmente, cada arista tiene tres atributos: seguridad, ancho de banda y latencia. Una arista es valida si cumple simultaneamente las siguientes condiciones:

- `seguridad >= s_min`
- `ancho_de_banda >= b_min`
- `latencia <= l_max`

Con estas condiciones se forma un subgrafo compuesto solo por las conexiones validas. El problema se reduce entonces a buscar si el destino pertenece al conjunto de vertices alcanzables desde el origen dentro de ese subgrafo.

Para resolver este problema se analizaron varias alternativas algoritmicas propias de la teoria de grafos:

- BFS, busqueda en anchura: recorre el grafo por niveles desde el origen. Permite determinar alcanzabilidad y, en grafos no ponderados, encontrar una ruta con el menor numero de saltos. Es adecuada cuando el costo de las aristas no se usa como peso acumulado, sino como criterio de aceptacion o rechazo.
- DFS, busqueda en profundidad: tambien permite determinar si existe una ruta entre dos vertices. Sin embargo, no garantiza encontrar una ruta con el menor numero de saltos, por lo que resulta menos conveniente para explicar la conectividad por niveles.
- Componentes conexas: permiten identificar grupos de vertices conectados entre si. Si se construye primero el subgrafo de aristas validas, se puede verificar si origen y destino pertenecen a la misma componente. Esta alternativa es util cuando se quieren responder muchas consultas de conectividad sobre el mismo escenario, pero no describe tan directamente la ruta encontrada desde un origen especifico.
- Warshall o Floyd-Warshall: pueden usarse para estudiar alcanzabilidad entre todos los pares de vertices mediante una matriz. Sin embargo, para un grafo de cientos de nodos puede ser menos practico por su costo computacional y porque el proyecto solo requiere comprobar rutas hacia un servidor central en escenarios concretos.

El algoritmo seleccionado para la implementacion fue BFS. Esta seleccion es coherente con el objetivo del proyecto porque se busca conectividad y numero minimo de saltos dentro de un subgrafo valido, no una optimizacion por pesos acumulados. El algoritmo de Dijkstra no se utiliza, ya que esta prohibido por la guia del proyecto y ademas no es necesario para el enfoque planteado.

### 1.3 Productos esperados

Como resultado del proyecto se consideran los siguientes productos:

- Notebook en Google Colab: contiene la descripcion del problema, el modelo del grafo, los escenarios de prueba, la implementacion propia de BFS con filtrado de aristas, las tablas de resultados y las visualizaciones.
- Video en YouTube: producto pendiente de enlace. Su objetivo sera presentar en un maximo de ocho minutos el problema, la investigacion realizada, la solucion algoritmica y los resultados obtenidos.
- Poster: producto pendiente de enlace o archivo final. Su objetivo sera resumir el proceso seguido, el modelo de grafos, la implementacion y los resultados principales.

### 1.4 Roles de los miembros del grupo

El grupo definio roles para distribuir el trabajo del proyecto. Jose David Consuegra Medina es el lider del grupo y se encarga del desarrollo y redaccion del informe final. Daniel Joaquin Orjuela Holguin se encarga principalmente de la implementacion del algoritmo BFS y del desarrollo computacional en el notebook. Adrian Santiago Sanchez Guerra apoya la elaboracion del video. Cristian David Pinzón Galvis apoya la elaboracion del poster.

Estos roles pueden ajustarse en la entrega final si el grupo modifica la distribucion de tareas o confirma datos faltantes.

### 1.5 Criterios de evaluacion considerados

El informe se desarrolla teniendo en cuenta los productos y porcentajes definidos para el proyecto. La descripcion e investigacion del problema, junto con las alternativas de solucion, se reflejan en las secciones de modelado, equivalencia matematica y seleccion algoritmica. La implementacion computacional se documenta a partir del notebook de Google Colab. El video y el poster se registran como productos esperados, con enlaces pendientes de confirmacion.

## 2. Objetivos

### 2.1 Objetivo general

Modelar una red representativa del CENTIC de la UIS mediante un grafo no dirigido y analizar la existencia de rutas validas hacia un servidor central usando BFS bajo restricciones de seguridad, ancho de banda y latencia.

### 2.2 Objetivos especificos

- Representar dispositivos de la red como vertices y conexiones fisicas como aristas.
- Asociar a cada arista atributos de seguridad, ancho de banda y latencia.
- Definir escenarios de operacion con distintos umbrales para validar conexiones.
- Implementar BFS de forma propia para buscar rutas hacia el servidor central.
- Comparar los resultados de alcanzabilidad en escenarios normal, seguridad alta, critico y congestion.
- Analizar la utilidad del modelo de grafos para estudiar conectividad en redes institucionales.

## 3. Modelado del problema mediante grafos

El modelo usa un grafo no dirigido `G=(V,E)`. El conjunto `V` representa los dispositivos y el conjunto `E` representa las conexiones fisicas entre ellos. Se usa un grafo no dirigido porque las conexiones modeladas se interpretan como enlaces fisicos que permiten comunicacion en ambos sentidos para el analisis de conectividad.

Los vertices principales del modelo son:

- `server_central`: servidor central de la red.
- `core_switch`: switch principal que conecta las areas de la red.
- Switches de piso.
- Switches de aula.
- Computadores de aula.
- Computadores centrales de aula.
- Routers Wi-Fi.
- Camaras.
- Impresoras.
- Computadores administrativos.
- Equipo de vigilancia.

Cada arista tiene los siguientes atributos:

- `security`: nivel de seguridad de la conexion, en escala de 1 a 5.
- `bandwidth`: ancho de banda disponible en Mbps.
- `latency`: latencia de la conexion en ms.

La seguridad se interpreta como una escala ordinal. Un valor bajo representa enlaces con controles debiles, mientras que un valor alto representa enlaces con controles reforzados, segmentacion, monitoreo y acceso mas restringido.

## 4. Equivalencia entre el problema real y el problema matematico

La equivalencia central del proyecto es la siguiente:

- En la red real, se desea saber si un dispositivo puede comunicarse con el servidor central mediante conexiones aceptables.
- En el modelo matematico, se desea saber si existe un camino entre dos vertices dentro de un subgrafo de aristas validas.

Cada escenario define umbrales minimos. Una conexion que no cumple esos umbrales se descarta para el recorrido. Por tanto, BFS no se ejecuta sobre todo el grafo original de manera indiscriminada, sino sobre las conexiones que cumplen las condiciones requeridas en el momento de expandir vecinos.

Esta equivalencia permite pasar de un problema tecnico de redes a un problema formal de teoria de grafos: determinar alcanzabilidad entre un origen y un destino bajo restricciones sobre las aristas.

## 5. Implementacion computacional

La implementacion se realizo en un notebook de Google Colab enlazado al repositorio de GitHub del proyecto. Las librerias usadas son `networkx`, `pandas`, `matplotlib` y `seaborn`. `networkx` se usa para representar el grafo, `pandas` para organizar resultados en tablas y `matplotlib` junto con `seaborn` para generar visualizaciones.

El notebook construye un grafo sintetico de 551 nodos y 550 aristas. La topologia considera 4 pisos. En cada piso se modelan aulas, computadores, camaras, routers Wi-Fi, switches, recepcion e impresoras. Tambien se incluye un bloque administrativo y un equipo de vigilancia, conectados al servidor central mediante el core switch.

La funcion `edge_is_valid` verifica si una arista cumple los tres umbrales definidos para un escenario. La funcion `bfs_valid_path` implementa BFS desde un origen hasta el servidor central. Durante la expansion de vecinos, la funcion revisa los atributos de cada arista y solo agrega a la cola los vertices conectados por enlaces validos.

El algoritmo mantiene un conjunto de visitados, una cola de exploracion y un diccionario de padres para reconstruir la ruta cuando el servidor es alcanzado. Si el servidor no aparece en el diccionario de padres al terminar el recorrido, se concluye que no existe una ruta valida bajo las restricciones del escenario.

La complejidad temporal esperada de BFS es `O(|V| + |E|)` y la complejidad espacial es `O(|V|)`, donde `V` es el conjunto de vertices y `E` el conjunto de aristas.

## 6. Escenarios de prueba

El notebook evalua cuatro escenarios con distintos niveles de exigencia:

- Normal: `s_min = 3`, `b_min = 100`, `l_max = 30`.
- Seguridad alta: `s_min = 4`, `b_min = 200`, `l_max = 20`.
- Critico: `s_min = 5`, `b_min = 300`, `l_max = 15`.
- Congestion: `s_min = 2`, `b_min = 50`, `l_max = 50`.

Los origenes evaluados hacia el servidor central son:

- PC de aula comun.
- PC central de aula.
- PC administrativo.
- Equipo de vigilancia.

Estos origenes permiten comparar dispositivos con diferentes condiciones de conexion y distintos niveles de prioridad dentro de la red modelada.

## 7. Resultados obtenidos

Los resultados del notebook muestran que la alcanzabilidad cambia segun los umbrales aplicados:

- En el escenario normal, todos los origenes evaluados alcanzan el servidor central.
- En el escenario de seguridad alta, el PC de aula comun no alcanza el servidor, mientras que el PC central de aula, el PC administrativo y el equipo de vigilancia si lo alcanzan.
- En el escenario critico, el PC de aula comun y el PC central de aula no alcanzan el servidor. El PC administrativo y el equipo de vigilancia si mantienen una ruta valida.
- En el escenario de congestion, todos los origenes evaluados alcanzan el servidor central.

Tambien se observa que las rutas de administracion y vigilancia tienen menos saltos que las rutas desde aulas. En el notebook, vigilancia alcanza el servidor en 2 saltos, administracion en 3 saltos y los equipos de aula en 4 saltos cuando las restricciones lo permiten.

## 8. Analisis de resultados

Los resultados confirman que la conectividad no depende solo de la existencia fisica de enlaces, sino tambien de las condiciones exigidas a cada conexion. Cuando los umbrales son moderados, como en el escenario normal, la mayoria de enlaces relevantes siguen siendo validos y los dispositivos evaluados pueden llegar al servidor.

En seguridad alta, los computadores comunes de aula pierden conectividad porque sus enlaces finales tienen menor nivel de seguridad o menor capacidad frente a los umbrales definidos. En cambio, el PC central de aula conserva acceso porque su conexion al switch de aula tiene mejores atributos.

En el escenario critico, solo los dispositivos conectados mediante enlaces mas robustos conservan una ruta valida. Esto explica por que administracion y vigilancia siguen alcanzando el servidor mientras algunos dispositivos de aula quedan aislados bajo las restricciones mas estrictas.

El escenario de congestion permite mayor latencia y menor ancho de banda, por lo que la alcanzabilidad se mantiene. Este caso muestra que relajar ciertos criterios puede aumentar el subgrafo disponible para BFS, aunque no necesariamente significa que la red tenga mejores condiciones de operacion.

En general, BFS resulta adecuado porque permite encontrar rapidamente si existe una ruta valida y, cuando existe, reconstruir una ruta con el menor numero de saltos en el subgrafo considerado.

## 9. Conclusiones

- La red del CENTIC puede modelarse de forma clara mediante un grafo no dirigido, donde los dispositivos son vertices y las conexiones fisicas son aristas.
- El problema real de conectividad hacia un servidor central se transforma en un problema matematico de alcanzabilidad bajo restricciones.
- BFS es una solucion adecuada porque permite recorrer el grafo por niveles, filtrar conexiones invalidas y encontrar rutas con menor numero de saltos en un grafo no ponderado.
- Las restricciones de seguridad, ancho de banda y latencia modifican el subgrafo disponible y pueden cambiar completamente la alcanzabilidad de algunos dispositivos.
- Los dispositivos administrativos y de vigilancia presentan mayor disponibilidad en escenarios exigentes debido a que sus enlaces fueron modelados con atributos mas robustos.
- El modelo permite analizar de forma comprensible como las condiciones de una red afectan la comunicacion hacia un servidor central.

## 10. Trabajo futuro

Como trabajo futuro se podria ampliar el modelo usando datos reales de trafico e infraestructura del CENTIC. Tambien se podria considerar un grafo dirigido para representar politicas de acceso no simetricas, agregar prioridad por tipo de dispositivo y simular fallas en switches o enlaces criticos. Otra extension posible seria comparar la respuesta del modelo ante cambios progresivos en los umbrales de seguridad, ancho de banda y latencia.

## 11. Bibliografia

- Rosen, K. H. Discrete Mathematics and Its Applications.
- Gross, J. L. y Yellen, J. Graph Theory and Its Applications.
- Material de clase de Matematicas Discretas.
- Documentacion de NetworkX: https://networkx.org/documentation/stable/
- Repositorio del proyecto: https://github.com/DanielJoaco/centic-bfs
- Notebook en Google Colab: https://colab.research.google.com/github/DanielJoaco/centic-bfs/blob/main/centic_bfs.ipynb
