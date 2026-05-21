# Punteros

Un puntero es simplemente una variable que contiene la direccion de memoria de otra variable. Para trabajar con punteros se utilizan los operadores `&` y `*`.

**Operador &:** Direccion de memoria
**Operador *:** Valor de la variable

```cpp
int main(){
    std::string nombre = "David";
    std::string *pNmbre = &nombre;

    std::cout << pNmbre;

    return 0;
}
```
En este ejemplo tenemos:
- `nombre` nuestra variable
- Y luego creamos un puntero `*pNombre` que almacena la direccion de memoria de `nombre`.
- Finalmente, cuando hacemos `std::cout << pNmbre;` estamos imprimiendo la direccion de memoria de la variable `nombre`.
- Mientras que si quisieramos imprimir el valor de `nombre` simplemente tendriamos que poner el `*` antes del puntero: `std::cout << *pNombre;`

Para el siguiente ejemplo:
```cpp
int main(){
    std::string nombre = "David";
    int edad = 18;

    std::string *pNmbre = &nombre;
    int *pEdad = &edad;

    std::cout << pNmbre;
    std::cout << *pNombre;

    std::cout << pEdad;
    std::cout << *pEdad;

    return 0;
}
```
En este nuevo ejemplo tenemos:
- El mismo ejemplo anterior de `nombre`
- Y una nueva variable `edad` y un nuevo puntero `*pEdad` que almacena la direccion de memoria de `edad`. 
- Luego, al final del código, hacemos un `std::cout` de los dos punteros y de los dos valores, tanto la direccion de memoria, como el valor de la variable.

Nuevo ejemplo:
```cpp
int main(){
    std::string nombre = "David";
    int edad = 18;

    std::string pizzasGratis[5] = {"pizza1","pizza2","pizza3","pizza4","pizza5"};

    std::string *pNmbre = &nombre;
    int *pEdad = &edad;
    std::string *pPizzas = pizzasGratis;

    std::cout << pNmbre;
    std::cout << *pNombre;

    std::cout << pEdad;
    std::cout << *pEdad;
    std::cout << pizzasGratis;
    
    return 0;
}
```

- Notase que en este ultimo ejemplo hemos anadido el array de 5 elementos `pizzasGratis`
- Y cuando hacemos `std::cout << pizzasGratis;` estamos imprimiendo la direccion de memoria del array
- porque no `*pizzasGratis`? porque el copilador me dara un error al intentarlo imprimir y por eso con arreglos basta con escribir simplemente el nombre del arreglo.

## Punteros dobles

Se puede definir como un puntero que apunta a la direccion de memoria de otro puntero.
Para utilizarlo con matrices bidimencionales, es decir, matrices de matrices, hacemos lo siguiente:
```cpp
int main(){
    int filas = 3;
    int columnas = 3;

    int** matriz = new int* [filas];

    for (int i = 0; i < filas; i++){
        matriz[i] = new int [columnas];       
    }
}
```
Puede parecer un poco complicado, pero en realidad no lo es. Vamos por partes:

- Primero declaramos nuestras variables de `filas` y `columnas` y las inicializamos en `3`.
- Luego declaramos una variable `matriz` de tipo que recordando que para uso de matrices es necesario un puntero doble, declaramos `int**` de tipo entero y lo terminamos de declarar con memoria dinamica haciendo referencia a las filas `new int* [filas]`.
- Seguido a eso, es necesario utilizar un bucle for para asignar memoria a cada fila de la matriz, es decir, `matriz[i] = new int [columnas];`

Pero nos falta algo importante y es que no podemos olvidar liberar la memoria que hemos asignado. Para este caso, es necesario hacerlo en el orden correcto.

```cpp
int main(){
    int filas = 3;
    int columnas = 3;

    int** matriz = new int* [filas];

    for (int i = 0; i < filas; i++){
        matriz[i] = new int [columnas];       
    }
}

// Liberar memoria
for (int i = 0; i < filas; i++){
    delete[] matriz[i];
}
delete[] matriz;
```
## Memoria dinamica

Memoria dinamica es aquella que se asigna durante la ejecucion del programa. Para asignar algun valor en la memoria dinamica es necesari utilizar la palabra reservada `new`.

Por ejemplo:
```cpp
int main(){
    int *pNum = NULL; // Creo un puntero sin valor

    pNum = new int; // Asigno memoria dinamica al puntero

    *pNum = 25; // Asigno valor

    std::cout << "Direccion: " << pNum << std::endl; // Imprimo la direccion de memoria
    std::cout << "Valor: " << *pNum << std::endl; // Imprimo el valor

    delete pNum; // Libero memoria con el operador de eliminacion delete

    return 0;
}
```

Segundo ejemplo:
```cpp
int main(){
    char* pNotas = NULL;
    int tam;

    std::cout << "Cuantas notaqs ingresara?: ";
    std::cin >> tam;

    pNotas = new char [tam];

    for (int i = 0; i < tam; i++){
        std::cout << "Ingrese una nota " << i + 1 << ":";
        std::cin >> pNotas[i];   
    }

    for (int i = 0; i < tam; i++){
        std::cout << pNotas[i] << " ";
    }

    delete[] pNotas;

    return 0;
}
```

### Explicación del Segundo Ejemplo: Gestión Dinámica de Memoria

Este ejemplo es un caso clásico de **Gestión Dinámica de Memoria** en C++. La clave aquí es que no sabemos cuántas notas vamos a guardar hasta que el programa ya se está ejecutando (en tiempo de ejecución), no cuando lo escribimos.

#### 1. Preparación del terreno
```cpp
char* pNotas = NULL;
int tam;
```
* **`char* pNotas`**: Creas un puntero. Piensa en esto como una "flecha" que por ahora no apunta a nada (`NULL`). Su único trabajo será recordar la dirección de donde empiece nuestra lista de notas.
* **`int tam`**: Una variable normal para guardar el número que el usuario decida.

#### 2. El momento de la "Reserva" (Dinámica)
```cpp
std::cin >> tam;
pNotas = new char [tam];
```
Esta es la parte más importante. 
* A diferencia de hacer algo como `char notas[10];` (que es estático y fijo), aquí usas **`new`**. 
* El programa va a la memoria (al *Heap*) y dice: *"Necesito espacio para exactamente `tam` caracteres"*. 
* **`pNotas`** ahora guarda la dirección del primer bloque de ese espacio. Ahora el puntero ya no es `NULL`, apunta a tu nuevo arreglo.

#### 3. Uso del arreglo (Como si fuera uno normal)
```cpp
for (int i = 0; i < tam; i++){
    std::cin >> pNotas[i];   
}
```
Aunque `pNotas` es un puntero, C++ te permite usar los corchetes `[]` para moverte por él. Es como decir: *"Ve a la dirección que tiene `pNotas` y muévete `i` posiciones hacia adelante"*.

#### 4. La "Limpieza" Obligatoria
```cpp
delete[] pNotas;
```
Como tú pediste ese espacio manualmente con `new`, el sistema operativo no lo recuperará automáticamente cuando la función termine. 
* **`delete[]`**: Es el comando para decir: *"Ya terminé de usar este bloque de memoria, puedes dárselo a otro proceso"*.
* Si olvidas esto, tendrías un **Memory Leak** (fuga de memoria), que es como dejar luces encendidas en una casa donde ya no vive nadie.

**En resumen:**
Este código es un ciclo de vida completo de memoria dinámica: 
1. **Apuntas** (`char*`), 
2. **Pides** (`new`), 
3. **Usas** (`pNotas[i]`) 
4. **Devuelves** (`delete[]`).

## Stack
Es donde se guardan las variables 