# Clase 4: Aproximaciones al lenguaje
## Recordemos: Estructura básica de un programa en C++
Todo programa en C++ sigue una estructura fundamental:
```cpp
#include <iostream> // Librería para mostrar información en pantalla
using namespace std; // Evita escribir "std::" antes de cada instrucción

int main() { // Función principal del programa
cout << "Hello World" << endl;

return 0; // La función main es de tipo int, por lo que debe retornar un valor
}
```
### Ejemplo: Cálculo de potencias
Usando la librería `math.h`
```cpp
#include <iostream>
#include <math.h> // Libreria nueva
using namespace std;

int main() {
int a = 2;
int b = 3;

cout << "Potencia: " << pow(a, b) << endl; // 2^3 = 8

return 0;
}
```

> ⚠️ **Ten en cuenta:** Cuantas más librerías incluyas, mayor será el tamaño del programa y, por lo tanto, menor su velocidad de respuesta.

**Sin librerías externas:** usando un ciclo for es posible calcular una potencia sin usar `math.h`, implementando la multiplicación de forma manual:

```cpp
#include <iostream>
using namespace std;

int main() {
int a = 2; // Base
int b = 3; // Exponente
int c = a; // Variable que acumulará el resultado

for (int i = 1; i < b; i++) {
	c *= a; // Multiplica c por a en cada iteración
}
cout << "Potencia: " << c << endl; // 2^3 = 8

return 0;
}
```
Al eliminar la dependencia de `math.h`, el programa se vuelve más ligero y eficiente.
> ⚠️ **¿Cuándo usar librerías?** Las librerías contienen una gran cantidad de código, lo que aumenta el peso del programa. Sin embargo, esto no significa que deban evitarse siempre. Cuando solo necesitas una función específica, puedes importar únicamente esa función usando `namespace`, en lugar de cargar toda la librería.
## Variables Globales en C++
Una variable global es aquella que se declara fuera de cualquier función, lo que la hace accesible desde cualquier parte del programa.
```cpp
#include <iostream>
using namespace std;

int contador = 0; // ✅ Variable GLOBAL (declarada fuera de main)
void incrementar() {
contador++; // Puede accederse desde cualquier función
}

int main() {

incrementar();
incrementar();
cout << contador << endl; // Imprime: 2

return 0;

}

```
En contraste, una variable local solo existe dentro de la función donde fue declarada:
```cpp
int main() {
int contador = 0; // Variable LOCAL, solo existe aquí
return 0;
}

```
**¿Por qué NO se recomienda usarlas?**
1. 🧩 **Dificultan el entendimiento del código:**

Cuando una variable puede ser modificada desde cualquier función, es difícil rastrear quién la cambia y cuándo.

2. 🐛 **Generan errores difíciles de detectar:**

Si dos funciones modifican la misma variable global sin coordinación, el comportamiento del programa se vuelve impredecible.
```cpp
int valor = 10;
void funcionA() { valor = 5; } // La modifica
void funcionB() { valor *= 2; } // También la modifica
// ¿Cuál se ejecutó primero? El resultado cambia según el orden.
```

3. 🔁 **Crean dependencias ocultas:**

Las funciones dejan de ser independientes para dependen de un estado externo que no controlan, lo que hace el código difícil de reutilizar y probar.

4. 💾 **Ocupan memoria durante toda la ejecución:**

Las variables globales viven desde que el programa inicia hasta que termina, a diferencia de las locales que se liberan al salir de su función.

✅ **Alternativa recomendada**
En lugar de variables globales, pasa los datos como parámetros a las funciones:

```cpp
void incrementar(int& contador) { // Recibe la variable por referencia
contador++;
}

int main() {

int contador = 0; // Variable local controlada
incrementar(contador);
cout << contador << endl; // 1

return 0;

}

```

>⚠️ **Regla general:** Si sientes la necesidad de usar una variable global, es una señal de que tu programa necesita mejor diseño. Casi siempre existe una forma de pasar esa información como parámetro.
## Estructuras de Control en C++

