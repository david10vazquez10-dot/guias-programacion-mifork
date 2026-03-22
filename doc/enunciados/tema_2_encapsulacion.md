<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Encapsulación". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# TEMA 2. Encapsulación

## 1. En Programación Orientada a Objetos (POO), ¿Qué buscan la **encapsulación** y **la ocultación** de información? Enumera brevemente algunas ventajas de la ocultación de información.

-En Programación Orientada a Objetos (POO), la encapsulación y la ocultación de información buscan principalmente:
  ·Proteger el estado interno de los objetos y controlar cómo se accede o modifica ese estado. En lugar de permitir acceso directo a los datos, se utilizan métodos (getters/setters u otros) que actúan como intermediarios.
-¿Qué persiguen exactamente?
  ·Encapsulación: agrupar datos (atributos) y comportamientos (métodos) dentro de una clase.
  ·Ocultación de información: restringir el acceso directo a ciertos detalles internos del objeto (por ejemplo, usando private o protected).
-Ventajas de la ocultación de información
  ·Mayor seguridad
    Evita modificaciones indebidas o inconsistentes en los datos.
  ·Control del acceso
    Permite validar datos antes de modificarlos.
  ·Menor acoplamiento
    Otros objetos no dependen de la implementación interna.
  ·Facilita el mantenimiento
    Puedes cambiar la implementación interna sin afectar al resto del código.
  ·Mejora la claridad del diseño
    Se define claramente qué es público y qué es interno.
  ·Reutilización de código
    Las clases bien encapsuladas son más fáciles de reutilizar.


## 2. ¿Qué se entiende por la **interfaz pública** de un objeto o clase en POO? Describe brevemente cómo se relaciona con la ocultación de información.

-La interfaz pública de un objeto o clase en POO es el conjunto de métodos (y en algunos casos atributos) accesibles desde fuera de la clase, es decir, todo aquello que otros objetos pueden usar para interactuar con él.

-Relación con la ocultación de información
  La interfaz pública está directamente ligada a la ocultación de información:
    ·La clase expone solo lo necesario a través de su interfaz pública.
    ·Los detalles internos (atributos, lógica interna) permanecen ocultos o restringidos (private o protected).
    ·Los usuarios de la clase no necesitan saber cómo funciona por dentro, solo cómo usarla.


## 3. Brevemente: ¿Por qué hay que ser conscientes y diseñar con cuidado la **interfaz pública** de una clase? ¿Es fácil cambiarla?

-Hay que diseñar con mucho cuidado la interfaz pública porque es el punto de contacto con el resto del sistema. Otras clases y módulos dependen de ella para funcionar.
-No, no es fácil cambiarla:
  ·Si modificas la interfaz pública, puedes romper código existente (compatibilidad).
  ·Obliga a actualizar todas las partes que dependen de ella.
  ·Puede introducir errores en cascada.

## 4. ¿Qué son las **invariantes de clase** y por qué la ocultación de información nos ayuda?

-Las invariantes de clase son condiciones o propiedades que siempre deben cumplirse para que un objeto esté en un estado válido.
-La ocultación de información permite mantener esas invariantes porque:
  ·Evita acceso directo a los atributos
  ·Fuerza el uso de métodos controlados
  ·Protege la consistencia del objeto

## 5. Pon un ejemplo de una clase `Punto` en `Java`, con dos coordenadas, `x` e `y`, de tipo `double`, con un método `calcularDistanciaAOrigen`, y que haga uso de la ocultación de información. ¿Cuál es la interfaz pública de la clase `Punto`? ¿Qué significa `public` y `private`?
-EJEMPLO:
public class Punto {
    private double x;
    private double y;

    // Constructor
    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    // Método público
    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    // Getters (opcional, también parte de la interfaz pública)
    public double getX() {
        return x;
    }

    public double getY() {
        return y;
    }
}
-La interfaz pública está formada por todos los elementos public:
  ·El constructor: Punto(double x, double y)
  ·El método: calcularDistanciaAOrigen()
  ·Los métodos: getX() y getY()
-¿Qué significan public y private?
  ·public:
    Accesible desde cualquier otra clase.
    Forma parte de la interfaz pública.
    Define cómo se usa el objeto.
  ·private:
    Solo accesible dentro de la propia clase.
    Oculta los detalles internos (como x e y).
    Protege los datos y mantiene el control sobre ellos.

## 6. En Java, ¿A quiénes se pueden aplicar los modificadores `public` o `private`?

