# Inteligencia Artificial para Videojuegos - Práctica 0: Bloques Deslizantes

Se trata de un prototipo básico del clásico puzle de los bloques deslizantes que incorpora un resolutor automático. Este es el [enunciado completo](https://narratech.com/es/inteligencia-artificial-para-videojuegos/introduccion/bloques-deslizantes/) en la web de Narratech. 

La versión original del prototipo proviene del repositorio de libro Artificial Intelligence: A Modern Approach, aunque el prototipo fue revisado y completado por Federico Peinado. El código se distribuye bajo la licencia LGPL.

El propósito es servir como ejemplo a los alumnos para las demás prácticas de la asignatura.

## Instalación y uso
Todo el contenido del proyecto está disponible aquí en el repositorio, pues Unity en su versión adecuada debería ser capaz de bajar todos los paquetes necesarios.

Al no estar publicada todavía ninguna versión ejecutable del prototipo, ni enlazado ningún video con las pruebas realizadas, es necesario abrir el proyecto en Unity y usarlo desde allí.

## Introducción
Aunque en un videojuego lo habitual es que sea el jugador (humano) el que resuelva los puzles, a menudo es útil disponer de una IA capaz de hacerlo automáticamente. Esto puede servir para ayudar al jugador a superarlo o para darle cierta información (como los pasos que faltan por dar). También puede ayudar al diseñador a realizar pruebas más rápida y eficazmente, verificando que es posible superar el puzle y que este no tiene excesiva dificultad, e incluso a generar nuevos puzles, ya que es una tarea muy relacionada con el hecho de resolverlos. 

El puzle de bloques deslizantes, sliding puzzle o n-puzzle,  es un clásico dentro de los llamados “problemas de juguete”, una serie de problemas de combinatoria utilizados a menudo para teorizar o explicar conceptos lógico-matemáticos en Inteligencia Artificial. La variante de 8 bloques los tiene distribuidos en un tablero de 3x3 casillas, dejando habitualmente la esquina inferior derecha libre.

La mecánica consiste en deslizar piezas, generalmente planas, sobre ciertas rutas predefinidas, básicamente a una casilla vecina que esté libre en un tablero bidimensional). El objetivo es llegar a una cierta configuración final, partiendo de una configuración inicial diferente. A menudo estas piezas van numeradas o llevan impreso partes de un dibujo que podremos ver completo cuando hayamos resuelto el puzle. 

## Planteamiento del problema
Aunque no hay un enunciado como tal en la web de Narratech que sirva de punto de partida, expresamos por aquí lo que se nos pide diseñar:
Tenemos el clásico puzle de bloques deslizantes, de NxM dimensiones, que podemos reordenar manualmente e incluso desorganizar de manera aleatoria. Queremos probar y comparar dos resolutores automáticos para este problema de búsqueda no informada, uno basado en el algoritmo Primero en anchura y otro en Primero en profundidad.  

Desarrolla un prototipo de IA que permita resolver, tanto manual como automáticamente, el puzle deslizante de dimensiones N x N, es decir con (N x N) -1 piezas distribuidas, donde N > 1. El tablero con números de un 8-puzle será fácilmente manipulable y la solución automática se alcanzará mediante pura “fuerza bruta”. 

El prototipo permitirá:
A. Se trabajará sobre el punto de partida para mostrar el puzle en su configuración inicial, indicando de alguna forma que el puzle se encuentra ordenado. El usuario podrá mover las piezas manualmente, tantas veces como desee. Una pieza se puede mover si es vecina del espacio libre (o “hueco”).
B. Habrá un botón para reiniciar el puzle a su configuración inicial, y otro para desordenarlo aleatoriamente.
C. Habrá también botones suficientes para resolver automáticamente el puzle con al menos dos estrategias no informadas.
D. Se podrá ver la resolución paso a paso, no sólo la configuración final.
E. Tras la resolución automática, se mostrarán medidas del éxito conseguido, como el número de pasos de la solución o el tiempo empleado en ella.

En cuanto a interfaz, arriba se mostrarán mensajes sobre la ordenación del puzle y métricas de resolución (pasos, nodos empleados, etc.) una vez que se utilizan los resolutores, y siempre se buscará una buena usabilidad con ratón, clicando sobre botones y directamente sobre las piezas en una ventana cuadrada de 640x480 píxeles o superior. 

