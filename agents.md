# Diseno arquitectonico (agents.md)

## Modelado matematico

Se modela la red del CENTIC como un grafo no dirigido:

- Grafo: $G = (V, E)$.
- Vertices $V$: dispositivos de red y usuarios finales. Incluye servidor central, core switch, switches de piso, routers wifi, PCs de aulas, PC central por aula, camaras, impresoras, PC de recepcion, oficinas administrativas y cuarto de vigilancia.
- Aristas $E$: conexiones fisicas entre dispositivos. Cada arista tiene atributos:
  - seguridad (escala 1-5)
  - ancho de banda (Mbps)
  - latencia (ms)

Una conexion es valida si cumple umbrales minimos en seguridad, ancho de banda y latencia. El problema se reduce a encontrar si existe un camino valido entre un nodo de origen y el servidor central dentro del subgrafo de conexiones validas.

## Seleccion algoritmica

Se selecciona BFS (Breadth First Search) porque:

- El grafo es no ponderado respecto al costo (se busca conectividad y menor numero de saltos).
- BFS encuentra rutas con el menor numero de saltos en grafos no ponderados.
- Se puede filtrar aristas por restricciones (seguridad, ancho de banda, latencia) antes de expandir vecinos.
- Dijkstra esta prohibido por la guia del proyecto.

Complejidad esperada: $O(|V| + |E|)$ en tiempo y $O(|V|)$ en memoria.

## Roadmap de ejecucion del notebook

1. Planteamiento del problema y supuestos del modelo.
2. Definicion formal del grafo $G=(V,E)$ y atributos de aristas.
3. Definicion de escenarios (normal, alta seguridad, congestion) y umbrales.
4. Implementacion de BFS con filtrado de aristas.
5. Construccion del grafo sintetico (4 pisos, aulas, PCs, camaras, oficinas, vigilancia).
6. Ejecucion de BFS desde distintos origenes hacia el servidor.
7. Visualizacion de la topologia (subgrafo representativo).
8. Tablas comparativas con resultados por escenario.
9. Conclusiones y trabajo futuro.