-public
  ·Clases
  ·Métodos
  ·Atributos (variables)
  ·Constructores
-private
  ·Atributos
  ·Métodos
  ·Constructores
  ·Clases internas (inner classes)

## 7. En POO, la visibilidad puede ser pública o privada, pero ¿existen más tipos de visibilidad? ¿Qué ocurre en Java? ¿Y en otros lenguajes?

-Tipos de visibilidad en general (POO). Además de:
  public → accesible desde cualquier parte
  private → accesible solo dentro de la clase
También suelen existir:
  ·protected
    Accesible desde la propia clase y sus subclases (herencia).
  ·visibilidad por defecto / de paquete (a veces llamada package-private)
    Accesible solo dentro del mismo módulo o paquete.
-En Java hay 4 niveles de visibilidad:
  ·public → accesible desde cualquier lugar
  ·protected → accesible en la misma clase, paquete y subclases
  ·(sin modificador) (package-private) → solo dentro del mismo paquete
  ·private → solo dentro de la propia clase
-Depende del lenguaje:
·C++
  Tiene public, protected y private.
  Muy similar a Java, pero sin “package”.
·Python
  No tiene modificadores estrictos.
  Usa convenciones:
    _variable → “protegido” (por convención)
    __variable → “privado” (name mangling)
·C#
  Tiene más niveles:
    public, private, protected
    internal (por ensamblado)
    protected internal, etc.

## 8. Responde: Los miembros de instancia privados de un objeto están ocultos para (a) otras clases o (b) otras instancias, aunque sean de la misma clase. Pon un ejemplo añadiendo un método `calcularDistanciaAPunto(Punto otro)` y explica la respuesta.

-La respuesta correcta es: 👉 (a) otras clases
  No están ocultos para otras instancias de la misma clase.
-EJEMPLO:
public class Punto {
    private double x;
    private double y;

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;
    }

    public double calcularDistanciaAOrigen() {
        return Math.sqrt(x * x + y * y);
    }

    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.x - otro.x; // acceso a atributo privado de otro objeto
        double dy = this.y - otro.y;
        return Math.sqrt(dx * dx + dy * dy);
    }
}
-Explicación:
  Los atributos x e y son private, por lo que:
    No son accesibles desde otras clases.
    Sí son accesibles desde métodos de la misma clase, incluso si pertenecen a otra instancia (otro.x, otro.y).


## 9. ¿Qué son los métodos "getter" y "setter" en los lenguajes orientados a objetos?

Los métodos getter y setter son métodos que se utilizan para acceder y modificar los atributos privados de una clase de forma controlada, respetando la encapsulación.

## 10. Cuando nos referimos a que la ocultación de información mejora la "seguridad" del programa, ¿nos referimos a que no pueda ser "hackeado"?

No, en este contexto no nos referimos a seguridad frente a hackers o ataques externos.


## 11. ¿Qué diferencia hay entre **miembro de instancia** y **miembro de clase**? ¿Los miembros de clase también se pueden ocultar?

·Miembro de instancia
  Pertenece a cada objeto (instancia) de la clase.
  Cada objeto tiene su propia copia.
  Se accede a través de un objeto.
·Miembro de clase (estático)
  Pertenece a la clase en sí, no a los objetos.
  Se comparte entre todas las instancias.
  Se declara con static.
-¿Se pueden ocultar los miembros de clase?
Sí, también se pueden ocultar.
Los miembros de clase pueden usar modificadores de acceso como:
  ·private
  ·protected
  ·public
  ·(package-private)


## 12. Brevemente: ¿Tiene sentido que los constructores sean privados?

Sí, puede tener sentido, aunque no es lo más común. Un constructor private se usa cuando se quiere controlar cómo se crean los objetos de una clase.

## 13. ¿Cómo se indican los **miembros de clase** en Java? Pon un ejemplo, en la clase `Punto` definida anteriormente, para que incluya miembros de clase que permitan saber cuáles son los valores `x` e `y` máximos que se han establecido en todos los puntos que se hayan creado hasta el momento.

-En Java, los miembros de clase se indican utilizando la palabra clave static.
-EJEMPLO CLASE 'PUNTO':
public class Punto {
    private double x;
    private double y;

    // Miembros de clase (static)
    private static double maxX = Double.NEGATIVE_INFINITY;
    private static double maxY = Double.NEGATIVE_INFINITY;

    public Punto(double x, double y) {
        this.x = x;
        this.y = y;

        // Actualizar máximos
        if (x > maxX) {
            maxX = x;
        }
        if (y > maxY) {
            maxY = y;
        }
    }

