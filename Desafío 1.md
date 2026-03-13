# Implementación de Tetris mediante manipulación de bits en C++ – Desafío 1
>Informática II - G1 - 13/03/2026

**Integrantes:** 
- Johan Steven Guarnizo Posada
- Oscar David Gutierrez Hernandez
## 1. Contextualización
### Descripción breve del desafío y objetivos del curso
<div style="text-align: justify;">
El presente trabajo consiste en el desarrollo de un motor simplificado del juego Tetris, implementado en `C++` bajo el `framework Qt` y utilizando exclusivamente interfaz de consola. A diferencia del juego tradicional, esta versión opera por turnos: el sistema muestra el estado actual del tablero, solicita una acción al usuario y procesa el movimiento de la pieza actual.
</div>

Tal como se establece en el documento del desafío 1:

<div style="text-align: justify;">

> “El objetivo principal de esta actividad es poner a prueba sus habilidades en el análisis de problemas y en el dominio del lenguaje C++. Si ha seguido un proceso disciplinado de aprendizaje a lo largo del semestre, esta es una excelente oportunidad para demostrarlo. Podrá proponer una solución efectiva y obtener un resultado satisfactorio"

</div>

<div style="text-align: justify;">
De esta manera, el desafío busca evaluar de forma práctica el dominio de técnicas avanzadas de programación en `C++`, con énfasis en el uso eficiente de operadores a nivel de bits y la gestión de memoria dinámica.
</div>

<div style="text-align: justify;">

### Consideraciones del desarrollo
1. No se pueden usar objetos tipo `string`como parte de la solución.
2. La implementación debe incluir el uso de punteros, arreglos y memoria dinámica
3. En la implementación no se pueden usar estructuras, librerías no autorizadas, ni STL.
4. La solución debe ser planteada con `C++` en el `framework Qt-Creator` 
5. **Uso de operadores a nivel de bits:** Desplazamientos, colisiones, rotaciones, fijación de piezas, eliminación de filas y detección de `Game Over` 
6. Gestión eficiente de la memoria
7. **Lógica del juego:** Que funcione como el clásico juego de Tetris

</div>

## 2. Análisis del problema
## Requisitos de desarrollo

<div style="text-align: justify;">

Teniendo en cuenta que las indicaciones para el desarrollo del desafío son:
- **Dimensiones:** El ancho y alto mínimo deben ser de 8 bloques
- **Validación:** Debe ser múltiplo de 8
- **Lógica basada en operaciones a nivel de `Bits`:**  Definir estructuras que permitan representar los elementos requeridos en la visualización.
- **Piezas:** Para el tetris, las piezas a representar serán | (1x4) , Cuadrado (2x2), T (3x2), S (3x2), Z (3x2), J (2x3), L (2x3)
![[aaa.png]]

</div>

## Pasos a seguir
<div style="text-align: justify;">

Teniendo en cuenta los requisitos anteriores, consideramos que los pasos que deben de seguirse para una elaboración optima son los siguientes:
### Diseño del panel de control
- **Uso de bits para filas:** Cada fila del tablero se representa con números enteros (por ejemplo, `uint8_t` para un ancho de 8 bloques).
- **Ancho personalizado:** El programa permitirá al usuario elegir el tamaño, pero siempre se verificará que el ancho sea múltiplo de 8 para facilitar la gestión de bytes, tal como indica el documento desafío 1.
- **Matriz flexible:**  Se intentara usar una matriz (con punteros) para definir la altura del tablero. Para no desperdiciar memoria y cumplir con el uso de memoria dinámica.
### Piezas
- **Mapa de bits:** Cada pieza será una pequeña cuadrícula de bits, lo que hace el juego rápido y con bajo consumo de memoria.
- **Rotaciones almacenadas:** En lugar de calcular rotaciones complejas, se predefinirán las rotaciones de cada pieza en un arreglo para que el programa solo cambie entre ellas.
- **Generación aleatoria:** El juego elegirá una pieza diferente en cada turno y la colocará en la parte superior central para iniciar la ronda.
### Movimiento y colisiones
- **Desplazamiento lateral:** Se usarán los operadores `<<` y `>>` para mover las piezas hacia la izquierda o derecha.
- **Detección de colisiones:** Se aplicará el operador `&`. Si el resultado al comparar la pieza con el tablero no es `0`, significa que hay choque y la pieza no puede moverse allí.
- **Fijación de piezas:** Cuando una pieza ya no pueda descender, se usará el operador | (OR) para integrarla permanentemente al tablero.
### Eliminación de líneas
- **Línea completa:** Se verificará si todos los bits de una fila están en `1`. Si es así, la fila se elimina.
- **Descenso de bloques:**  Al eliminar una fila, las superiores se desplazarán hacia abajo mediante punteros, sin necesidad de mover bloque por bloque.
## Pantalla y fin del juego
- **Representación visual:** Se usará `#` para bloques ocupados y `.`  para espacios vacíos, dibujando el tablero en la consola.
- **Controles:** El usuario jugará con las teclas `A (izquierda)`, `D (derecha)`, `S (abajo)` y `W (rotar)`.
- **Game Over:** Si una nueva pieza no puede colocarse en la parte superior porque ya está ocupada, el programa mostrará el mensaje ***“Juego terminado”*** y fin


