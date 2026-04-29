# Clase 9 - Sobrecarga y Constructores Especiales

La sobrecarga es un pilar fundamental en C++ que permite definir múltiples comportamientos para un mismo nombre (ya sea de función o de operador), facilitando la legibilidad y el uso del código.

---

## 1. Sobrecarga de Funciones

Consiste en crear diferentes funciones con el mismo nombre, con el fin de ofrecer al usuario una manera más sencilla de interactuar con el programa sin tener que recordar nombres distintos para tareas similares.

### Definición General
```cpp
TipoRetorno nombreFuncion(ListaParametros_1);
TipoRetorno nombreFuncion(ListaParametros_2);
TipoRetorno nombreFuncion(ListaParametros_3);
// ...
TipoRetorno nombreFuncion(ListaParametros_n);
```

> [!IMPORTANT]
> Para que la sobrecarga sea válida, la **firma** de la función debe ser única. Esto significa que, aunque el nombre sea el mismo, la `ListaParametros` debe variar en **número** o **tipo** de datos. El tipo de retorno por sí solo no basta para diferenciar una función de otra.

### Resolución de Sobrecarga (Overload Resolution)
Cuando invocamos una función sobrecargada, el **compilador** decide cuál utilizar mediante un proceso de selección basado en las siguientes reglas de precedencia:

1. **Concordancia exacta**: El número y tipo de argumentos coinciden perfectamente con la declaración.
2. **Promociones triviales**: Conversiones automáticas de tipos asimilables (ej. `char`, `short` o `bool` pasan a `int`).
3. **Conversiones estándar**: Transformaciones de tipos básicos (ej. de `int` a `double`).
4. **Conversiones definidas por el usuario**: Conversiones mediante constructores o operadores de conversión propios.

---

## 2. Sobrecarga de Métodos en Clases

Dentro de una clase, los métodos también pueden sobrecargarse para ofrecer flexibilidad en el comportamiento del objeto.

### Ejemplo: Clase `carro`
```cpp
class carro {
    private:
        int gGas;
        char* Marca;
        int velMax;
        int vel;
        bool start;
    public:
        carro(); // Constructor por defecto
        void arrancar();
        
        // --- Métodos Sobrecargados ---
        void acelerar();                // Aceleración estándar
        void acelerar(int increment);   // Aceleración personalizada
        
        void frenar();
        int getVel() const;
        ~carro(); // Destructor (No se puede sobrecargar)
};
```

#### Implementación de la sobrecarga:
```cpp
void carro::acelerar() {
    if (--gGas <= 0) {
        vel = 0;
    } else {
        vel++;
    }
}

void carro::acelerar(int increment) {
    if (--gGas <= 0) {
        vel = 0;
    } else {
        vel += increment;
    }
}
```

> [!TIP]
> Aunque comparten nombre, el compilador las distingue por la presencia o ausencia del parámetro `increment`. 
> **Nota:** El **destructor** es único; no puede recibir parámetros ni ser sobrecargado.

---

## 3. El Constructor Copia

El **constructor copia** es un constructor especial que el compilador provee por defecto si nosotros no definimos uno. Se invoca automáticamente cuando necesitamos crear un objeto nuevo basándonos en uno ya existente.

### Ejemplo de uso:
```cpp
#include <iostream>
using namespace std;

// Instancia original
carro Deportivo(10, "BMW", 50);

// Se crea 'carreras' usando el constructor copia
carro carreras(Deportivo); 

int main() {
    cout << "Velocidad Deportivo: " << Deportivo.getVel() << endl;
    cout << "Velocidad Carreras: " << carreras.getVel() << endl;
}
```

### ¿Cómo funciona realmente? (Shallow vs Deep Copy)

El constructor que provee el compilador por defecto realiza una **copia superficial** (*shallow copy*). Esto significa que copia los valores de los atributos bit a bit del objeto original al nuevo.

#### El problema con los punteros:
En nuestra clase `carro`, tenemos el atributo `char* Marca`.
1. El objeto `Deportivo` tiene una dirección de memoria donde vive el texto "BMW".
2. El objeto `carreras`, al ser una copia superficial, recibe **exactamente la misma dirección de memoria**.
3. **Resultado:** Ambos objetos "comparten" el mismo nombre en memoria.