1. **Condicionales:** `if / else`

Permiten ejecutar un bloque de código solo si se cumple una condición.
```cpp
#include <iostream>
using namespace std;

int main() {
int nota = 75;

if (nota >= 90) {
	cout << "Excelente" << endl;
	} 
	else if (nota >= 60) {
		cout << "Aprobado" << endl; // ← Se ejecuta este
	} 
	else {
		cout << "Reprobado" << endl;
	}
return 0;

}

```

| Operadores de comparación | Significado                   |
| ------------------------- | ----------------------------- |
| `==`                      | Igual a                       |
| `!=`                      | Diferente de                  |
| `> / <`                   | Mayor / Menor que             |
| `>= / <=`                 | Mayor o igual / Menor o igual |

2. **`switch` con `do-while`**

***`switch`***

Evalúa una variable y ejecuta el caso que coincida. Es más limpio que muchos `if-else` cuando comparas un mismo valor contra varias opciones.

***`do-while`***

Ejecuta el bloque al menos una vez y luego repite mientras la condición sea verdadera. A diferencia del `while`, la condición se evalúa al final.

Siendo que ambos juntos pueden ejecutar un menu que se repita infinitamente: Solicite una opción, ejecute una función y solicite una opción nuevamente. Tal que:

```cpp
#include <iostream>
using namespace std;

int main() {
int opcion;

do {
// El menú se muestra AL MENOS una vez
cout << "=== MENÚ ===" << endl;
cout << "1. Saludar" << endl;
cout << "2. Despedirse" << endl;
cout << "0. Salir" << endl;
cout << "Opción: ";
cin >> opcion;

switch (opcion) {
	case 1:
		cout << "¡Hola!" << endl;
		saludar(); // Una función que se ejecuta al usuario ingresar "1"
		break; // Sin break, caería al siguiente caso
	case 2:
		cout << "¡Adiós!" << endl;
		despedirse();
		break;
	case 0:
	cout << "Saliendo..." << endl;
		break;
	default: // Si ningún caso coincide
		cout << "Opción no válida." << endl;
	}
} while (opcion != 0); // Repite hasta que el usuario elija 0, si no se ingreso 0 entonces se vuelve a repetir desde el menu

return 0;

}
```
> ⚠️ **Importante:** El `break` dentro del `switch` es obligatorio al final de cada caso. Sin él, el programa continúa ejecutando los casos siguientes aunque no coincidan (comportamiento llamado "`fall-through`").

3. **Bucle `for`**

Ideal cuando sabes de antemano cuántas veces quieres repetir algo. La estructura de un `for` es: `for (inicio; condición; actualización)`.

En un uso practico:

```cpp

#include <iostream>
using namespace std;

int main() {
// Imprime los números del 1 al 5
for (int i = 1; i <= 5; i++) {
cout << i << " ";
}
// Salida: 1 2 3 4 5
return 0;

}
```
**Desglose de las tres partes:**

| Parte         | En el ejemplo | Descripción                           |
| ------------- | ------------- | ------------------------------------- |
| Inicio        | `int i = 1`   | Se ejecuta una sola vez al comenzar   |
| Condición     | `i <= 5`      | Se evalúa antes de cada iteración     |
| Actualización | `i++`         | Se ejecuta al final de cada iteración |

**Ejemplo práctico:** tabla de multiplicar

```cpp
int n = 5;
for (int i = 1; i <= 10; i++) {
cout << n << " x " << i << " = " << n * i << endl;
}
```
**Resumen rápido**

| Estructura  | Úsala cuando...                               |
| ----------- | --------------------------------------------- |
| `if / else` | La condición es compleja o compara rangos     |
| `switch`    | Comparas una variable contra valores fijos    |
| `for`       | Sabes cuántas iteraciones necesitas           |
| `do-while`  | Necesitas ejecutar el bloque al menos una vez |