# Clase 6: Introducción a la Programación Orientada a Objetos (POO)

## Tener en cuenta que

- Los programas suelen tener **varias soluciones posibles**
- En programación existen **distintos paradigmas** que nos ayudan a enfrentar un problema
- Cada **paradigma** tiene **diversos lenguajes** que las soportan.
    - Algunos lenguajes soportan varias metodologías, como `Python`, `C++`, `Java`, etc.
    

## ¿Qué es la Programación Orientada a Objetos (POO)?

La programación orientada a objetos es un paradigma de programación que se basa en el concepto de "objetos", los cuales pueden contener datos en forma de campos (a menudo conocidos como atributos o propiedades), y código, en forma de procedimientos (a menudo conocidos como métodos).

En C++, la POO se implementa a través de clases y objetos.

### Importante:

- Usamos **Objetos en lugar de tareas** como  bloque fundamental de análisis.
- Cada objeto es una **instancia** de una **Clase**, un elemento que pertenecee aa dicha categoria.

### Terminos a tener en cuenta:

- **Clase**: Es un modelo o plantilla que define las características y comportamientos comunes de un grupo de objetos.
- **Objeto**: Es una instancia específica de una clase, con sus propios datos y comportamientos.
- **Atributo**: Es una característica o propiedad de un objeto.
- **Método**: Es una acción o comportamiento que un objeto puede realizar.
- **Declaro o instancio una variable**: Es el acto de crear una variable en memoria, lo que usualmente soliamos decir *"creo una variable"* en programación orientada  objetos se dice **Instanciar una variable**.

> Tener en cuenta que al **instanciar** una varible o una clase es lo mismo que decirle al sistema que te guarde un espacio en memoria para guardar los datos de esa variable o clase.

## Ventajas de la POO

- Proximidad de los conceptos de la POO con los conceptos del **mundo real**.
- Facilita la **reutilización** y el **mantenimiento** del código.
- Se pueden usr **conceptos comunes** durante todas las fases del desarrollo: **definición de requerimientos**, **análisis**, **diseño** e **implementación**.
- Disipa la barreras entre el **que hace** y el **como lo hace**.
- Constribuye a darle mayor estructura (**arquitectura**) el software y mejora su seguridad.

## Desventajaas de la POO

- Mayor **complejiddad** a la hora de entender el flujo de datos
    - Pérdida de linealidad
- Requiere de un **lenguaje** de modelado de problemas más elaborado:
    - **Unified Modeling Language (UML):** En este curso estudiaaremos una *versión simplificada* de UML.
    - **Representaaciones graficas**: y documentación más complejas.

## Objeto y Clase

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

### Por ejemplo: Objeto y clases

|Objeto: |=| Clase: |
|---|---|---|
| camisa | | prenda de vestir |
| auto | | vehiculo |
| perro | | animal |

## Conceptos importantes de la POO

### Conceptos básicos
- Objeto
- Clase

### Características
- Abstracción
- Encapsulamiento
- Modularidad
- Jerarquía

### Tipos de relaciones
- Asociación
- Herencia
- Agregación o Composición
- Instanciación

### Representaciones graficas

- Digramas estéticos (de clses, de objetos...)
- Digramas dinámicos (de secuencia, de colaboración...)

## Conceptos POO: Abstracción
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

