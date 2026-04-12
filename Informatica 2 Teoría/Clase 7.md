# Continuación Clase 6: Programación Orientada a Objetos (POO)

## Recordemos
Tengamos en cuenta que el codigo de la clase anterior es el siguiente:

```cpp

class perro{
    private:
        int edad;
        int *raza = new int;
    public:
        perro(int numero);
        int getEdad() const;
        void setEdad(int newEdad);
        ~perro();
};

int main(){
    perro pincher(3);
    perro pastor(6);

    pincher.setEdad(10);
    pastor.setEdad(2);

    cout << pincher.getEdad() << endl;
    cout << pastor.getEdad() << endl;

    return 0;
}

perro::perro(int numero){
    edad = numero;
    raza = new int;
}

int perro::getEdad() const{
    return edad;
}

void perro::setEdad(int newEdad){
    edad = newEdad;
}

perro::~perro(){
    cout << "Se elimina el objeto" << endl;
    delete raza;
}
```

Teniendo en cuenta este codigo que veniamos trabajando entonces vamos a ver como se puede mejorar o como podemos aplicar los conceptos de la POO de la clase 6 ya sea para modificarlo o añadirle cosas.

## 1. Modificar el codigo para afianzar los conceptos de la POO de la Clase 6

Empecemos anadiendo unas cuantos metodos y atributos a la clase perro:

```cpp
class perro{
    private:
        int edad;
        int *raza = new int;
    public:
        perro(int numero);
        int getEdad() const;
        void setEdad(int newEdad);
        int saludar(int n_veces);
        void comer(float cantidad);
        void pelear();
        ~perro();
};
```
Como podemos observar, a la clase `perro` le hemos instanciado nuevos metodos, `int saludar(int n_veces)`, `void comer(float cantidad)` y `void pelear()`. Ya que siguiendo todo lo mencionado anteriormente, puedo instanciar los metodos y atributos que crea correcto.

Una vez despues de instanciar los metodos y atributos a la clase, es necesario implementar esas 3 funciones, porque asi como las tenemos ahora no hacen nada, solo estan instanciadas.

Es decir, que si pusieramos eso en el `main`

```cpp
int main(){
    perro pincher(3);
    perro pastor(6);

    pincher.setEdad(10);
    pastor.setEdad(2);

    paastor.saludar(4);

    cout << pincher.getEdad() << endl;
    cout << pastor.getEdad() << endl;

    return 0;
}
```

Aqui estoy declarando la instancia de saludar de forma correcta de acuerdo a las reglas de sintaxis de C++, pero como no he implementado nada al metodo, entonces me dira error. Por lo que es necesario hacer eso:

```cpp
perro::perro(int numero){
    edad = numero;
    raza = new int;
}

int perro::getEdad() const{
    return edad;
}

void perro::setEdad(int newEdad){
    edad = newEdad;
}

void perro::saludar(int n_veces){
    for (int i = 0; i < n_veces; i++){
        cout << "Guau" << endl;
    }
}

perro::~perro(){
    cout << "Se elimina el objeto" << endl;
    delete raza;
}
```

De esta forma el `main` ya no deberia de dar ningun problema, porque ya hemos implementado el metodo correctamente y lo hemos llamado en el `main`de forma correcta tambien. Entonces podemos:

```cpp
int main(){
    perro pincher(3);
    perro pastor(6);

    pincher.setEdad(10);
    pastor.setEdad(2);

    pincher.saludar(2);
    pastor.saludar(4);

    cout << pincher.getEdad() << endl;
    cout << pastor.getEdad() << endl;

    return 0;
}
```
Y copilara sin errores. Ya si deseamos implementar el resto de los metodos:

```cpp
perro::perro(int numero){
    edad = numero;
    raza = new int;
}

int perro::getEdad() const{
    return edad;
}

void perro::setEdad(int newEdad){
    edad = newEdad;
}

void perro::saludar(int n_veces){
    for (int i = 0; i < n_veces; i++){
        cout << "Guau" << endl;
    }
}

void perro::comer(float cantidad){
    cout << "El perro come " << cantidad << " kg de comida" << endl;
}

void perro::pelear(){
    cout << "El perro pelea" << endl;
}

perro::~perro(){
    cout << "Se elimina el objeto" << endl;
    delete raza;
}
```

Y si queremos llamarlos al `main`:

```cpp
int main(){
    perro pincher(3);
    perro pastor(6);

    pincher.setEdad(10);
    pastor.setEdad(2);

    pincher.saludar(2);
    pastor.saludar(4);

    pincher.comer(0.5);
    pastor.comer(1.2);

    pincher.pelear();
    pastor.pelear();

    cout << pincher.getEdad() << endl;
    cout << pastor.getEdad() << endl;

    return 0;
}
```
Y copilara sin ningun error.

> NOTA: Lo recomendado es que la instanciasion de la clase, como los metodos y atributos esten en archivos de cabecera de terminacion `.h` y la implementacion de los metodos en archivos de terminacion `.cpp` del mismo archivo de cabecera e incluir al archivo `main.cpp` los archivos de cabecera con `#include "nombre_archivo.h"`.

### Ejercicio propuesto

Par poder afianzar los conceptos de la POO se propone el siguiente ejercicio:

- **Tema:** La digestion

