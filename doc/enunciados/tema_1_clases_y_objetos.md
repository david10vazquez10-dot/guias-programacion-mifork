<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Clases y Objetos". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: ninguno.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->

# TEMA 1. Clases y objetos

## 1. ¿Cuáles son las cuatro características básicas de la programación orientada a objetos? Describe brevemente cada una

Las cuatro características básicas de la programación orientada a objetos (POO) son:

-Encapsulación
Consiste en agrupar datos (atributos) y métodos (funciones) dentro de una misma unidad llamada objeto, y restringir el acceso directo a algunos de sus componentes. Esto se logra usando modificadores de acceso (como público, privado, etc.), lo que protege los datos y evita que se modifiquen de forma incorrecta.

-Abstracción
Se basa en mostrar solo la información esencial de un objeto y ocultar los detalles innecesarios. Permite trabajar con conceptos generales sin necesidad de conocer cómo están implementados internamente.

-Herencia
Permite que una clase (clase hija) herede atributos y métodos de otra clase (clase padre). Esto facilita la reutilización de código y la creación de jerarquías entre clases.

-Polimorfismo
Es la capacidad de un objeto de comportarse de diferentes maneras según el contexto. Por ejemplo, un mismo método puede tener distintas implementaciones dependiendo de la clase que lo utilice.


## 2. Cita cuatro lenguajes populares que permitan la programación orientada a objetos

-Java – Uno de los lenguajes más conocidos, totalmente orientado a objetos y muy utilizado en aplicaciones empresariales y móviles.

-Python – Lenguaje muy versátil y fácil de aprender que también soporta programación orientada a objetos.

-C++ – Extiende el lenguaje C e incorpora características de POO como clases, herencia y polimorfismo.

-C# – Desarrollado por Microsoft, ampliamente usado en aplicaciones de escritorio, web y videojuegos


## 3. Los paradigmas anteriores a la POO, ¿Qué es la **programación estructurada**? y, todavía mejor, ¿Qué es la **programación modular**?

-Programación estructurada: Es un paradigma que organiza el código en estructuras claras y controladas, evitando el uso desordenado de instrucciones como los saltos
-Programación modular: Es un enfoque que consiste en dividir un programa en partes más pequeñas llamadas módulos (o funciones/procedimientos).

## 4. ¿Qué tres elementos definen a un objeto en programación orientada a objetos?

-Atributos (o propiedades):
Son las características o datos que describen al objeto. Representan su estado.

-Métodos (o comportamientos):
Son las acciones que el objeto puede realizar. Son funciones asociadas al objeto.

-Identidad:
Es la característica que permite distinguir un objeto de otro, incluso si tienen los mismos atributos y métodos. Cada objeto es único dentro del sistema.

## 5. ¿Qué es una clase? ¿Es lo mismo que un objeto? ¿Qué es una instancia? ¿Todos los lenguajes orientados a objetos manejan el concepto de clase?

-Una clase es una plantilla o modelo a partir del cual se crean objetos.Define:
Los atributos (datos),los métodos (comportamientos).
-¿Es lo mismo que un objeto? No, no son lo mismo.

Clase → es el molde o definición.

Objeto → es una entidad concreta creada a partir de esa clase.
-¿Qué es una instancia? Una instancia es simplemente un objeto creado a partir de una clase.
-¿Todos los lenguajes orientados a objetos manejan el concepto de clase? No, no todos. Aunque muchos lenguajes como Java, C++ o C# sí usan clases, existen lenguajes orientados a objetos que no utilizan clases, sino otro enfoque.

## 6. ¿Dónde se almacenan en memoria los objetos? ¿Es igual en todos los lenguajes? ¿Qué es la **recolección de basura**? 
-Generalmente, los objetos se almacenan en una zona de memoria llamada heap (montículo):
  ·El heap se usa para memoria dinámica (objetos creados en tiempo de ejecución).
  ·Las variables que hacen referencia a esos objetos suelen estar en el stack (pila), pero el objeto en sí está en el heap.
  
-No, no es exactamente igual en todos los lenguajes.
  ·En lenguajes como Java o C#, los objetos casi siempre se almacenan en el heap.
  ·En C++, depende: los objetos pueden estar en el stack o en el heap según cómo se creen.
  ·En lenguajes como Python, todo se maneja automáticamente en el heap.