    // Métodos de clase (static) para acceder a los máximos
    public static double getMaxX() {
        return maxX;
    }

    public static double getMaxY() {
        return maxY;
    }
}
## 14. Como sería un método factoría dentro de la clase `Punto` para construir un `Punto` a partir de dos coordenadas, pero que las redondee al entero más cercano. Escribe sólo el código del método, no toda la clase ¿Has usado `static`? 

-public static Punto crearRedondeado(double x, double y) {
    return new Punto(Math.round(x), Math.round(y));
}

-Sí, he usado static, porque es un método de clase (método factoría) que se invoca sin necesidad de crear una instancia previa de Punto.


## 15. Cambia la implementación de `Punto`. En vez de dos `double`, emplea un array interno de dos posiciones, intentando no modificar la interfaz pública de la clase.

public class Punto {
    private double[] coordenadas;

    public Punto(double x, double y) {
        this.coordenadas = new double[2];
        this.coordenadas[0] = x;
        this.coordenadas[1] = y;
    }

    public double calcularDistanciaAOrigen() {
        return Math.sqrt(coordenadas[0] * coordenadas[0] +
                         coordenadas[1] * coordenadas[1]);
    }

    public double calcularDistanciaAPunto(Punto otro) {
        double dx = this.coordenadas[0] - otro.coordenadas[0];
        double dy = this.coordenadas[1] - otro.coordenadas[1];
        return Math.sqrt(dx * dx + dy * dy);
    }

    public double getX() {
        return coordenadas[0];
    }

    public double getY() {
        return coordenadas[1];
    }
}

## 16. Si un atributo va a tener un método "getter" y "setter" públicos, ¿no es mejor declararlo público? ¿Cuál es la convención más habitual sobre los atributos, que sean públicos o privados? ¿Tiene esto algo que ver con las "invariantes de clase"?

-No, aunque un atributo tenga getter y setter, no es mejor hacerlo público.
-Convención habitual
  Lo más común en POO (especialmente en Java) es:
    ·Atributos private
    ·Acceso mediante métodos public (getters/setters)
-Sí, está directamente relacionado

## 17. ¿Qué significa que una clase sea **inmutable**? ¿qué es un método modificador? ¿Un método modificador es siempre un "setter"? ¿Tiene ventajas que una clase sea inmutable?

-Una clase es inmutable cuando una vez creado un objeto, su estado no puede cambiar.
-Un método modificador es aquel que cambia el estado interno de un objeto (sus atributos).
-No necesariamente.
  ·Un setter es un tipo específico de método modificador.
  ·Pero no todos los métodos modificadores son setters.
-Sí, varias importantes:
  ·Seguridad: el estado no puede cambiar inesperadamente.
  ·Hilos (thread-safe): son seguras en entornos concurrentes sin sincronización.
  ·Más fáciles de entender y razonar: no cambian con el tiempo.
  ·Menos errores: no hay efectos secundarios por modificaciones.
  ·Reutilización y caching: se pueden compartir instancias sin riesgo.


## 18. ¿Es recomendable incluir métodos "setter" siempre y como convención?

No, no es recomendable incluir métodos “setter” siempre como convención.

## 19. ¿La clase `String` en Java es mutable o inmutable? ¿Qué ocurre al concatenar dos cadenas? ¿Qué debemos hacer si vamos a hacer una operación que implique concatenar muchas veces para construir paso a paso una cadena muy larga?

-La clase String en Java es inmutable.
-Cuando concatenas cadenas, no se modifica la cadena original, sino que se crea un nuevo objeto String.
-Se recomienda usar clases mutables diseñadas para esto:
  ·StringBuilder (no sincronizada, más rápida)
  ·StringBuffer (sincronizada, thread-safe)


## 20. En POO ¿Cómo se comparan objetos de una misma clase? ¿Por su contenido o por su identidad? ¿Qué es el método equals en Java? ¿Qué hace por defecto? ¿Cómo se deben comparar dos cadenas en Java? 

-En POO, los objetos se pueden comparar de dos formas:
  ·Por identidad 👉 si son el mismo objeto en memoria.
  ·Por contenido 👉 si sus atributos tienen el mismo valor.
-Es un método de la clase Object que sirve para comparar objetos.
-En la clase Object, equals:
  ·Se comporta igual que ==
  ·Es decir, compara referencias (identidad), no contenido
-Las cadenas (String) deben compararse usando:
  ·equals()