- **Requerimientos:** Para el desarrollo de este es necesario que haga uso de los conceptos de la POO vistos en la clase anterior.
    - Comer alimentos por la boca
    - Tragar alimento por la boca

    - Digerir en el estomago

Algunas pistas que te pueden ayudar a empezar a resolver este ejercicio son estas dos clases:

```cpp
class alimento{
    private:
        string nombre;
    public:
        alimento(string _nombre);
        string getNombre() const;
        bool transformar();
};

class boca{
    private:
        float capacidad;
        float capacidad_actual;
    public:
        boca(float _capacidad); 
        
        bool masticar(alimento generico, float cantidad);
};
```
Aquí estamos declarando dos clases: `alimento` y `boca`. 
Nota cómo el método `masticar` de la clase `boca` recibe por parámetro un objeto de tipo `alimento` llamado `comida_a_masticar`. ¡Esta es la forma habitual en la que los objetos de diferentes clases pueden interactuar entre sí!

Por ahora, solo tenemos las **declaraciones** dentro de las clases. Para que esto funcione completamente, necesitamos **implementar** esos métodos ("Out of line") como aprendimos. Por ejemplo, el constructor de `boca` podría implementarse así:

```cpp
boca::boca(float _capacidad){
    capacidad = _capacidad;
    capacidad_actual = _capacidad;
}

alimento::alimento(string _nombre) {
    nombre = _nombre;
}

string alimento::getNombre() const {
    return nombre;
}

bool boca::masticar(alimento generico, float cantidad){
 if(capacidad_actual >= cantidad) {
    capacidad_actual = capacidad_actual - cantidad;
    cout << "Masticando" << generico.getNombre() << endl; 
    return true;
    }
    if (capacidad_actual < cantidad && capacidad_actual > 0) {
        cout << "Masticando " << generico.getNombre() << " parcialmente, solo se puede masticar " << capacidad_actual << endl;
        capacidad_actual = 0;
        return true;
    }
    else {
        cout << "No se puede masticar " << cantidad << " del alimento " << generico.getNombre() << endl;
        return false; 
    }

}
```

Teniendo eso, en tu `main` ya podrías ir creando ("instanciando") los objetos y probarlos:

```cpp
int main(){
    alimento frutas("manzana");
    alimento vegetal("lechuga");
    alimento tuberculo("arracacha");
    boca grande(100);

    grande.masticar(frutas, 10);
    grande.masticar(frutas, 10);
    grande.masticar(vegetal, 10);
    grande.masticar(tuberculo, 10);

    return 0;
}
```

De esta forma, puede parecer bastante complicado de entender porque están pasando muchas cosas. Entendamos el flujo completo de este código viéndolo paso por paso:

1. **Creamos nuestros objetos (Instanciación):** En las primeras líneas del `main`, preparamos nuestro entorno. Creamos tres objetos de la clase `alimento` y al momento de nacer les damos un nombre en el constructor (`"manzana"`, `"lechuga"`, `"arracacha"`). Luego, creamos un objeto de la clase `boca` llamado `grande`, que inicia con un espacio o capacidad disponible de `100`.

```cpp
int main(){
    alimento frutas("manzana");
    alimento vegetal("lechuga");
    alimento tuberculo("arracacha");
    boca grande(100);

    grande.masticar(frutas, 10);
    grande.masticar(frutas, 10);
    grande.masticar(vegetal, 10);
    grande.masticar(tuberculo, 10);

    return 0;
}
```

2. **Pasar un objeto dentro de otro:** Cuando haces `grande.masticar(frutas, 10);`, está ocurriendo la magia de la Programación Orientada a Objetos: no le estás enviando solo texto o números a la boca, le estás pasando el objeto `frutas` en su totalidad.

```cpp
    grande.masticar(frutas, 10);
    grande.masticar(frutas, 10);
    grande.masticar(vegetal, 10);
    grande.masticar(tuberculo, 10);
```

3. **Interactuar con el visitante:** Dentro de la función `masticar`, ese objeto que acaba de entrar toma temporalmente el apodo de `generico`. Nuestra boca primero hace matemáticas: revisa si le cabe el bocado comparando la `capacidad_actual` con la `cantidad` que mandaste. Si funciona, resta la capacidad ocupada y luego ¡le habla al alimento! Al usar `generico.getNombre()`, la boca le está diciendo al objeto: *"Oye, ¿cómo te llamas?"*. Como le enviamos a `frutas`, este le responde *"manzana"*.

```cpp
bool boca::masticar(alimento generico, float cantidad){
 if(capacidad_actual >= cantidad) {
    capacidad_actual = capacidad_actual - cantidad;
    cout << "Masticando" << generico.getNombre() << endl; 
    return true;
    }
    if (capacidad_actual < cantidad && capacidad_actual > 0) {
        cout << "Masticando " << generico.getNombre() << " parcialmente, solo se puede masticar " << capacidad_actual << endl;
        capacidad_actual = 0;
        return true;
    }
    else {
        cout << "No se puede masticar " << cantidad << " del alimento " << generico.getNombre() << endl;
        return false; 
    }
}
```

4. **Lógica defensiva:** Finalmente, la estructura de los `if` actúa como un portero. Si le mandas un número muy grande de alimento o la boca ya se llenó después de masticar mucho, se encarga de masticar solo lo poquito que quepa (vaciando lo que queda de capacidad) o imprimir directamente que no entra más.