## Diseño de la solución
Para empezar se puede detallar algo sobre cómo es el escenario de juego, e incluso indicar los controles en un panel de la ventana, incluyendo cualquier atajo de teclado, etc. El botón Reset reinicia el tablero a la posición original, ajustando también filas y columnas según lo indicado en los recuadros. El botón Random actúa como Reset si hemos cambiado el tamaño de filas y columnas, y además reordena el puzle probando movimientos pseudoaleatorios. Los botones Solve BFS y Solve DFS llaman a los resolutores automáticos. Exit es para salir.

A continuación se puede añadir la representación utilizada para los datos y las estructuras intermedias (grafo de nodos) así como el pseudocódigo más preciso posible que se ha seguido para implementar el BFS y el DFS. Aquí todavía NO debemos entrar en detalles de la implementación, como el código C# del prototipo.

Indicar también cuál es la manera recomendada de realizar las pruebas, si manualmente, escribiendo texto en línea de comandos (o por el contrario, visual e interactivamente) o aprovechando algún banco de pruebas (cargando ficheros de texto, JSON o XML).

```mermaid
stateDiagram
    [*] --> Inicio
    Inicio --> Juego
    Juego --> Manual
    Manual : Resolución manual
    Juego --> Automatica 
    Automatica : Resolución automática
    Manual --> Resuelto
    Automatica --> Resuelto
    Resuelto --> Juego
    Resuelto :Puzle resuelto 
```
Lo que vamos a tener que utilizar:
* **Algoritmos**: Primero en anchura y Primero en profundidad (INSERTAR AQUÍ EL PSEUDOCÓDIGO)
* **Heurísticas**: Desordenar a base de clicar en piezas aleatorias
* **Trucos**: -

## Implementación
Las tareas se han realizado y el esfuerzo ha sido asumido por el único autor (ya que no era posible repartirlo entre varios).

| Estado  |  Tarea  |  Fecha  |  
|:-:|:--|:-:|
| ✔ | Diseño: Primer borrador | 1-2-2020 |
| ✔ | Desarrollo: Implementación del juego | 10-2-2020 |
| ✔ | Desarrollo: Implementación del resolutor | 13-2-2020 |
| ✔ | Desarrollo: Migración a Unity 2019 | 25-2-2021 |
| ✔ | Desarrollo: Migración a Unity 2022 | 24-2-2024 |
|   | ... | |
| :x: | Corregir error en resolutores | ... |

Las clases principales que se han desarrollados son las siguientes.
```mermaid
classDiagram
      BlockBoard <|-- MonoBehaviour
      CameraManager <|-- MonoBehaviour
      MovableBlock <|-- MonoBehaviour
      SlidingPuzzleManager <|-- MonoBehaviour
      class IDeepCloneable
      <<interface>> IDeepCloneable

      class IDeepCloneableT ["IDeepCloneable < T >"]
      <<interface>> IDeepCloneableT

      class Position

      SlidingPuzzle <|-- IDeepCloneableSP : implements
      class IDeepCloneableSP ["IDeepCloneable < SlidingPuzzle >"]
      <<interface>> IDeepCloneableSP
      SlidingPuzzle <|-- IEquatableSP : implements
      class IEquatableSP  ["IEquatable < SlidingPuzzle >"]
      <<interface>> IEquatableSP 
      SlidingPuzzle <|-- IComparableSP : implements
      class IComparableSP ["IComparable < SlidingPuzzle >"]
      <<interface>> IComparableSP
      SlidingPuzzle <|-- IComparable  : implements
      class IComparable
      <<interface>> IComparable

      class SlidingPuzzleFunctionFactory
      SlidingPuzzleGoalTest <|-- GoalTest : implements
      <<interface>> GoalTest
      class SlidingPuzzleSolver

      BasicOperator <|-- Operator : implements
      <<interface>> Operator
      NoOperator <|-- Operator : implements
      <<interface>> Operator

      FIFOQueueT <|--  QueueT
      class FIFOQueueT ["FIFOQueue < T >"]
      class QueueT ["Queue < T >"]

      FIFOQueueT <|--  IQueueT  
      class IQueueT ["IQueue < T >"]
      <<interface>> IQueueT
      IQueueT <|-- IEnumerableT 
      class IEnumerableT ["IEnumerable < T >"]
      <<interface>> IEnumerableT
      LIFOQueueT <|--  StackT
      class LIFOQueueT ["LIFOQueue < T >"] 
      class StackT ["Stack < T >"]
      LIFOQueueT <|-- IQueueT : implements

      class ApplicableOperatorsFunction
      <<interface>> ApplicableOperatorsFunction
      DefaultStepCostFunction <|-- StepCostFunction
      class GoalTest
      <<interface>> GoalTest
      GraphSearch <|-- QueueSearch
      class Metrics

      Node <|-- IEquatableN
      class IEquatableN ["IEquatable < Node >"]
      <<interface>> IEquatableN
      Node <|-- IComparableN
      class IComparableN ["IComparableN < Node >"]
      <<interface>> IComparableN
      Node <|-- IComparable
      class IComparable
      <<interface>> IComparable

      class NodeExpander
      class Problem
      QueueSearch <|--  NodeExpander
      class Search
      <<interface>> Search
      class SearchUtils
      class StepCostFunction
      <<interface>> StepCostFunction
      class TransitionModel
      <<interface>> TransitionModel

      BreadthFirstSearch <|--  Search : implements
      DepthFirstSearch <|--  Search : implements
```

