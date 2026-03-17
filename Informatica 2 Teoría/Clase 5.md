# Introducción a puntero
Los punteros son variables. Mientras que en `Python`no hay mucha necesidad de definir claramente el tipo de dato, en `C++` si debe ser explicito el atributo de la misma (`int` , `float`, `char`, etc). Si ***los punteros son variables que almacenan direcciones de memoria*** deben tener un tipo de atributo en el momento de declaración, `*` llamado `Pointer` .

```cpp
#include <iostream>
using namespace std;

int main(){
	
	int a = 8;
	int b = 5;
	
	b = a + b; // Tengo la seguridad de que será 13, porque inicialice a y b

	int *pointer; // Declarando un entero apuntando a esa dirección de memoria
	cout << "Hello World!" << endl;
	return 0;
}
```
>***Recomendación:*** Siempre inicializa las variables, es probable que tenga un valor indeseado si no se hace.

Toda variable apunta a una dirección de memoria, donde para obtener esa dirección de memoria utilizamos `&`, tal que:
```cpp
#include <iostream>
using namespace std;

int main(){
	int a = 8;
	int b = 5;
	
	b = a + b;

	int *pointer = &a; // Utilizar el & para imprimir la dirección de memoria
	cout << "Hello World!" << endl;
	
	return 0;
}
```
> ***NOTA:*** Los punteros no pueden almacenar nada que no sea una dirección de memoria. No es posible hacer `*pointer = a` porque `a` no es una dirección de memoria. Mientras que si decimos `*pointer = &a` que imprimirá lo que hay en `a` 

Yo puedo saber a través del puntero que es lo que tiene una linea, tal que:
```cpp
#include <iostream>
using namespace std;

int main(){
	
	int a = 8;
	int b = 5;
	
	b = a + b;

	int *pointer = &a;
	
	cout << *pointer << endl; // Imprimer 8, no una dirección de memoria
	
	return 0;
}
```
Si digo `cout << *pointer << endl` entonces imprimirá lo que hay en `a`, pero si decimos `cout << pointer << endl` imprime la ***dirección de memoria*** de `a`
Si declaramos nuevamente el puntero más abajo entonces el valor de a cambiará, tal que:
```cpp
#include <iostream>
using namespace std;

int main(){
	int a = 8;
	
	int *pointer = &a;
	a = 20;
	*pointer = 10; // No importa que cambiará a antes, el valor será a = 10
		
	cout << *pointer << endl;
	cout << pointer << endl;
	cout << a << endl;
	
	return 0;
}
```
Siendo que la salida es:

![alt text](<../Material/Pasted image 20260316135626.png>)

Mientras que si comentamos la linea `pointer = 10;` entonces el valor será el `20` anteriormente declarado. Tal como se puede observar: 

![alt text](<../Material/Pasted image 20260316135800.png>)

## Arreglos
Un arreglo es una variable a la que se le puede almacenar varios datos del mismo tipo. Con un ejemplo cotidiano sería algo como
- Arreglo con temperaturas de cada día e un mes

| Temp | 10  | 12  | 16  | 20  | 18  | 14  | 15  | 10  | ... | 16  |
| ---- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

- Arreglo con los precios de cada uno de los productos

| Precios | 1700 | 850 | 2300 | 300 | 1000 | ... | 1800 |
| ------- | ---- | --- | ---- | --- | ---- | --- | ---- |

Solo que al definir un arreglo se debe de especificar la cantidad de espacios de memoria a resguardar, teniendo en cuenta que al igual que en `Python` se empieza desde `0`. Algo como`int Temp[30];` donde estoy creando un arreglo y le estoy diciendo que me guarde `30` espacios de memoria.
```cpp
#include <iostream>
using namespace std;

int main(){

	int temp[5]={3,4,5,6,7}; // Declaración de un arreglo y su forma de inicializar
	
	cout << temp[0] << endl; // Esta es la forma de acceder a una posición
	
	return 0;
}
```
Donde su salida evidentemente sería:

![alt text](<../Material/Pasted image 20260316175039.png>)

Mientras que si accedemos a la posición 4, tal que
```cpp
#include <iostream>
using namespace std;

int main(){

	int temp[5]={3,4,5,6,7}; 
	
	cout << temp[4] << endl; // Accediendo a la posición 4
	return 0;
}
```
La salida será:

![alt text](<../Material/Pasted image 20260316175143.png>)

Mientras que para imprimir todo lo que contiene el arreglo, la forma correcta de hacerlo sería:
```cpp
#include <iostream>
using namespace std;

int main(){

	int temp[5]={3,4,5,6,7};
	
	for(int i = 0; i < 5; i++){
		cout << temp[i] << endl; // Imprimiendo todas las posiciones del mismo
	}
	
	return 0;
}
```
Donde se ejecuta únicamente el bucle `for` la salida sería:

![alt text](<../Material/Pasted image 20260316175015.png>)

### Arreglos multidimensionales
Para crear una matriz se usan los arreglos  multidimensionales, que consisten en declararlo separando por una coma. Tal que:

```cpp
#include <iostream>
using namespace std;

int main(){

	int temp[5]={3,4,5,6,7};
	
	for(int i = 0; i < 5; i++){
		cout << temp[i] << endl; // Imprimiendo todas las posiciones del mismo
	}
	
	int matrizA[2][3] = {{1,2,3}, {4,5,6}}; // Una matriz
	
	for (int i = 0; i < 2; i++){
		for(j = 0; j < 3; j++){
			cout << matrizA[i][j] << " ";
		}
		cout << endl;
	}
	
	return 0;
}
```

## Funciones
La definición de una función consiste en un encabeza y un cuerpo. La estructura básica de definición de una función es:
```c++
tipo nombre([Lista de parámetros]){
	[declaraciones]
	instrucciones
	[return(expresión);]
}
```
La siguiente función usa dos parámetros de tipo entero y devuelve un valor de tipo entero
```cpp
int suma(int a, int b){
	int valor; // Declaración
	valor = a+b; // Instrucción
	return valor; // Retorno
}
```