-La recolección de basura es un mecanismo automático que libera memoria que ya no se está utilizando.
  ·Detecta objetos que ya no tienen referencias (nadie los usa).
  ·Libera el espacio que ocupaban en memoria.


## 7. ¿Qué es un método? ¿Qué es la **sobrecarga de métodos**? 

-Un método es una función que pertenece a una clase y define una acción que pueden realizar sus objetos.
-La sobrecarga de métodos (method overloading) es la capacidad de definir varios métodos con el mismo nombre, pero con diferentes parámetros.


## 8. Ejemplo mínimo de clase en Java, que se llame Punto, con dos atributos, x e y, con un método que se llame `calculaDistanciaAOrigen`, que calcule la distancia a la posición 0,0. Por sencillez, los atributos deben tener visibilidad por defecto. Crea además un ejemplo de uso con una instancia y uso del método

// Definición de la clase
class Punto {
    double x;
    double y;

    // Método que calcula la distancia al origen (0,0)
    double calculaDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }
}

// Ejemplo de uso
public class Main {
    public static void main(String[] args) {
        Punto p = new Punto();
        p.x = 3;
        p.y = 4;

        double distancia = p.calculaDistanciaAOrigen();
        System.out.println("Distancia al origen: " + distancia);
    }
}


## 9. ¿Cuál es el punto de entrada en un programa en Java? ¿Qué es `static` y para qué vale? ¿Sólo se emplea para ese método `main`? ¿Para qué se combina con `final`?

-El punto de entrada es el método: public static void main(String[] args)
-La palabra clave static indica que un elemento pertenece a la clase y no a las instancias (objetos).
-No, se usa en muchos más casos:
  ·Variables estáticas (compartidas)
  ·Métodos estáticos (utilidades, como Math.sqrt())
  ·Bloques estáticos (inicialización de la clase)

## 10. Intenta ejecutar un poco de Java de forma básica, con los comandos `javac` y `java`. ¿Cómo podemos compilar el programa y ejecutarlo desde linea de comandos? ¿Java es compilado? ¿Qué es la **máquina virtual**? ¿Qué es el *byte-code* y los ficheros `.class`?

-Compilar el programa: javac Main.java
Esto genera un archivo llamado Main.class.
-Ejecutar el programa: java Main 
Esto ejecuta el programa (sin poner .class).
-Sí, pero no completamente como otros lenguajes tradicionales.
Java es un lenguaje compilado e interpretado a la vez:
  ·Se compila el código fuente (.java)
  ·Se genera bytecode
  ·Ese bytecode es interpretado o ejecutado por la máquina virtual
-La JVM (Java Virtual Machine) es un programa que ejecuta el código Java. Su función es:
  ·Leer el bytecode
  ·Ejecutarlo en cualquier sistema operativo
-Bytecode → es un código intermedio (no es código máquina real).  .class → es el archivo donde se guarda ese bytecode.

## 11. En el código anterior de la clase `Punto` ¿Qué es `new`? ¿Qué es un **constructor**? Pon un ejemplo de constructor en una clase `Empleado` que tenga DNI, nombre y apellidos

-new es una palabra clave en Java que se utiliza para crear (instanciar) objetos a partir de una clase.
-Un constructor es un método especial que:
  ·Tiene el mismo nombre que la clase
  ·No devuelve ningún tipo (ni siquiera void)
  ·Se ejecuta automáticamente al crear un objeto con new
  ·Se usa para inicializar los atributos del objeto

EJEMPLO:
  -class Empleado {
    String dni;
    String nombre;
    String apellidos;

    // Constructor
    Empleado(String dni, String nombre, String apellidos) {
        this.dni = dni;
        this.nombre = nombre;
        this.apellidos = apellidos;
    }
}

## 12. ¿Qué es la referencia `this`? ¿Se llama igual en todos los lenguajes? Pon un ejemplo del uso de `this` en la clase `Punto`

-this es una referencia al objeto actual dentro de una clase. Se utiliza para acceder a los atributos y métodos del propio objeto desde dentro de la clase.
-No exactamente.
  ·En Java, C# y C++ se usa this.
  ·En otros lenguajes orientados a objetos puede tener otros nombres:
  ·En Python se usa self (aunque se pasa como parámetro explícito).
  ·En JavaScript existe this, pero su comportamiento es distinto según el contexto.

  EJEMPLO: 
  class Punto {
    double x;
    double y;

    // Constructor usando this
    Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    double calculaDistanciaAOrigen() {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }
}