## Pruebas
Detallar la serie más corta y rápida posible de pruebas que pueden realizarse para verificar que se cumple todo lo que piden el enunciado:

* Arranca la aplicación y haz un par de Reset para mostrar el puzle en su configuración inicial, y ver que se indica cuando el puzle está ordenado.  
* Clica tres veces en piezas vecinas del espacio libre o “hueco” (y en algunas que no lo sean) para ver que se pueden mover las piezas manualmente.  
* Usa el botón Reset para reiniciar el puzle a su configuración inicial y luego Random para ver que efectivamente se desordena aleatoriamente.  
* Usa el botón Solve BFS primero, y Solve DFS después (sobre un puzle de tamaño pequeño y no demasiado desordenando) para ver que se puede resolver automáticamente el puzle con esas dos estrategias no informadas.
* Observa la resolución paso a paso, no sólo su configuración final.  
* Observa las medidas del éxito (pasos, tiempo...) al terminar. 

## Conclusiones
Queda toda la posproducción por hacer: el pulido y la distribución del ejecutable del juego, así como la publicación del video-documental con las pruebas.

Para ir más allá en el aprendizaje, para el futuro consideramos estas posibles ampliaciones:
* Aumentar el número de estrategias (algoritmos) utilizados, para compararlos.
* Ofrecer más medidas del éxito, como número de nodos expandidos, nivel de profundidad alcanzado, memoria máxima utilizada durante la resolución, etc.
* Probar con alguna estrategia informada, pensando en alguna heurística válida.
* Usar otros algoritmos, otros tipos de búsqueda (informada) o un resolutor interactivo. 
* Generalizar el problema a puzles NxM.
* Generalizar el problema a puzles con piezas que ocupan más de una casilla. 

## Licencia
A, B y C, autores de la documentación, código y recursos de este trabajo, concedemos permiso permanente a los profesores de la Facultad de Informática de la Universidad Complutense de Madrid para utilizar nuestro material, con sus comentarios y evaluaciones, con fines educativos o de investigación; ya sea para obtener datos agregados de forma anónima como para utilizarlo total o parcialmente reconociendo expresamente nuestra autoría.

Una vez superada con éxito la asignatura se prevé publicar todo en abierto (la documentación con licencia Creative Commons Attribution 4.0 International (CC BY 4.0) y el código con licencia GNU Lesser General Public License 3.0).

## Referencias
* [AnalogBit: Sliding Block Puzzle Solver](http://analogbit.com/software/puzzletools/)
* [How Sliding Puzzles Work (How Stuff Works)](https://entertainment.howstuffworks.com/puzzles/sliding-puzzles.htm)
* Sliding Puzzle Collection (Random Box Studio, 2020)
* [Sliding puzzle (Wikipedia)](https://en.wikipedia.org/wiki/Sliding_puzzle)