## 3. Algoritmo

Para entender mejor el desarrollo del desafío hemos dispuesto de `Pseint`para analizar y desarrollar el algoritmo base a seguir durante el desarrollo. El algoritmo es:
![[Diagrama de flujo pseint.png]]
Donde el código de `Pseint`es:
```pascal
Algoritmo TetrisBits
	Definir ancho, alto, posicionX, posicionY Como Entero
	Definir gameOver, piezaFijada, colision Como Logico
	Definir accion Como Caracter
	
	Escribir "Ingrese ancho del tablero (múltiplo de 8, min 8): "
	Leer ancho
	Escribir "Ingrese alto del tablero (min 8): "
	Leer alto
	
	Si ancho < 8 O ancho MOD 8 <> 0 O alto < 8 Entonces
		Escribir "Dimensiones invalidas. El ancho debe ser múltiplo de 8."
	Sino
		gameOver <- Falso
		Mientras No gameOver Hacer
			posicionX <- trunc(ancho / 2) - 2
			posicionY <- 0
			piezaFijada <- Falso
			colision <- Falso
			
			Mientras No piezaFijada Hacer
				Escribir "Accion: [A]Izq [D]Der [S]Bajar [W]Rotar [Q]Salir:"
				Leer accion
				Segun accion Hacer
					"A", "a": posicionX <- posicionX - 1
					"D", "d": posicionX <- posicionX + 1
					"W", "w": Escribir "Rotando..."
					"S", "s": 
						posicionY <- posicionY + 1
						piezaFijada <- Verdadero 
					"Q", "q":
						gameOver <- Verdadero
						piezaFijada <- Verdadero
				FinSegun
				
				Si No piezaFijada Y accion <> "S" Y accion <> "s" Entonces
					posicionY <- posicionY + 1
				FinSi
			FinMientras
		FinMientras
		Escribir "GAME OVER"
	FinSi
FinAlgoritmo

```
</div>

## Esquema de Tareas - Cronograma
En vista de que la fecha máxima de entrega es el 20 de Marzo, entonces el trabajo se realizará de la siguiente forma:

- **14/03/26 - Sábado:** Realizar funciones relacionadas al diseño del panel de control. `Filas()`, `Ancho` y `Matriz`.
- **15/03/26 - Domingo:** Día libre.
- **16/03/26 - Lunes:** Funciones relacionadas con las piezas del Tetris. `Linea()` , `Cuadrado()`, `Te()`, `Ese()`, `Zeta()`, `Jota()`, `Ele()`.
- **17/03/26 - Martes:** Implementar las funciones relacionadas con el movimiento de las piezas `izquierda()`, `derecha()`, `abajo` y `colision()`.
- **18/03/26 - Miércoles:** Por ultimo, las funciones de eliminación de filas y fin del juego. `eliminar_fila()` y `game_over()`.
- **10/03/26 - Jueves:** Grabación del vídeo
- **2'/03/26 - Viernes:** Documentación