## 21. ¿Qué son las clases "wrapper" en un lenguaje de programación orientado a objetos? ¿Cómo se hace? ¿Es un proceso automático? ¿Qué ventajas tienen? ¿Todos los lenguajes orientados a objetos tienen tipos primitivos y necesitan wrappers? 

-Las clases wrapper son clases que envuelven (wrap) un tipo primitivo para tratarlo como un objeto.
-Se puede hacer de dos formas:
  ·Manual (antes de Java 5)
    Integer x = Integer.valueOf(10);
    int y = x.intValue();
  ·Automático (autoboxing / unboxing)
  Java convierte automáticamente entre primitivos y wrappers:
    Integer x = 10; // autoboxing
    int y = x;      // unboxing


## 22. ¿En POO qué es un **tipo de dato enumerado**? ¿En Java, un tipo de dato enumerado es una clase? ¿Qué ventajas tienen en términos de encapsulación los enumerados en Java?
-Un tipo de dato enumerado (enum) es un tipo que representa un conjunto finito y predefinido de valores posibles.
-Sí. En Java, un enum es en realidad un tipo especial de clase.
-Los enum en Java aportan varias ventajas:
  ·Valores limitados y controlados
    Solo existen las constantes definidas en el enum.
    No se pueden crear nuevos valores arbitrarios.
  ·Seguridad de tipo (type safety)
    Evitan errores frente a usar constantes sueltas (como int o String).
  ·Encapsulación de comportamiento
    Los enums pueden incluir métodos y lógica interna.
  ·Mejor legibilidad y mantenimiento
    El código es más claro y expresivo que usar constantes dispersas.
  ·Evitan valores inválidos
    No se pueden asignar valores fuera del conjunto definido.


## 23. Crea un tipo enumerado en Java que se llame `Mes`, con doce posibles instancias y que además proporcione métodos para obtener cuántos días tiene ese mes, el ordinal de ese mes en el año (1-12), empleando atributos privados y constructores del tipo enumerado.

public enum Mes {
    ENERO(31),
    FEBRERO(28),
    MARZO(31),
    ABRIL(30),
    MAYO(31),
    JUNIO(30),
    JULIO(31),
    AGOSTO(31),
    SEPTIEMBRE(30),
    OCTUBRE(31),
    NOVIEMBRE(30),
    DICIEMBRE(31);

    private final int dias;

    private Mes(int dias) {
        this.dias = dias;
    }

    public int getDias() {
        return dias;
    }

    public int getOrden() {
        return this.ordinal() + 1;
    }
}


## 24. Añade a la clase `Mes` del ejercicio anterior cuatro métodos para devolver si ese mes tiene algunos días de invierno, primavera, verano u otoño, indicando con un booleano el hemisferio (norte o sur, parámetro `enHemisferioNorte`). Es decir: `esDePrimavera(boolean esHemisferioNorte)`, `esDeVerano(boolean esHemisferioNorte)`, `esDeOtoño(boolean esHemisferioNorte)`, `esDeInvierno(boolean esHemisferioNorte)`

public enum Mes {
    ENERO(31),
    FEBRERO(28),
    MARZO(31),
    ABRIL(30),
    MAYO(31),
    JUNIO(30),
    JULIO(31),
    AGOSTO(31),
    SEPTIEMBRE(30),
    OCTUBRE(31),
    NOVIEMBRE(30),
    DICIEMBRE(31);

    private final int dias;

    private Mes(int dias) {
        this.dias = dias;
    }

    public int getDias() {
        return dias;
    }

    public int getOrden() {
        return this.ordinal() + 1;
    }

    public boolean esDePrimavera(boolean enHemisferioNorte) {
        return enHemisferioNorte
                ? this == MARZO || this == ABRIL || this == MAYO
                : this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE;
    }

    public boolean esDeVerano(boolean enHemisferioNorte) {
        return enHemisferioNorte
                ? this == JUNIO || this == JULIO || this == AGOSTO
                : this == DICIEMBRE || this == ENERO || this == FEBRERO;
    }

    public boolean esDeOtoño(boolean enHemisferioNorte) {
        return enHemisferioNorte
                ? this == SEPTIEMBRE || this == OCTUBRE || this == NOVIEMBRE
                : this == MARZO || this == ABRIL || this == MAYO;
    }

    public boolean esDeInvierno(boolean enHemisferioNorte) {
        return enHemisferioNorte
                ? this == DICIEMBRE || this == ENERO || this == FEBRERO
                : this == JUNIO || this == JULIO || this == AGOSTO;
    }
}
