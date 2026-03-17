# Clase 3: De la Idea a la Ejecución y Fundamentos de C++
En esta clase exploraremos cómo se transforma el código que escribimos en algo que la computadora puede entender, y daremos nuestros primeros pasos en el lenguaje **C++**.

---
## 1. Introducción a la Producción (Ciclo de Compilación)
Cuando hablamos de "producir" software, nos referimos al proceso de transformar el código fuente (texto legible por humanos) en un archivo ejecutable (instrucciones para la CPU).
### El Flujo de Trabajo:
1. **Código Fuente:** Es el archivo `.cpp` que escribes.
2. **Preprocesador:** Limpia el código, expande macros y añade librerías (`#include`).
3. **Compilador:** Traduce el código C++ a **Lenguaje Ensamblador**.
4. **Ensamblador:** Traduce el código ensamblador a **Código Objeto** (binario no ejecutable).
5. **Enlazador (Linker):** Une tu código objeto con las librerías del sistema para generar el **Ejecutable** final.
---
## 2. Lenguaje de Máquina (El Idioma del Procesador)
El procesador (CPU) solo entiende **bits**: 0 y 1.
- Cada instrucción es una secuencia de números binarios que representan operaciones matemáticas (sumas, restas) o saltos de memoria.
- Es extremadamente difícil de leer para un humano, por eso inventamos lenguajes de mayor nivel.
---
## 3. Lenguajes de Programación
Podemos clasificar los lenguajes según su cercanía al hardware:
- **Bajo Nivel:** Lenguaje de Máquina y Ensamblador. Son muy rápidos pero difíciles de programar.
- **Alto Nivel:** C++, Java, Python. Usan palabras similares al inglés (`if`, `while`, `print`), lo que facilita la creación de software complejo.
### ¿Por qué C++?
C++ es considerado un lenguaje de "nivel medio/alto" porque permite manejar el hardware directamente (como la memoria) pero ofrece herramientas potentes de abstracción.

---
## 4. Sintaxis Básica de C++
Todo programa básico en C++ tiene esta estructura:
```cpp
#include <iostream> // Librería para entrada/salida
using namespace std; // Para no escribir std:: antes de cada comando

int main() { // Punto de inicio del programa
cout << "Hola Mundo"; // Imprime en pantalla
return 0; // Indica que el programa terminó correctamente
}
```
### Tipos de Datos Comunes
| Tipo     | Descripción                         | Ejemplo         |
| -------- | ----------------------------------- | --------------- |
| `int`    | Números enteros                     | `10`, `-5`      |
| `float`  | Números decimales simples           | `3.14f`         |
| `double` | Números decimales de alta precisión | `3.14159`       |
| `char`   | Un solo carácter                    | `'A'`, `'@'`    |
| `bool`   | Valores lógicos                     | `true`, `false` |
| `string` | Cadenas de texto                    | `"Hola"`        |
### Conectores y Operadores
1. **Aritméticos:** `+`, `-`, `*`, `/`, `%` (módulo o resto).
2. **Relacionales:** `==` (igual), `!=` (diferente), `>`, `<`, `>=` (mayor o igual) o `<=` (Menor o igual).
3. **Lógicos:** `&&` (Y), `||` (O), `!` (Negación).
4. **E/S:** `cout <<` (salida) y `cin >>` (entrada).
5. **Incremento/Decremento:** `++` (Aumenta) y `--` (Disminuye)
### Ejemplo Práctico: Operadores y Variables

```cpp
int a = 10;
int b = 3;
int suma = a + b;
int resto = a % b; // El resultado será 1
bool esMayor = (a > b); // El resultado será true
```
---
## 5. Ejemplo de Programa Completo: Calculadora de Área de Círculo
A continuación,un ejemplo que integra varios de los conceptos previos: variables, constantes, entrada/salida y operadores.
```cpp
#include <iostream>
using namespace std;

int main() {

// 1. Declaración de constantes y variables
const double PI = 3.14159265;
double radio, area;

// 2. Entrada de datos (cin)
cout << "¡Bienvenido al calculador de áreas!" << endl;
cout << "Ingresa el radio del círculo: ";
cin >> radio;

// 3. Proceso (Operadores aritméticos)
area = PI * (radio * radio);

// 4. Salida de datos (cout)
cout << "----------------------------------------" << endl;
cout << "El área del círculo con radio " << radio << " es: " << area << endl;
cout << "Gracias por usar nuestro programa ";

return 0; // Toda función tipo int debe de retornar algo. En este caso 0, indicando que finializo sin errores
}
```
### Explicación Paso a Paso:
1. **`const double PI`**: Usamos `const` para definir un valor que no cambiará durante la ejecución del programa. `double` nos permite tener mucha precisión decimal.
2. **`cout << ... << endl`**: `cout` envía texto a la pantalla. `endl` (end line) sirve para hacer un salto de línea.
3. **`cin >> radio`**: El programa se detiene y espera a que el usuario escriba un valor y presione Enter. Ese valor se guarda en la variable `radio`.
4. **`area = PI * (radio * radio)`**: Realizamos la operación matemática. El asterisco `*` representa la multiplicación.
5. **`return 0`**: Es la convención para decirle al sistema operativo que el programa finalizó exitosamente sin errores.

## 6. Operadores a Nivel de Bits (Bitwise)

  

Las operaciones a nivel de bits nos permiten manipular individualmente los bits (0s y 1s) que componen cualquier dato en la memoria. Son sumamente rápidas y se utilizan frecuentemente en sistemas de bajo nivel, desarrollo de videojuegos y optimización de memoria.

  

### Principales Operadores en C++:

1. **`&` (AND a nivel de bits):** Compara cada bit de dos números. El resultado es `1` solo si *ambos* bits son `1`.

2. **`|` (OR a nivel de bits):** El resultado es `1` si *al menos uno* de los bits es `1`.

3. **`^` (XOR / OR Exclusivo):** El resultado es `1` solo si los bits son *diferentes*.

4. **`~` (NOT a nivel de bits):** Operador unario que invierte todos los bits (`0` pasa a `1`, y `1` pasa a `0`).

5. **`<<` (Desplazamiento a la izquierda):** Mueve los bits hacia la izquierda. Cada desplazamiento equivale a multiplicar por 2.

6. **`>>` (Desplazamiento a la derecha):** Mueve los bits hacia la derecha. Cada desplazamiento equivale a dividir entre 2.
---
