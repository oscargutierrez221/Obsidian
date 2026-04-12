# Clase 6: Introducción a la Programación Orientada a Objetos (POO)

## Indice

- [1. Tener en cuenta que](#1-tener-en-cuenta-que)
- [2. ¿Qué es la Programación Orientada a Objetos (POO)?](#2-qué-es-la-programación-orientada-a-objetos-poo)
    - [2.1 Importante:](#21-importante)
    - [2.2 Terminos a tener en cuenta:](#22-terminos-a-tener-en-cuenta)
- [3. Ventajas de la POO](#3-ventajas-de-la-poo)
- [4. Desventajaas de la POO](#4-desventajaas-de-la-poo)
- [5. Objeto y Clase](#5-objeto-y-clase)
    - [5.1 Ejemplo: Objeto y clases](#51-ejemplo-objeto-y-clases)
- [6. Conceptos importantes de la POO](#6-conceptos-importantes-de-la-poo)
    - [6.1 Conceptos básicos](#61-conceptos-básicos)
    - [6.2 Características](#62-características)
    - [6.3 Tipos de relaciones](#63-tipos-de-relaciones)
    - [6.4 Representaciones graficas](#64-representaciones-graficas)
- [7. Conceptos POO: Abstracción](#7-conceptos-poo-abstracción)
- [8. Conceptos POO: Encapsulamiento](#8-conceptos-poo-encapsulamiento)
- [9. Conceptos POO: Modularidad](#9-conceptos-poo-modularidad)
- [10. Ejemplos](#10-ejemplos-de-poo)
    - [10.1 Diferentes formas de instanciar un metodo](#101-ejemplo-1)
    - [10.2 Constructores y destructores](#102-constructor-y-destructor)

## 1. Tener en cuenta que

- Los programas suelen tener **varias soluciones posibles**

- En programación existen **distintos paradigmas** que nos ayudan a enfrentar un problema
- Cada **paradigma** tiene **diversos lenguajes** que las soportan.
    - Algunos lenguajes soportan varias metodologías, como `Python`, `C++`, `Java`, etc.
    

## 2. ¿Qué es la Programación Orientada a Objetos (POO)?

La programación orientada a objetos es un paradigma de programación que se basa en el concepto de "objetos", los cuales pueden contener datos en forma de campos (a menudo conocidos como atributos o propiedades), y código, en forma de procedimientos (a menudo conocidos como métodos).

En C++, la POO se implementa a través de clases y objetos.

### 2.1 Importante:

- Usamos **Objetos en lugar de tareas** como  bloque fundamental de análisis.

- Cada objeto es una **instancia** de una **Clase**, un elemento que pertenecee aa dicha categoria.

### 2.2 Terminos a tener en cuenta:

- **Clase**: Es un modelo o plantilla que define las características y comportamientos comunes de un grupo de objetos.
- **Objeto**: Es una instancia específica de una clase, con sus propios datos y comportamientos.
- **Atributo**: Es una característica o propiedad de un objeto.

- **Método**: Es una acción o comportamiento que un objeto puede realizar.
- **Declaro o instancio una variable**: Es el acto de crear una variable en memoria, lo que usualmente soliamos decir *"creo una variable"* en programación orientada  objetos se dice **Instanciar una variable**.

> Tener en cuenta que al **instanciar** una varible o una clase es lo mismo que decirle al sistema que te guarde un espacio en memoria para guardar los datos de esa variable o clase.

## 3. Ventajas de la POO

- Proximidad de los conceptos de la POO con los conceptos del **mundo real**.
- Facilita la **reutilización** y el **mantenimiento** del código.

- Se pueden usr **conceptos comunes** durante todas las fases del desarrollo: **definición de requerimientos**, **análisis**, **diseño** e **implementación**.
- Disipa la barreras entre el **que hace** y el **como lo hace**.
- Constribuye a darle mayor estructura (**arquitectura**) el software y mejora su seguridad.

## 4. Desventajaas de la POO

- Mayor **complejiddad** a la hora de entender el flujo de datos
    - Pérdida de linealidad
- Requiere de un **lenguaje** de modelado de problemas más elaborado:
    - **Unified Modeling Language (UML):** En este curso estudiaaremos una *versión simplificada* de UML.

    - **Representaaciones graficas**: y documentación más complejas.

## 5. Objeto y Clase

un **objeto** es un ente abstracto que podemos describir y manipular; tiene características y un comportamientos específico.

|Objeto: |=| Clase: |
|---|---|---|
| Atributo1:|=| valor1 | 
| Atributo2:|=| valor2 | 
| ... | ... | ... |
| AtributoN:|=| valorN |

Una **clase** describe los objetos del mismo tipo, los categoriza.
- Todos los objetos son **instancias** de una clase.
- Describe las **propiedades** y el **comportamiento** de un grupo de objetos

|Clase |
|---|
| Atributos |
| Métodos |

Una **clase** permite al programador definir un tipo de datos propio, que puede contener tanto datos (atributos) como comportamiento (métodos).

### 5.1 Ejemplo: Objeto y clases

|Objeto: |=| Clase: |
|---|---|---|
| camisa | | prenda de vestir |
| auto | | vehiculo |
| perro | | animal |

## 6. Conceptos importantes de la POO

### 6.1 Conceptos básicos
- Objeto

- Clase

### 6.2 Características
- Abstracción

- Encapsulamiento
- Modularidad
- Jerarquía

### 6.3 Tipos de relaciones
- Asociación
- Herencia

- Agregación o Composición
- Instanciación

### 6.4 Representaciones graficas

- Digramas estéticos (de clses, de objetos...)

- Digramas dinámicos (de secuencia, de colaboración...)

## 7. Conceptos POO: Abstracción
- Nos permite trabajr con la **complejidad del mundo real**.
    - Resaaltaqndo los aaspectos relevantes de los objetos que pertenecen a una clase, ocultando los detallles particulares de cada objeto.
- Separemos el **comportamiento** de la **implementación**, diferenciando **que se hace** en lugar de **como se hace**.

```
Un sensor de temperatura
    - Se define porque...
        - mide la temperatura
        - nos muestra su valor
        - se puede calibrar...
    - No sabemos... (no nos importa)
        - como mide la temperatura
        - de que esta hecho
        - como se calibra
```

## 8. Conseptos POO: Encapsulamiento
- **Ninguna paarte** de un sistema complejo **debe depender** de los detaalles internos de **otros**
- **Complementa** la abstracción.
- Se consigue:
    - **Separando** laa **interfaz** (nombre, parámetros, tipo de retorno) de la **implementación**.

    - **Ocultando** la **estructura** e **implementación** de los **métodos** (algoritmos que los implementan).
    - **Exponiendo** solo **la forma de interactuar** con el objeto (los métodos públicos).
    - Cada clase encapsula únicamente sus propias **propias responsabilidades**.

- El ocultamiento es fundaamental en la POO, permitiendo controlar el acceso a los miembros y métodos de una clase. Este acceso se debe restringir adecuadamente.

### 8.1 Metodos de acceso

- **Publicos**: Pueden ser accedidos desde cualquier lugar.
- **Privados**: Solo pueden ser accedidos desde la misma clase.

- **Protegidos**: Pueden ser accedidos desde la misma clase y desde las clases hijas.

## 9. Conceptos POO: Modularidad
- Consiste en separar el sistema en **bloques poco ligados** entre si: **Módulos**.
    - Organización del código en componentes.
- Representa un **encapsulamiento** del más alto **nivel**.
    - C++ no lo impone aunque los soporta (por ej: `namespaces`).
- Muy **importante en sistemas grandes**.

- ¿Cuántas módulos definir?, ¿Cuáles? y ¿Por qué?

## 10. Ejemplo:
Para definir una clase en C++ se utiliza la palabra reservada `class` seguida del nombre de la clase y un par de llaves que encierran la definición de la clase.

```cpp
class perro{};
```
Ahora, si deseamos definir un atributo de la clase perro, como por ejemplo su nombre, lo podemos hacer de la siguiente manera:

```cpp
class perro{
    int edad;
};
```
Como podemos ver, la clase perro tiene un atributo edad, que es de tipo int. Y, al poder copilar correctamente el programa, podemos decir que es posible acceder a el desde cualquier lugar, por lo que es publico.

Pero si decimos que

```cpp
main(){
    perro p;
    pincher.edad = 10;
}
```

no copilara porque la variable edad es privada. Porque no especificamos ningun metodo de acceso, por defecto es privada.

Si queremos que sea publica, debemos hacerlo de la siguiente manera:

```cpp
class perro{
    private:
        int edad;
};
```
Por lo general, los atributos de una clase deben ser privados, para que no puedan ser accedidos desde cualquier lugar.

Ahora si ejecutaramos la funcionn `main` nuevamente, copilaria sin errores

```cpp
int main(){
    perro pincher;
    pincher.edad = 10;
    cout << pincher.edad << endl;
    return 0;
}
```
Pero, si queremos controlar la edad entonces es necesrio instanciar un metodo que nos permita hacerlo, por ejemplo:

```cpp
class perro{
    private:
        int edad;
    public:
        void setEdad(int edad){
            edad = edad;
            }
};
```
Luego de instanciar el `setEdad` podemos modificar la edad del perro. Por ejemplo:

```cpp
int main(){
    perro pincher;
    pincher.setEdad(10);
    cout << pincher.edad << endl;
    return 0;
}
```
mas sin embargo, esto no copilara correctamente, ya que instancianciamos el metodo `setEdad` para poder manimpular la variable `edad`, pero no hemos intanciado el metodo necesario para mostrarla, es decir, el `getEdad`:

```cpp
class perro{
    private:
        int edad;
    public:
        void setEdad(int edad){
            edad = edad;
            }
        int getEdad(){
            return edad;
            }
};
```

Ahora debemos de hacer alguns modificaaciones a la funcion `main` para que ahorasi ejecutaramos, copilaria sin errores:

```cpp
int main(){
    perro pincher;
    pincher.setEdad(10);
    cout << pincher.getEdad() << endl;
    return 0;
}
```
Pero hay que tener cuidado al manejar el `set` y el `get`
- `set` es un metodo que se utiliza para establecer el valor de una variable.
- `get` es un metodo que se utiliza para obtener el valor de una variable.

> Nota que, en este ejemplo, al imprimir la edad en la pantalla entonces ponemos `getEdad()` y no `getEdad`. Esto se debe a que `getEdad` es un metodo, y como tal, debe ser llamado con parentesis.


### 10.1 Diferentes formas de instanciar los metodos `set` y `get`

Pero necesarimente no debemos de llamar a los metodos con `set` y `get`. Por ejemplo, podríamos tener un metodo que se llame `establecerEdad` y otro que se llame `obtenerEdad`. 

```cpp
class perro{
    private:
        int edad;
    public:
        void obtenerEdaad(int edad){
            edad = edad;
            }
        int establecerEdad(){
            return edad;
            }
};
```

Y de la misma manera usarlos en el `main`.

Como puedes ver, podemos instanciar los metodos `set` y `get` dentro de la clase, a lo que esto se llama **In line**. Pero, taambien podemos hacerlo fuera de la clase, de la siguiente manera:

```cpp
void perro::getEdad(){
    return edad;
}

void perro::setEdad(int nuevaEdad){
    edad = nuevaEdad;
}
```
Esta maneraa de poner los metodos fuera de la clase se llama **Out of line**. Es decir, que puedo poner las declaraciones de los metodos dentro de la clase y afuera de la clase poner las implementaciones de estas mismas. Con el ejemplo de los `set` y `get` entonces quedaria:

```cpp
class perro{
    private:
        int edad;
    public:
        void setEdad(int edad);
        int getEdad();
};

void perro::setEdad(int edad){
    edad = edad;
}

void perro::getEdad(){
    return edad;
}
```
Como puedes ver, instanciamos los metodos dentro de la clase, pero los codificamos afuera. Nota que, al instanciar los metodos fuera de la clase, debemos de poner el nombre de la clase seguido de dos puntos y el nombre del metodo. Por ejemplo: `perro::setEdad(int edad)`, a esos dos puntos se les conoce como operador `scope`, que en pocas palabras le dice al codificador que el metodo `setEdad` pertenece a la clase `perro`.

Vamor por partes:

```cpp
void perrro::setEdad(int edad){
    edad = edad;
}
```
- `void`: Es el tipo de retorno del metodo.
- `perro`: Es el nombre de la clase.
- `::`: Es el operador `scope`.
- `setEdad`: Es el nombre del metodo.
- `()`: Es el parámetro del metodo.
- `{}`: Es el cuerpo del metodo, es decir, donde se codificara el metodo.

Ya que tenemos todo esto, podemos decir que la clase `perro` tiene dos atributos: `edad` y `nombre`, y dos metodos: `setEdad` y `getEdad`. A pesar de ser largo y un poco mas complejo, es mas seguro y eficiente. Ahora que lo tenemos todo, entonces podemos usarlo para crear mas objetos de la clase `perro` tal que:

```cpp
int main(){
    perro pincher;
    perro lola;
    perro max;
    
    pincher.setEdad(10);
    lola.setEdad(5);
    max.setEdad(2);
    
    cout << pincher.getEdad() << endl;
    cout << lola.getEdad() << endl;
    cout << max.getEdad() << endl;
    
    return 0;
}
```

### 10.2 Constructor y destructor

El constructor es un metodo especial que se utiliza para inicializar los atributos de un objeto. Por ejemplo:

```cpp
perro::perro(){
    cout << "Creando la instancia de perro" << endl;
}
```

Como anteriormente en el `main` creamos 3 instancias de `perro` (pincher, lola, max) entonces se ejecutara 3 veces el constructor. Por lo tanto, la salida del programa sera 3 veces "Creando la instancia de perro". 

La importancia del constructor radica en que nos permite inicializar los atributos de un objeto en el momento de su creación. Como por definicion, el constructor es un metodo que permite inicializar los atributos de un objeto en el momento de su creación. Por ejemplo, si quisieramos que la edad inicie en 0, entonces podemos hacerlo de la siguiente manera:

```cpp
perro::perro(){
    edad = 0;
}
```
de tal forma que, si ejecutamos el `main` eliminando la creacion de los objetos pincher, lola y max entonces:

```cpp
int main(){
    cout << getEdad() << endl;
    return 0;
}
```
como la edad inicia en 0 y no hemos creado ningun objeto de la clase `perro` y tampoco hemos usado el `set` para modificaar la edad, entonces la salida del programa sera 0.


Por otro lado, el destructor es un metodo especial que se utiliza para eliminar los atributos de un objeto. Por ejemplo:

```cpp
perro::~perro(){
    cout << "Eliminando la instancia de perro" << endl;
}
```

> Nota que el destructor se diferencia del constructor en que tiene una tilde `~` antes del nombre de la clase.

Si usaramos esto en el `main` donde tenemos a los objetos pincher, lola y max, entonces la salida del programa seria 3 veces "Eliminando la instancia de perro". Y en ese momentol, los objetos pincher, lola y max dejan de existir. Es decir, que el destructor se ejecuta cuando el objeto deja de existir. Por lo tanto, el destructor es un metodo especial que se utiliza para eliminar los atributos de un objeto. O en otras palabras, se libera la memoria que ocupaba el objeto.

Entonces, en resumen el constructor permite inicializar los atributos de un objeto en el momento de su creacion y el destructor permite eliminar los atributos de un objeto en el momento de su destruccion.

> Es comun usar el destructor para liberar como memoria. Por ejemplo, si tuvieramos en el ambito privado `int *raza = new int` entonces en el destructor deberiamos de poner `delete[] raza` para liberar la memoria que ocupaba el objeto. Porque, al ser privado no podemos poner `delete[]` en el `main` porque pertenece al ambito privado. Y si no lo liberamos, entonces se producira una fuga de memoria.