## Valores por defecto

En el codigo anterior uno de los constructores tiene argumentos de entrada planteados por defecto

```cpp
carro(int _gGas, char* _marca ="mazda", int_velMax = 80);
```

Invocaciones como la siguiente resolveran con el valor por defecto

```cpp
carro Deportivo(10, "Renaul");
```

Considere que otros tipos de sintaxis darian error

```cpp
carro Deportivo (10,,50); //MAL
carro Deportivo (10, "Renaul"); //OK
carro Deportivo (10); //OK
```

Esto tiene sus ventajas.

**Ventajas:**

- **Menos código que escribir:** No necesitamos escribir un constructor para cada caso.
- **Menos código que mantener:** Si necesitamos cambiar la lógica de los argumentos por defecto, solo lo hacemos en un lugar.
- **Menos código que depurar:** Si hay un error en los argumentos por defecto, solo lo depuramos en un lugar.

O en palabras simples, si tenemos un constructor que acepta muchos argumentos de entrada, podemos usar argumentos por defecto para que el constructor sea mas flexible, es decir, si son 5 entonces simplemente ingreso 2 y los otros 3 toman el valor por defecto previamente declarado.

## Sobrecarga de Operadores

La sobrecarga de operadores permite redefinir algunos de los operadores existentes en C++ para que actuen de una determinada manera.

Cuando sobrecargamos cualquier operador nos referimos a cambiar su funcionalidad pero no su gramatica original. Por ejemplo:

- Suma: `a+b` vs `a+`
- Asignacion: `a = a+b` vs `a + b = a`

> Operadores: `+,-,*,/,=,++,--,...`

Estamops haciendo uso de funciones con identificadores (nombres) especiales

- `+` --> `operator+`
- `-` --> `operator-`
- `*` --> `operator*`
- `/` --> `operator/`
- `=` --> `operator=`
- `++` --> `operator++`
- `--` --> `operator--`

Es decir que para sobrecargar un operador simplemente es necesario definir una funcion con el identificador especial "operator" seguido del operador a sobrecargar. Por ejemplo, si queremos sobrecargar el operador `+`, debemos definir una funcion llamada `operator+`.

> No se pueden sobrecargar: `.` (operador miembro), `::` (operador de resolución de ámbito), `?:` (operador condicional) y `sizeof` (operador sizeof), etc.

La sobrecarga de operador puede ser declarada de la siguiente forma:

```cpp
TipoRetorno PalabraReservada(operator) operador (parametros);
```

Por ejemplo

```cpp
float operator* (float x);
```

1. `float`: Es el tipo de dato que retorna la funcion.
2. `operator*`: Es la palabra reservada.
3. `*`: El operador a sobrecargar.
4. `(float x)`: Es el palametro

***Ejemplo:***

Suponiendo que tenemos tres objetos de una misma clase: `c1`, `c2`, `c3`

```cpp
c3 = c1.sumar(c2);
```

Seria mas sencillo utilizar la sobrecarga de operadores:

```cpp
c3 = c1 operator+(c2);

c3 = c1 + c2; //Forma mas sencilla
```

La sintaxis `c3 = c1 + c2` es mas limpia y legible. Ademas, es mas comoda de utilizar porque no necesitamos escribir la palabra reservada `operator` cada vez que queremos utilizar el operador.

El obetivo de la osbrecarga de operadores es simplificar al maximo el codigo a implementar.

> Sobrecarga de operadores unarios: `+=`, `-=`, `^=`, etc.
> Por ejemplo: `i++`, `i--`, `++i`, `--i`, `+x`, `-x`, `!x`, `~x`, `&x`, `*x`, `sizeof(x)`

***Sobrecarga de operador de pre incremento***

```cpp
ClassX ClaseX::operator++(){
    x=x+2; //datos miembro de la clase ClaseX
    Y=Y+4;

    return *this;
}
```

> El puntero **`this`**: En C++, **`this`** es un puntero especial que existe dentro de cada función miembro. 
> Su propósito es **apuntar al objeto** para el cual se está invocando el método. 
> Por lo tanto, **`*this`** se refiere al **objeto actual**.