## 13. Añade ahora otro nuevo método que se llame `distanciaA`, que reciba un `Punto` como parámetro y calcule la distancia entre `this` y el punto proporcionado

class Punto {
    double x;
    double y;

    // Constructor
    Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    // Distancia al origen
    double calculaDistanciaAOrigen() {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }

    // Distancia entre dos puntos
    double distanciaA(Punto otro) {
        double dx = this.x - otro.x;
        double dy = this.y - otro.y;
        return Math.sqrt(dx * dx + dy * dy);
    }
}


## 14. El paso del `Punto` como parámetro a un método, es **por copia** o **por referencia**, es decir, si se cambia el valor de algún atributo del punto pasado como parámetro, dichos cambios afectan al objeto fuera del método? ¿Qué ocurre si en vez de un `Punto`, se recibiese un entero (`int`) y dicho entero se modificase dentro de la función? 

-En Java, el paso de parámetros es siempre por valor, pero hay un matiz importante cuando trabajamos con objetos.
-Cuando pasas un objeto (como Punto) a un método:
  ·Se pasa una copia de la referencia al objeto.
  ·Esa referencia apunta al mismo objeto en memoria.
Por tanto:
  ·Si modificas los atributos del objeto dentro del método, esos cambios sí afectan al objeto original fuera del método.
-¿Qué ocurre con un int?
Los tipos primitivos como int:
  ·Se pasan por valor (copia del valor).
  ·No se comparten referencias.
Por tanto:
  ·Si modificas el int dentro del método, no afecta al valor original fuera del método.

## 15. ¿Qué es el método `toString()` en Java? ¿Existe en otros lenguajes? Pon un ejemplo de `toString()` en la clase `Punto` en Java

-toString() es un método heredado de la clase base Object que se utiliza para obtener una representación en forma de cadena (String) de un objeto.
-Sí, muchos lenguajes tienen mecanismos similares, aunque con nombres distintos:
  ·JavaScript → toString()
  ·C# → ToString()
  ·Python → __str__() y __repr__()
  ·C++ → no hay un equivalente directo estándar, pero se suele sobrecargar el operador <<

## 16. Reflexiona: ¿una clase es como un `struct` en C? ¿Qué le falta al `struct` para ser como una clase y las variables de ese tipo ser instancias?

-Una clase en programación orientada a objetos se parece en parte a un struct de C, pero no son equivalentes.
-A un struct de C le faltan principalmente estas características propias de las clases:

·Encapsulación real
  En clases puedes controlar el acceso (private, public, protected).
  En C, los struct no tienen mecanismos nativos de encapsulación (sus campos son accesibles directamente).
·Métodos asociados
  Las clases pueden tener funciones (métodos) que operan sobre sus datos.
  Los struct en C no incluyen métodos como tal (aunque se pueden simular con funciones externas).
·Herencia
  Las clases pueden heredar de otras clases.
  Los struct en C no soportan herencia.
·Polimorfismo
  Las clases permiten comportamientos distintos mediante herencia e interfaces.
  Los struct no lo soportan directamente.
·Constructores y control de inicialización
  Las clases suelen tener constructores para inicializar objetos.
  Los struct en C no tienen constructores (la inicialización es manual).

## 17. Quitemos un poco de magia a todo esto: ¿Como se podría “emular”, con `struct` en C, la clase `Punto`, con su función para calcular la distancia al origen? ¿Qué ha pasado con `this`?

-En C no existen clases ni métodos asociados a un tipo como en POO, pero se puede emular una clase usando un struct junto con funciones que reciben ese struct como parámetro.
-Emulación de la clase Punto en C
#include <stdio.h>
#include <math.h>

// Definición del struct
typedef struct {
    double x;
    double y;
} Punto;

// Función equivalente a calculaDistanciaAOrigen
double calculaDistanciaAOrigen(Punto p) {
    return sqrt(p.x * p.x + p.y * p.y);
}

int main() {
    Punto p;
    p.x = 3;
    p.y = 4;

    double distancia = calculaDistanciaAOrigen(p);
    printf("Distancia al origen: %f\n", distancia);

    return 0;
}
-En este modelo en C:
  ·No existe this.
  ·No hay objetos con métodos asociados.
  ·La función recibe explícitamente el “objeto” como parámetro (Punto p).
