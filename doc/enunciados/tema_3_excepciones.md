<!--
Posible prompt:
<prompt>
Tengo un cuestionario con preguntas sobre "Excepciones". Debes tener en cuenta que los conocimientos previos que tengo (y por tanto tus respuestas deben ser adaptadas), son:
- C/C++ sin orientación a objetos.
- Temas de Java previos: Clases y Objetos, Encapsulación.

Cada respuesta debe tener entre 2 - 4 párrafos de longitud (sin contar los trozos de código).

Por favor, escribe en impersonal las respuestas.

</prompt>
----
-->
# TEMA 3. Excepciones

## 1. Empecemos un tema sobre control de errores en lenguajes de programación, con algo básico. En C, donde no existen las excepciones, pongamos un ejemplo de una raíz que toma número flotante positivo. Queremos controlar el error si la función recibe un número negativo. El usuario debe ser informado pero desde fuera de la función `raiz` ¿Cómo indicamos ese error?. Enumera dos opciones diferentes de diseñar, poniendo un ejemplo de código de cada una.
-Opción 1: Usar un valor de retorno especial (código de error)
-Opción 2: Usar un valor especial en el retorno

## 2. Brevemente ¿Qué es una **"excepción"**? ¿Con qué objetivo las usa un programador cuando implementa funciones o cuando las llama?
-Una excepción es un mecanismo que permite indicar y gestionar errores o situaciones anómalas que ocurren durante la ejecución de un programa.
-Al implementar funciones:
  ·Para señalar condiciones de error de forma clara y estructurada.
  ·Para separar la lógica normal del manejo de errores.
Al llamar funciones:
  ·Para detectar y manejar errores sin interrumpir bruscamente el programa.
  ·Permiten reaccionar de forma controlada (mostrar mensaje, reintentar, limpiar recursos, etc.).

## 3. Reescribe el mismo ejemplo de raiz, pero en Java, metiendo ese método en una clase `Calculadora` y llama a dicho método desde el método `main`, mostrando cómo se puede controlar desde fuera.
public class Calculadora {

    public static double raiz(double x) {
        if (x < 0) {
            throw new IllegalArgumentException("No se puede calcular la raíz de un número negativo.");
        }
        return Math.sqrt(x);
    }

