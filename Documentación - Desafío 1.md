>Informática II - G1 - 20/03/2026

**Integrantes:** 
- Johan Steven Guarnizo Posada
- Oscar David Gutierrez Hernandez
## 1. Contextualización
### 1.1 Descripción del desafío y objetivos del curso
El presente trabajo consiste en el desarrollo de un motor simplificado del juego Tetris, implementado en `C++` bajo el `framework Qt` y utilizando exclusivamente interfaz de consola. A diferencia del juego tradicional, esta versión opera por turnos: el sistema muestra el estado actual del tablero, solicita una acción al usuario y procesa el movimiento de la pieza actual.

Tal como se establece en el documento del desafío 1:

> “El objetivo principal de esta actividad es poner a prueba sus habilidades en el análisis de problemas y en el dominio del lenguaje C++. Si ha seguido un proceso disciplinado de aprendizaje a lo largo del semestre, esta es una excelente oportunidad para demostrarlo. Podrá proponer una solución efectiva y obtener un resultado satisfactorio"

De esta manera, el desafío busca evaluar de forma práctica el dominio de técnicas avanzadas de programación en `C++`, con énfasis en el uso eficiente de operadores a nivel de bits y la gestión de memoria dinámica.
### 1.2 Consideraciones del desarrollo
Teniendo en cuenta que las indicaciones para el desarrollo del desafío son:
- **Dimensiones:** El ancho y alto mínimo deben ser de 8 bloques
- **Validación:** Debe ser múltiplo de 8
- **Lógica basada en operaciones a nivel de `Bits`:**  Definir estructuras que permitan representar los elementos requeridos en la visualización.
- **Piezas:** Para el tetris, las piezas a representar serán | (1x4) , Cuadrado (2x2), T (3x2), S (3x2), Z (3x2), J (2x3), L (2x3)
### 1.3. Restricciones del desarrollo
Lo que se debía tener en cuenta para el desarrollo del desafío 1 según la guía propuesta era:
1. No se pueden usar objetos tipo `string`como parte de la solución.
2. La implementación debe incluir el uso de punteros, arreglos y memoria dinámica
3. En la implementación no se pueden usar estructuras, librerías no autorizadas, ni STL.
4. La solución debe ser planteada con `C++` en el `framework Qt-Creator` 
5. **Uso de operadores a nivel de bits:** Desplazamientos, colisiones, rotaciones, fijación de piezas, eliminación de filas y detección de `Game Over` 
6. Gestión eficiente de la memoria
7. **Lógica del juego:** Que funcione como el clásico juego de Tetris

## 2. Desarrollo
### 2.1 Arquitectura
Existen 8 archivos excluyendo el archivo principal `main.cpp`  donde cada uno de estos archivos tiene un rol muy especifico. Dichos archivos, están divididos en el `Headers` y `Sources` de la siguiente forma: `panel_control cpp/h`, `piezas cpp/h`, `movimiento cpp/h` y `fin_juego cpp/h`. 

Puede interpretarse que su uso esta en forma piramidal. Viéndolo de la siguiente forma:

1. ***Panel de control (`panel_control cpp/h`):*** Actúa como el archivo que gestiona de manera exclusiva la asignación y liberación de la memoria dinámica correspondiente al escenario (la matriz de `booleanos`). 
	- **Relación:** Al contener la ocupación del `tablero` y los límites espaciales `alto` y `ancho`, es importado por casi la totalidad de los demás archivos y al mismo tiempo para poder ejecutar correctamente`imprimir_tablero()`, el archivo depende de las variables globales que se encuentran en `piezas`, con el objetivo de calcular la posición de las piezas al inicio del tablero.


2. ***Piezas(`piezas cpp/h`):*** Donde se almacena, mediante arreglos estáticos de tipo `unsigned short`, la representación en hexadecimal de los siete figuras clásicas (en cuadrículas de 4x4).
	- **Relación:** Usa `panel_control.h` para interactuar con el tablero, detectar choques con `hay_colision()` y fijar la posición de la pieza cuando deja de caer `fijar_pieza` 


3. ***Movimiento(`movimiento cpp/h`):*** Es el encargado de procesar el movimiento de la ficha en curso, modificando sus coordenadas (`X, Y`) basándose en las entradas del teclado.
	- **Relación:** Se apoya en `piezas.h` para validar cada movimiento. Nunca cambia la posición de la pieza sin antes verificar con `hay_colision()` si el nuevo espacio está libre y dentro de los límites.


4. ***Fin del juego(`fin_juego cpp/h`):*** Se activa cada vez que una pieza termina de caer. Revisa si hay líneas completas para borrarlas y verifica si el jugador perdió.
	- **Relación:** Importa tanto `panel_control.h` como `piezas.h`. Usando `panel_control.h` para buscar filas llenas (todas en `true`) y borrarlas con `eliminar_filas_llenas()` y con `piezas.h` para detectar si una pieza nueva choca apenas aparece (en la posición `[0][0]`), lo que activa el fin del juego.


5. ***Programa principal:*** Al ser el archivo al que el copilador de `C++` busca en un principio, entonces incluye todos los `.h` y organiza todo de forma correcta para configurar el tablero en memoria, carga las piezas y arranca el bucle de control.


Para comprender de mejor manera la escala piramidal del proceso que se sigue, entonces hemos dispuesto del siguiente diagrama de flujo:
![[Diagrama_de_flujo_documentacion.png]]

### 2.2 Descripción archivos

***`panel_control.cpp/h`*** 
Este archivo contiene la lógica para la administración espacial y visual del juego, gestionando de forma manual el almacenamiento de las dimensiones del tablero según lo ingresado por el usuario.

- `validar_dimensiones` captura el `ancho` y `alto` por consola y exige (mediante bucles `while`) que los valores sean mayores u iguales a 8 y estrictamente múltiplos de 8 (utilizando operador módulo `%`). Tras la validación, efectúa la reserva en el _Heap_ del bloque dinámico asignándolo a un puntero doble `bool** tablero`.

- `imprimir_tablero` Recorre celda por celda. Usando el operador AND a nivel de bit (`&`) para superponer la `pieza_actual` sobre el `tablero` en tiempo real. Aquellas celdas ocupadas en memoria o superpuestas temporalmente por la ficha activa se imprimen mediante el carácter `#`; las celdas vacías con el carácter `.`

- `destruir_tablero()` este lo hemos diseñado para liberar la memoria reservada con `delete[]` e impedir fugas de memoria.

***`piezas.cpp/h`***