    public static void main(String[] args) {
        double num = -4;

        try {
            double r = raiz(num);
            System.out.println("La raíz de " + num + " es " + r);
        } catch (IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}


## 4. ¿Qué es **"lanzar"** una excepción? ¿Qué es **"controlar"** o **"capturar"** una excepción? ¿Qué es que se **"propague"** una excepción? ¿Qué le va ocurriendo a las funciones en la pila de llamadas por donde se va propagando la excepción? ¿Las funciones que no la controlan se reanudan después de alguna forma? Explica con el mismo ejemplo anterior en Java de la raíz cuadrada.

-Lanzar (throw) una excepción significa generar un error explícitamente en el código cuando ocurre una situación anómala.
-Capturar (catch) una excepción significa interceptarla y manejarla para evitar que el programa termine abruptamente.
-Si una función no captura la excepción, esta se propaga automáticamente hacia la función que la llamó.
-¿Qué ocurre en la pila de llamadas?
  Cuando se lanza una excepción:
    ·Se interrumpe la ejecución en el método actual.
    ·Se buscan bloques catch en ese método.
    ·Si no se encuentra:
      Se abandona el método.
      Se vuelve al método que lo llamó.
    ·Este proceso se repite subiendo por la pila de llamadas.
-¿Se reanudan las funciones que no la controlan? No


## 5. ¿Qué ventajas tiene frente a C, la **"propagación natural"** de las excepciones a través de la pila (*stack*) de llamadas?

  ·Separación entre lógica normal y manejo de errores
  ·Propagación automática por la pila
  ·Código más limpio y legible
  ·Manejo centralizado de errores
  ·Menos errores por descuido


## 6. En orientación a objetos, ¿las excepciones suelen ser objetos? ¿Qué ventajas tiene esto en términos de encapsulación? ¿Podemos entonces crear excepciones personalizadas?

-Sí, en orientación a objetos las excepciones suelen ser objetos.
-Al ser objetos, las excepciones permiten:
  ·Encapsular información del error
    Mensaje descriptivo
    Código de error
    Estado adicional relevante
  ·Agrupar datos y comportamiento
    No solo indican que hay un error, sino también detalles sobre él.
  ·Extensibilidad
    Se pueden añadir atributos y métodos propios.
  ·Tratamiento más específico
    Se pueden capturar tipos concretos de excepciones.
-Sí


## 7. En relación con las ventajas de la encapsulación, comparando el ejemplo en C con Java. ¿Qué **información esencial** lleva cualquier **objeto excepción** que es muy útil tener cuando se llega a un manejador?

·Tipo de la excepción
·Mensaje descriptivo
·Traza de la pila (stack trace)
·Causa (cause)
·Datos adicionales (opcionales)


## 8. En Java, sobre el bloque **"try-catch"**, ¿se pueden tener más de un bloque `catch`? ¿cuántos bloques `catch` se ejecutan?

-Sí, en Java se pueden tener múltiples bloques catch asociados a un mismo try.
-¿Cuántos catch se ejecutan? Solo se ejecuta un bloque catch.


## 9. Si las excepciones producen rupturas en el código llamador, ¿cómo podemos garantizar que se ejecuta siempre finalmente un código necesario para cierre de ficheros, liberacion de recursos, antes de que continúe propagándose la excepción? Pon un ejemplo en Java con `finally`, tanto con `catch` como sin él.

-Para garantizar que cierto código se ejecute siempre, incluso cuando se produce una excepción, en Java se utiliza el bloque finally.
-El bloque finally se ejecuta siempre:
  ·Haya o no excepción
  ·Se capture o no en un catch
  ·Se produzca un return dentro del try
-EJEMPLO con catch y finally
public class Ejemplo1 {
    public static void main(String[] args) {
        try {
            int x = 10 / 0;
            System.out.println("Esto no se ejecuta");
        } catch (ArithmeticException e) {
            System.out.println("Se produjo una excepción: " + e.getMessage());
        } finally {
            System.out.println("Bloque finally ejecutado (limpieza)");
        }

        System.out.println("El programa continúa...");
    }
}
-EJEMPLO sin catch (solo finally)
public class Ejemplo2 {
    public static void metodo() {
        try {
            int x = 10 / 0;
            System.out.println("Esto no se ejecuta");
        } finally {
            System.out.println("Finally ejecutado aunque no haya catch");
        }
    }

    public static void main(String[] args) {
        metodo();
        System.out.println("Esto no se ejecuta si la excepción no se captura");
    }
}

## 10. En Java, el bloque `finally` puede ir sin `catch`? ¿Se ejecuta siempre tanto si ocurre como si no ocurre una excepción? ¿Y si hay un `return` en medio del `try`?
-Sí, en Java el bloque finally puede ir sin catch.
-Sí, el bloque finally se ejecuta en prácticamente todos los casos, tanto si:
  ·No ocurre ninguna excepción
  ·Ocurre una excepción (aunque no se capture)
  ·Hay un catch que la maneja
  ·Hay un return dentro del try
-Aunque haya un return en el try:
  ·Primero se ejecuta el finally
  ·Luego se completa el return

## 11. En Java, qué son las excepciones **"controladas"** y las **"no controladas"**? ¿Qué papel juega `RuntimeException`? Pon un ejemplo de excepciones típicas controladas y no controladas que incluso nosotros mismos podríamos usar. Haz dos listas con 3 o 4 ejemplos de situación donde se suele preferir una excepción controlada y donde se suele preferir una excepción no controlada.
-Excepciones controladas (checked)
  Representan condiciones previsibles que el programador debería gestionar.
-Excepciones no controladas (unchecked)
  Representan errores de programación o situaciones que suelen indicar fallos lógicos.
-¿Qué papel juega RuntimeException?
  ·Es la clase base de todas las excepciones no controladas.
  ·Las excepciones que heredan de RuntimeException:
    No requieren try-catch obligatorio.
    Se usan para errores de programación o validaciones internas.
  ·Permite lanzar excepciones sin forzar su gestión en la firma del método.
  -EJEMPLO Controlada:
public class EdadInvalidaException extends Exception {
    public EdadInvalidaException(String mensaje) {
        super(mensaje);
    }
}
-EJEMPLO No controlada:
public class EdadInvalidaRuntimeException extends RuntimeException {
    public EdadInvalidaRuntimeException(String mensaje) {
        super(mensaje);
    }
}
-Cuándo preferir excepciones controladas
  ·Operaciones de entrada/salida (archivos, red)
  ·Acceso a bases de datos
  ·Servicios externos o APIs remotas
  ·Situaciones recuperables donde el usuario puede reaccionar
-Cuándo preferir excepciones no controladas
  ·Errores de programación (bugs)
  ·Validación de argumentos (null, rangos inválidos)
  ·Estados inconsistentes del sistema
  ·Situaciones que no se espera que el programador recupere directamente


## 12. ¿Qué es y para qué se usa `throws`? ¿Por qué es alternativa a capturar una excepción controlada?

-En Java, throws se utiliza en la declaración de un método para indicar que ese método puede lanzar una o varias excepciones controladas (checked exceptions) y que no las gestiona internamente.
-Cuando una excepción es controlada, Java obliga a elegir entre:
1. Capturarla con try-catch
try {
    metodo();
} catch (IOException e) {
    // manejar el error aquí
}

2. Declararla con throws
public void otroMetodo() throws IOException {
    metodo();
}


## 13. Pon un ejemplo en Java de firma de método que incluya `throws`, de una función que abre un fichero pero que declara que no le interesa menejar la excepción de si el fichero no existe, sino que se propague hacia arriba. Eso sí, acuérdate del `finally`.

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class EjemploFichero {

    public static void leerFichero(String ruta) throws IOException {
        BufferedReader br = null;
        try {
            br = new BufferedReader(new FileReader(ruta));
            String linea;
            while ((linea = br.readLine()) != null) {
                System.out.println(linea);
            }
        } finally {
            if (br != null) {
                try {
                    br.close();
                } catch (IOException e) {
                    // Se podría registrar el error de cierre si se desea
                    e.printStackTrace();
                }
            }
        }
    }

    public static void main(String[] args) {
        try {
            leerFichero("archivo.txt");
        } catch (IOException e) {
            System.out.println("Error al leer el fichero: " + e.getMessage());
        }
    }
}


## 14. ¿Podemos poner en `throws` excepciones no controladas, como `RuntimeException`? ¿Debería el método llamador entonces poner `try-catch` en ese caso? ¿Qué sentido tendría?

-Sí, se pueden declarar excepciones no controladas (RuntimeException) en throws, aunque no es obligatorio.
-Sí, por ejemplo:
public void metodo() throws RuntimeException {
    throw new IllegalArgumentException("Error");
}
Es válido, pero no es necesario porque:
  ·Las RuntimeException son unchecked.
  ·Java no obliga a declararlas ni a capturarlas.
-¿Debe el llamador usar try-catch?
No es obligatorio.
metodo(); // compila sin try-catch
-En general, poco o ninguno a nivel técnico, pero puede tener usos informativos:
  ·Documentación explícita de que el método puede lanzar ciertas excepciones.
  ·Indicar intencionalmente qué errores pueden ocurrir.
  ·Ayudar a herramientas o lectores del código a entender el comportamiento.

## 15. ¿Cuándo se recomienda usar excepciones controladas, como `IOException`, y cuándo no controladas como `IllegalArgumentException`? ¿Existen en todos los lenguajes ambas opciones? En los que sólo existe una opción, ¿cuál es la más habitual?

-Excepciones controladas (checked) — ej. IOException
Se recomiendan cuando:
  ·El error es previsible y recuperable
  ·El llamador puede (y debería) hacer algo razonable
  ·Forma parte del flujo normal de uso de la API
-Excepciones no controladas (unchecked) — ej. IllegalArgumentException
Se recomiendan cuando:
  ·El error indica un fallo de programación
  ·Se trata de validar argumentos o estado interno
  ·No se espera que el llamador pueda recuperarse en ese punto
-No.
-En lenguajes sin distinción (Python, C++, etc.), el modelo se acerca más a:
Excepciones no controladas (unchecked)
Porque:
  ·No se obliga al programador a declararlas.
  ·Se gestionan opcionalmente con try-catch (o equivalente).
  ·Se prioriza flexibilidad sobre control estricto del compilador.

## 16. ¿Tiene sentido lanzar excepciones dentro del `catch`? ¿Se puede relanzar la misma excepción capturada? ¿Cuándo tendría sentido hacer esto último? Pon ejemplos de ambos casos.

-Sí, tiene sentido lanzar excepciones dentro de un catch en varios escenarios, y también es posible relanzar la misma excepción capturada.
-1. Lanzar una nueva excepción dentro de catch
  Sí, es una práctica común cuando:
    ·Se quiere transformar la excepción en otra más adecuada para el nivel de abstracción.
    ·Se desea añadir contexto o información adicional.
    ·Se quiere ocultar detalles internos y exponer una excepción más general.
2. Relanzar la misma excepción
  Sí, se puede relanzar la misma excepción capturada:
-EJEMPLO EXCEPCIÓN DENTRO DE UN MISMO CATCH:
try {
    leerFichero("datos.txt");
} catch (IOException e) {
    throw new RuntimeException("Error al procesar el fichero de datos", e);
}
-EJEMPLO RELANZAR LA MISMA EXCEPCIÓN CAPTURADA:
try {
    leerFichero("datos.txt");
} catch (IOException e) {
    System.out.println("Se registra el error");
    throw e; // relanza la misma excepción
}

## 17. ¿En qué consiste que una excepción sea la **"causa"** de otra excepción? Pon un ejemplo en Java, donde capturemos una excepción de bajo nivel y la encapsulemos en otra personalizada de alto nivel. Cuando una excepción sale por pantalla y tiene una causa, ¿se ve?

-En Java, una excepción puede encapsular a otra como su causa cuando una excepción de bajo nivel provoca otra de más alto nivel.
-EJEMPLO EN JAVA:
import java.io.*;

class MiExcepcionAplicacion extends Exception {
    public MiExcepcionAplicacion(String mensaje, Throwable causa) {
        super(mensaje, causa);
    }
}

public class Ejemplo {

    public static void leerArchivo() throws MiExcepcionAplicacion {
        try {
            FileReader fr = new FileReader("archivo_inexistente.txt");
            BufferedReader br = new BufferedReader(fr);
            br.readLine();
        } catch (IOException e) {
            // Se encapsula la excepción original como causa
            throw new MiExcepcionAplicacion("Error en la lectura del archivo", e);
        }
    }

    public static void main(String[] args) {
        try {
            leerArchivo();
        } catch (MiExcepcionAplicacion e) {
            e.printStackTrace();
        }
    }
}
-Sí
Cuando se imprime con printStackTrace(), se muestra:
  ·La excepción principal
  ·Y debajo, la sección “Caused by:” con la excepción original y su traza
