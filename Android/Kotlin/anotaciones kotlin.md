# **Palabras reservadas**
fun=función 

var=variable

val=  constante

Math = clase matemáticas, con las funciones mátemáticas

- .cos()= función para calcular el coseno

this. = hace referencia a una variable creada dentro de una clase, NO a una variable que recibe en los parámetros de la clase

constructor

# **Tipos de datos**
Double			64  bits

Float				32 bits

Long				64 bits

Int				32 bits

Short				16 bits

Byte				 8 bits

Characters 			un caracter

String, 				una cadena

Arrays,				Matriz

Booleans			lógico

# **Conversión de tipo de dato**

```Kotlin
//esto se hace en los tipos de dato char, ya que el número en char es 48 numeros superior a su igual en Decimal

*Tipo de Dato*:toInt() – 48 
```


# **Funciones String.**
## **Acceder a un elemento dentro de una cadena (String)**
```Kotlin
*variable*[*Posición*]
```
## **Saber el tamaño de una cadena**
```Kotlin
*variable*.length
```

## **Tipos de Strings**
Strings con secuencia de Escape: se pueden agregar secuencias de escape(n, u, etc)

Strings puros: son los strings que solamente imprimen lo que está en comillas(“,”””)
## **Imprimir una variable string sin usar +**
```Kotlin
println(“*Texto* $*Variable*”)
```
# **Arreglos**
```Kotlin
//un arreglo explícito

var *Nombre*: Array<*Tipo de dato*> = arrayOf(*contenido*,*contenido*,*contenido*)

//un arreglo implícito

var arreglo = int ArrayOf(1,2,3)

var *Nombre* = *Tipo de dato*ArrayOf(1,2,3)
```

## **Imprimir contenido de un arreglo**
```Kotlin
printl(*Nombre*[*posición*])
```
# **Variables que no sabes que tipo de dato serán**
```Kotlin
var *Nombre*:Any = *Valor*
```
# **Estructura de control**
```Kotlin
//forma corta del if else

If(*variable/valor* > *variable/valor*) *accion* else *acción*
```

# **When**
```Kotlin
//ejemplos de when

when (x) {

      1 -> print("x == 1")

      2 -> print("x == 2")

      else -> { // Note the block

          print("x is neither 1 nor 2")

      }

}

//evitamos estar marcando cada opción

When(*variable*){

1 -> *variable* = *accion*

2 -> *variable* = *accion*

3,4,5,6 -> *variable* = {*accion*

}

.

.

.

.

.

Else -> *variable* = *acción*

}

//ponemos un rango de opciones

When(*variable*){

in 1..5 -> *variable* = {*accion*}

.

.

.

.

.

Else -> *variable* = *acción*

}
```

# **Ciclo for**
```Kotlin
//forma corta

for (*variable*:*tipo de dato* in 1..5) *acción*

//forma larga

for (*variable*  in 1..5){

*acción*

}

//doble variable y matriz

fun main(args: Array<String>) {
var arregloInt = intArrayOf(4,5,6,7,8,9,10,11,12,13,14,15,16,17,18)
      for ((indice, valor)in arregloInt.withIndex()){
          println ("El indice $indice representa el valor $valor")
      }
}
```

# **Ciclo while**
```Kotlin
//la forma corta
while(x<=10){
  println(x)
  x=x+1
}

//do while
var y=1
do{
  print("Estoy dentro")
}
while(y!=1)
```

# **Funciones**
```Kotlin
//especificando el tipo de dato de la función

var *variable* = *función*(*valor*,*valor*)

println(resultado)

fun *función*(*variable*:*Tipo de dato*, *variable*:*Tipo de dato*):*Tipo de dato*{

}
```

# **Inicializar las variables**
```Kotlin
init{
this.*variable* = *variable*
.
.
.
.
}
```

# **Crear Objetos**
```Kotlin
var *nombre* = *clase*()
```

# **Acceder a una propiedad del objeto**
```Kotlin
*objeto*.*propiedad*
```

# **Crear funciones**
```Kotlin
//sin pasar parámetros
fun *nombre*() {
     *acción*
}
```

# **Método constructor(construye objetos)**
```Kotlin
constructor(*parametro*:*Tipo de dato*…):this(){

this.*variable* = *parametro*
.
.
.
}
```

# **Tipos de clases**
```Kotlin
//Clases tipo open: puedes hacer que otras clases, hereden atributos o métodos de la clase open.

open class *nombre de la clase*(){
.
.
.
.
}


//Clases tipo final: una vez escrito/compilado en el programa, ya no puedes heredar o modificar de ellas.

class *nombre de la clase*(){
.
.
.
.
}
```

# **Herencia entre clases**
```Kotlin
class *nombre de la clase*():*clase padre*(){
.
.
.
}
```

# **HTTP y JSON**
## **Tipos de solicitudes HTTP y Métodos**
**GET:** hace solicitudes de información específica (pides información)

**POST:** envía los datos para ser procesados a un recurso específico (envías la información)

## **Formas de implementar las solicitudes HTTP**
**Nativa:** usando los métodos que tiene kotlin para llamar las solicitudes http en busca de un recurso
**Volley:**
**OkHttp:**

# **Null-safety**
## **Llamadas seguras**
En caso de la llamada sea nula evitará que se crashe la aplicación:

```Kotlin
var *nombre de la variable*: *tipo de dato*? = *valor o sin valor*

*llamada a la variable ya sea print, toast, Log, etc.*
```

Otro ejemplo de llamada segura:
```Kotlin
 	 *nombre de la variable*?.let{

 	 println(it)

} ?: run{

 	 println(*nombre de la variable*)

}
```

## **Probando condiciones nulas**
```Kotlin-
val l = if (b != null) b.length else -1
```

## **Elvis Operator**
Cuando tengas una referencia nula, puedes decir “Sí b no es nulo, usar esto, de lo contrario usar un valor no nulo”

```Kotlin
val l = b?.length ?: -1
```

otro ejemplo de Elvis operador:
```Kotlin
fun foo(node: Node): String? {

     		 val parent = node.getParent() ?: return null

val name = node.getName() ?: throw IllegalArgumentException("name expected")



}
```

## **El operador !!**
Convierte cualquier valor a tipo no nulo y lanza una excepción si el valor es nulo:

```Kotlin
val l = b!!.length
```

## **Cast seguro**
Los lanzamientos regulares pueden resultar en a ClassCastException si el objeto no es del tipo de destino. Otra opción es usar conversiones seguras que regresan null si el intento no fue exitoso:
```Kotlin
val aInt: Int? = a as? Int
```
## **Colección de un tipo nulable**
Si tiene una colección de elementos de un tipo que acepta valores NULL y desea filtrar elementos no nulos, puede hacerlo mediante filterNotNull:
```Kotlin
val nullableList: List<Int?> = listOf(1, 2, null, 4)

val intList: List<Int> = nullableList.filterNotNull()
```

# **Comparación de LiveData, Flow, StateFlow, y SharedFlow**
![](Aspose.Words.4e276513-788f-4af8-9e8b-9cd31daeee0c.004.png)
## **LiveData vs StateFlow**
### LIVEDATA**	
- **Consciente del ciclo de vida:** Se detiene/reanuda automáticamente en función del estado del ciclo de vida
- **Enfocado en IU:** Diseñado específicamente para componente de la IU para Android
- **Solamente en el hilo principal:** Los observadores funcionand en el hilo principal
- **Chismoso:** Siempre emite el último valor a los nuevos observadores
### **STATEFLOW**
- **No es consciente del ciclo de vida:** Requiere del control manual del ciclo de vida.
- **Basado en corrutinas:** Forma parte del ecosistema de corrutinas de Kotlin
- **A prueba de hilos:** Puede emitir de cualquier hilos.
- **Compatibilidad con Compose:** Funciona mejor con compose y patrones de diseño reactivos modernos
- **Flujo de acceso rápido:** Siempre activo, no se detiene automáticamente
- **Corrutinas y testing:** tiene un mejor soporte para testing e integración de corrutinas que LiveData
## **LiveData vs Flows**
### **LIVEDATA**
- **Consciente del ciclo de vida:** Controla automáticamente el ciclo de vida de Android
- **Centrado en la IU:** Diseñado para la capa de IU de Android.
- **Hilo principal:** Observadores se ejecutan en el hilo principal.
- **Dependencias Android:** Forma parte de los componentes de arquitectura de Android.
- **Emisión de datos:** Un solo valor
- **Soporte de plataforma:** Específico de Android
- **Modelo de ejecución:** Caliente (siempre está activo).
- **Operadores:** Operadores límitados.
- **Mejor capa:** Capa de IU
- **Cuando usar:** Estados de la IU que necesitan estar conscientes del comportamiento del ciclo de vida.
### **FLOW**
- **No es consciente del ciclo de vida:** Es Kotlin puro y no controla el ciclo de vida de Android. Controla el ciclo de vida manualmente.
- **Flujo de valores:** Puede emitir multiples valores a lo largo del tiempo
- **Es frío por defecto:** Solo se activa cuando es recolectado
- **Cualquier Hilo:** A prueba de hilos, puede cambiar de contextos
- **Operadores poderosos:** Set rico de operadores de transformación
- **Emisión de datos:** Flujo de valores.
- **Soporte de plataforma:** Plataforma agnóstico de Kotlin
- **Modelo de ejecución:** Frío (Perezoso).
- **Operadores:** Set rico de operadores.
- **Mejor capa:** Capa de Datos/Negocio (propositos generales de kotlin para flujos reactivos y multiplataforma).
- **Cuando usar:** Flujos de datos, capa de repositorio, tranformacioens complejas, proyectos que no son de android.
## **LiveData vs SharedFlow**
### **LIVEDATA**
- **Lifecycle-aware:** gestiona automáticamente el ciclo de vida de Android
- **Tenedor del estado:** Tiene valor actual, los nuevos observadores obtienen el último valor
- **Valor único:** Un valor a la vez
- **Enfocado en la interfaz de usuario:** Diseñado para componentes de interfaz de usuario
- **Manejo automático del ciclo de vida:** pausas/resumen con ciclo de vida
- **Naturaleza de los datos:** Recipiente de estado (pegajoso).
- **Control del ciclo de vida:** Consciente del ciclo de vida.
- **Observadores:** Patrón de un solo observador.
- **Valor inicial:** Siempre tiene el valor actual.
- **Enfoque:** Enfocado en la IU.
- **Plataforma:** Específico de android.
- **Cuando usar:** El estado de la IU que necesita persistencia (perfil de usuario, estado de carga).
### **SHAREDFLOW**
- **No tiene conocimiento del ciclo de vida:** Requiere el manejo manual del ciclo de vida
- **Flujo de eventos:** Diseñado para eventos/acciones, no estado
- **Transmisión en caliente:** Siempre activo, múltiples suscriptores
- **Configurable:** Puede reproducir eventos, valores de búfer
- **Sin valor inicial:** A diferencia de StateFlow, no mantiene el estado
- **Naturaleza de los datos:** Flujo de eventos (no es pegajoso)
- **Control del ciclo de vida:** Control manual del ciclo de vida.
- **Observadores:** Multiples subscriptores.
- **Valor inicial:** No tiene un valor inicial.
- **Enfoque:** Enfocado en acciones y eventos.
- **Plataforma:** Independiente de plataformas.
- **Cuando usar:** Un evento a la vez (navegación, toasts, snackbars, clicks de botón).
## Flow vs StateFlow
### Flow
- **Flujo frío:** Solo activo cuando se recolecta, cada colector recibe su propio flujo.
- **Sin recipiente de estado:** no almacena el valor actual
- **Emisiones múltiples:** puede emitir una secuencia de valores a lo largo del tiempo
- **Lazy:** Inicia la ejecución cuando se recolecta
- **Uno a uno:** cada recolector obtiene ejecución independiente.
- **Modelo de ejecución:** Frío (perezoso)
- **Caso de uso:** Flujo de datos, operaciones de información, llamadas a API, queries de bases de datos, transformaciones.
- **Ciclo de vida:** Empieza en la recolección.
### StateFlow
- **Flujo caliente:** Siempre activo, compartido entre los recolectores
- **Recipiente de estado:** Siempre tiene el valor actual
- **Mezclado:** Solo importa el valor más reciente, cae valores intermedios
- **Pegajoso:** Los nuevos recolectores obtienen inmediatamente el valor actual
- **Uno-a-muchos:** Ejecución única, múltiples suscriptores
- **Modelo de ejecución:** Caliente (siempre activo)
- **Caso de uso:** Gestión de estado, estados de IU, configuraciones, Información actual de usuario, estado de la app.
- **Ciclo de vida:** Siempre está ejecutándose.
## **Flow vs SharedFlow**
### **Flow**
- **Flujo en frío:** solo se ejecuta cuando se recopila, cada colector obtiene ejecución independiente
- **Uno a uno:** Cada colector desencadena ejecución separada
- **Perezoso:** No comienza hasta que se recoge
- **Secuencial:** Valores emitidos secuencialmente a cada colector
- **Procesamiento de datos:** Mejor para las transformaciones y operaciones de datos
- **Comportamiento del recolector:** Independiente por recolector.
- **Uso primario:** Procesamiento/Transformación de información
- **Ciclo de vida:** Empieza en la recolección
- **Capacidad de repetición:** Sin capacidad de repetición.
- **Manejo de la contrapresión:** Manejo de la contrapresión
- **Caso de uso:** Operaciones de información, llamadas API, queries de base de datos, transformaciones, capa de repositorio.
### **SharedFlow**
- **Flujo de acceso rápido:** siempre activo, ejecución compartida entre los coleccionistas
- **Uno-a-muchos:** Ejecución única, múltiples suscriptores
- **Transmisión de eventos:** Diseñado para transmitir eventos
- **Configurable:** Puede reproducir eventos, valores de búfer
- **Sin contrapresión:** Utiliza el buffer con estrategias de desbordamiento
- **Comportamiento del recolector:** Compartido entre recolectores.
- **Uso primario:** Transmisión de eventos.
- **Ciclo de vida:** siempre está en ejecución
- **Capacidad de repetición:** Repetición configurable.
- **Manejo de contrapresión:** Basado en Búfer
- **Caso de uso:** Eventos, Notificaciones, User actions, Navigation events, global broadcasts.
## **StateFlow vs SharedFlow**
### **StateFlow**
- **Titular del estado:** Siempre tiene el valor actual, representa el estado
- **Conflado:** Solo importa el valor más reciente, los valores intermedios se eliminan
- **Valor inicial requerido:** Debe proporcionar el estado inicial
- **Comportamiento pegajoso:** los nuevos coleccionistas obtienen inmediatamente el valor actual
- **Gestión del estado:** Diseñado para la gestión de la interfaz de usuario/estado de la aplicación
- **Naturaleza de los datos:** Recipiente del estado (pegajoso)
- **Valor actual:** Siempre tiene el valor actual
- **Caso de uso primario:** Gestión del estado IU
- **Comportamiento de nuevos observadores:** Los nuevos observadores obtienen el estado actual.
- **Cuando usarse:** estado de la IU (estados de carga, éxito, error), configuración de información, Información actual de usuarios, Formulario de datos, algún dato que represente el estado actual.
### **SharedFlow**
- **Flujo de eventos:** Diseñado para eventos/acciones, no estado
- **No se combina:** Todos los eventos emitidos se entregan (a menos que se desborde el búfer)
- **Sin valor inicial:** Comienza vacío, solo emite cuando se activa
- **Impulsados por eventos:** Los nuevos coleccionistas no tienen eventos anteriores (a menos que se configuren la repetición)
- **Acciones de una sola vez:** Perfecto para la navegación, tostadas, efectos secundarios
- **Naturaleza de los datos:** Flujo de eventos (No es pegajoso)
- **Valor actual:** Sin valor inicial
- **Caso de uso primario**: Acciones/Eventos de una sola vez
- **Comportamiento de nuevos observadores:** Los nuevos observadores obtienen solamente los eventos futuros.
- **Cuando usarse:** Eventos de navegación, mensajes Toast/Snackbar, Eventos del botón click, resultado de llamadas a API (Notificaciones de Exito/error), acciones o eventos de una sola vez.
## **Resumen de la guía de uso**
### **Cuando usar LiveData**
- Construcción de interfaz de usuario tradicional de Android (Vistas, no Componer)
- ¿Necesita una gestión automática del ciclo de vida
- Observación de estado simple
- Trabajar con componentes de arquitectura existentes
### **Cuando usar Flow**
- Tratamiento y transformaciones de datos
- Operaciones de capa de repositorio
- Consultas de base de datos
- Cadenas de llamadas API
- Secuencias de operadores complejas
- ¿Necesitas una ejecución perezosa
### **Cuando usar StateFlow**
- Gestión del estado de la interfaz de usuario con Compose
- Estado de configuración de la aplicación
- Datos de usuario actuales
- Estado de la forma
- Cualquier estado que debe persistir
- ¿Necesita actualizaciones de estado seguras para los hilos
### **Cuando usar SharedFlow**
- Eventos de una sola vez (navegación, tostadas)
- Transmisión de eventos
- Acciones de usuario
- Efectos secundarios
- Necesidad de notificar a varios observadores
- No se requiere persistencia estatal

# **Guía avanzada de Kotlin: conceptos intermedios y avanzados**

## **data class**
- **¿Qué es?**: Una clase especializada para almacenar datos. El compilador genera automáticamente `equals()`, `hashCode()`, `toString()`, `copy()` y `componentN()`.
- **¿Qué problema resuelve?**: Evita escribir boilerplate para clases de modelo.
- **¿Por qué fue creado?**: Para hacer más legible y segura la manipulación de datos simples.
- **¿Cómo funciona internamente?**: Se basa en el constructor primario y en las propiedades declaradas como `val` o `var`.
- **¿Qué conceptos previos necesito entender?**: Clases, constructores, propiedades, igualdad y copia de objetos.
- **¿Cuándo debería usarlo?**: Cuando representas DTOs, modelos de UI, entidades o estructuras de datos inmutables.
- **¿Cuándo no debería usarlo?**: Cuando la clase tiene lógica compleja, herencia o comportamiento importante más allá de guardar datos.
- **¿Qué alternativas existen?**: Clases normales, `record` en otros lenguajes, `sealed class` si necesitas representar estados.
- **Ventajas**: Menos código, comparaciones seguras, fácil copia.
- **Desventajas**: No es ideal para lógica de negocio.
- **Arquitectura**: Muy útil en capas de dominio, repositorio y UI.
- **Errores comunes**: Usarlo para objetos con lógica, modificar propiedades mutables sin pensar en la inmutabilidad.
- **Prueba**: Verificar igualdad, copia y serialización.
- **Depuración**: Revisar `toString()` y `copy()` cuando cambian valores inesperadamente.
- **Rendimiento, memoria y seguridad**: Muy eficiente; crea objetos simples y claros, reduce errores de comparación.
- **Entrevista**: “¿Qué diferencia hay entre una clase normal y una `data class`?”
- **Ejemplo real**: Un modelo `User(name, email, age)` para pantalla de perfil.
- **Explicación para junior**: “Sirve para guardar información de forma simple y segura.”
- **Explicación para no técnico**: “Es una plantilla para guardar datos como una ficha de una persona.”

```kotlin
data class User(val name: String, val age: Int)

val user1 = User("Ana", 25)
val user2 = user1.copy(age = 26)
println(user1)
```

## **sealed class**
- **¿Qué es?**: Una clase cerrada que solo puede ser heredada dentro del mismo archivo o módulo.
- **¿Qué problema resuelve?**: Permite modelar estados o resultados con un conjunto finito de opciones.
- **¿Por qué fue creado?**: Para manejar casos complejos de forma segura y expresiva.
- **¿Cómo funciona internamente?**: Cada subclase debe definirse en el mismo contexto, lo que facilita `when` exhaustivo.
- **¿Qué conceptos previos necesito entender?**: Herencia, clases abstractas, `when` y polimorfismo.
- **¿Cuándo debería usarlo?**: Para representar estados de carga/éxito/error, eventos o resultados de una operación.
- **¿Cuándo no debería usarlo?**: Si el número de posibles tipos es abierto o dinámico.
- **Alternativas**: Interfaces, enums, clases normales.
- **Ventajas**: Seguridad al manejar casos, código más mantenible.
- **Desventajas**: Menos flexible si cambias mucho el dominio.
- **Arquitectura**: Muy común en ViewModels, presenters y manejo de UI state.
- **Erroros comunes**: Olvidar agregar un `else` en `when` o no cubrir todos los casos.
- **Prueba**: Probar cada subclase y el `when` exhaustivo.
- **Depuración**: Revisar qué rama se está ejecutando en el `when`.
- **Rendimiento, memoria y seguridad**: Muy buena para seguridad de tipos y mantenibilidad; casi no añade coste significativo.
- **Entrevista**: “¿Por qué usar `sealed class` en vez de `enum`?”
- **Ejemplo real**: `sealed class UiState { object Loading; data class Success(val data: List<User>): UiState(); data class Error(val message: String): UiState() }`
- **Explicación para junior**: “Sirve para definir tipos de estado y evitar olvidarse de un caso.”
- **Explicación para no técnico**: “Es como decir: ‘esto solo puede tener estas 3 formas’.”

```kotlin
sealed class Result<out T> {
    data class Success<T>(val data: T) : Result<T>()
    data class Error(val exception: Throwable) : Result<Nothing>()
}
```

## **object y companion object**
- **¿Qué es?**: `object` define un singleton; `companion object` es un objeto asociado a una clase.
- **¿Qué problema resuelve?**: Evita crear múltiples instancias innecesarias y permite agrupar utilidades.
- **¿Por qué fue creado?**: Para simplificar el patrón singleton y los miembros estáticos.
- **¿Cómo funciona internamente?**: El objeto se crea una sola vez y se comparte en toda la aplicación.
- **¿Qué conceptos previos necesito entender?**: Instancias, clases, miembros estáticos, `this`.
- **¿Cuándo debería usarlo?**: Para utilidades, configuraciones globales, repositorios singleton o factories.
- **¿Cuándo no debería usarlo?**: Si necesitas múltiples instancias o dependencias complejas.
- **Alternativas**: Clases normales, DI, `lazy` o inyección de dependencias.
- **Ventajas**: Fácil de usar, acceso simple, evita instanciación extra.
- **Desventajas**: Puede dificultar el testing si se usa demasiado.
- **Arquitectura**: Se usa en servicios, helpers y managers, aunque en arquitectura limpia suele preferirse la inyección.
- **Errores comunes**: Colocar demasiada lógica en un `object`, hacerlo difícil de probar.
- **Prueba**: Usar mocks o sustituir dependencias con DI.
- **Depuración**: Revisa el ciclo de vida y el estado compartido del singleton.
- **Rendimiento, memoria y seguridad**: Muy ligero; cuidado con estados globales y concurrencia.
- **Entrevista**: “¿Cuál es la diferencia entre `object` y `companion object`?”
- **Ejemplo real**: Un objeto `SessionManager` para manejar la sesión del usuario.
- **Explicación para junior**: “Un `object` es como una única instancia global.”
- **Explicación para no técnico**: “Es una caja única que todos comparten.”

```kotlin
object Utils {
    fun formatName(name: String) = name.trim().uppercase()
}

class UserService {
    companion object {
        const val DEFAULT_ROLE = "user"
    }
}
```

## **extension functions**
- **¿Qué es?**: Permiten agregar funciones nuevas a clases existentes sin modificar su código.
- **¿Qué problema resuelve?**: Hace el código más expresivo y reutilizable.
- **¿Por qué fue creado?**: Para mejorar la legibilidad y evitar clases utilitarias innecesarias.
- **¿Cómo funciona internamente?**: Se compilan como funciones estáticas de utilidad con el receptor como parámetro implícito.
- **¿Qué conceptos previos necesito entender?**: Funciones, clases, `this`, scope y tipos.
- **¿Cuándo debería usarlo?**: Para añadir comportamiento útil a tipos de terceros, `String`, colecciones o clases de SDK.
- **¿Cuándo no debería usarlo?**: Si cambia mucho la semántica de la clase o si el código parece oculto.
- **Alternativas**: Clases utilitarias, wrappers, herencia.
- **Ventajas**: Código más limpio y expresivo.
- **Desventajas**: Pueden ser difíciles de encontrar si se usan demasiado.
- **Arquitectura**: Muy útiles en capas de dominio y presentación.
- **Errores comunes**: Sobrecargar con funciones poco claras o nombrarlas ambiguamente.
- **Prueba**: Probar casos normales y límite.
- **Depuración**: Revisar si el `this` está apuntando al objeto correcto.
- **Rendimiento, memoria y seguridad**: Sin coste notable; mejoran claridad y mantenimiento.
- **Entrevista**: “¿Qué es una extension function y por qué se usa?”
- **Ejemplo real**: `String.isEmailValid()` o `List<Int>.sumOrZero()`.
- **Explicación para junior**: “Te dejan añadir funciones a tipos que ya existen.”
- **Explicación para no técnico**: “Es como añadir una herramienta nueva a un objeto sin cambiarlo por dentro.”

```kotlin
fun String.removeSpaces() = this.replace(" ", "")
println("Hola Mundo".removeSpaces())
```

## **scope functions**
- **¿Qué es?**: Funciones como `let`, `run`, `also`, `apply`, `with` que cambian el contexto de ejecución.
- **¿Qué problema resuelve?**: Simplifican la inicialización y transformación de objetos.
- **¿Por qué fue creado?**: Para hacer el código más conciso y declarativo.
- **¿Cómo funcionan internamente?**: Ejecutan un bloque de código con un receptor implícito.
- **¿Qué conceptos previos necesito entender?**: Lambdas, `this`, `it`, funciones de orden superior.
- **¿Cuándo debería usarlo?**: Para configurar objetos, evitar `null`, transformar datos o cadenas de lógica corta.
- **¿Cuándo no debería usarlo?**: Si el bloque crece demasiado o se vuelve difícil de leer.
- **Alternativas**: Código clásico con variables intermedias.
- **Ventajas**: Menos boilerplate y mejor legibilidad en casos concretos.
- **Desventajas**: Pueden reducir claridad si se abusa de ellas.
- **Arquitectura**: Muy útiles en inicialización de modelos y binding de UI.
- **Errores comunes**: Usar `let` cuando debería ser `apply`, o sobreutilizar `run`.
- **Prueba**: Verificar el resultado final tras la transformación.
- **Depuración**: Revisar el scope y el receptor actual.
- **Rendimiento, memoria y seguridad**: Muy bajo impacto; mejoran claridad.
- **Entrevista**: “¿Cuál es la diferencia entre `let`, `also`, `apply` y `run`?”
- **Ejemplo real**: Inicializar un objeto `TextView` o transformar un `User` a `UserUiModel`.
- **Explicación para junior**: “Te ayudan a trabajar sobre un objeto de forma breve.”
- **Explicación para no técnico**: “Son atajos para hacer acciones sobre una cosa sin escribir mucho.”

```kotlin
val user = User("Luis", 30)
val result = user.let { "${it.name} tiene ${it.age} años" }
```

## **lambdas**
- **¿Qué es?**: Funciones anónimas que pueden pasarse como argumentos.
- **¿Qué problema resuelve?**: Permite escribir código más declarativo y flexible.
- **¿Por qué fue creado?**: Para soportar programación funcional y callbacks.
- **¿Cómo funciona internamente?**: Se convierten en objetos que implementan una interfaz funcional.
- **¿Qué conceptos previos necesito entender?**: Funciones, funciones de orden superior, parámetros y tipos.
- **¿Cuándo debería usarlo?**: En `map`, `filter`, `forEach`, eventos y callbacks.
- **¿Cuándo no debería usarlo?**: Si el bloque es muy largo o tiene demasiados efectos secundarios.
- **Alternativas**: Interfaces, clases anónimas, funciones nombradas.
- **Ventajas**: Código compacto y expresivo.
- **Desventajas**: Puede ser menos claro si se anida demasiado.
- **Arquitectura**: Muy comunes en repositorios, flujos y operaciones asincrónicas.
- **Errores comunes**: Escribir lambdas demasiado complejas o perder claridad del contexto.
- **Prueba**: Verificar el resultado con casos simples y límite.
- **Depuración**: Revisar el bloque y los valores capturados.
- **Rendimiento, memoria y seguridad**: Muy buenas; solo cuidado con cierres y capturas de estado.
- **Entrevista**: “¿Qué es una lambda y cómo se diferencia de una función normal?”
- **Ejemplo real**: `users.filter { it.isActive }`.
- **Explicación para junior**: “Son funciones pequeñas que puedes pasar como si fueran datos.”
- **Explicación para no técnico**: “Es una instrucción corta que puedes entregar a otra instrucción.”

```kotlin
val suma = { a: Int, b: Int -> a + b }
println(suma(2, 3))
```

## **generics**
- **¿Qué es?**: Parámetros de tipo que permiten crear estructuras reutilizables sobre distintos tipos.
- **¿Qué problema resuelve?**: Evita duplicar código para `List<Int>`, `List<String>` y similares.
- **¿Por qué fue creado?**: Para escribir código genérico y seguro.
- **¿Cómo funciona internamente?**: El compilador reemplaza el tipo en tiempo de compilación.
- **¿Qué conceptos previos necesito entender?**: Tipos, clases, interfaces y polimorfismo.
- **¿Cuándo debería usarlo?**: En colecciones, clases de utilidades, repositorios y componentes reutilizables.
- **¿Cuándo no debería usarlo?**: Cuando el tipo es muy específico o no aporta reutilización.
- **Alternativas**: Tipos concretos o `Any` con casteos.
- **Ventajas**: Reutilización, seguridad de tipos.
- **Desventajas**: Más complejidad en tipos y lectura.
- **Arquitectura**: Muy común en capas de datos y componentes genéricos.
- **Errores comunes**: Usar `Any` cuando un generic sería mejor, o restringir demasiado.
- **Prueba**: Verificar que compila con varios tipos.
- **Depuración**: Revisar las restricciones del tipo y los castings.
- **Rendimiento, memoria y seguridad**: Muy buenas; evitan casteos inseguro.
- **Entrevista**: “¿Qué es un tipo genérico y para qué sirve?”
- **Ejemplo real**: `class Box<T>(val value: T)`.
- **Explicación para junior**: “Permiten crear una estructura que funcione con muchos tipos.”
- **Explicación para no técnico**: “Es como una plantilla que puedes usar con distintos tipos de datos.”

```kotlin
class Box<T>(val value: T)
val boxInt = Box(10)
val boxString = Box("hola")
```

## **delegation**
- **¿Qué es?**: Técnica que permite delegar una implementación a otro objeto usando `by`.
- **¿Qué problema resuelve?**: Evita duplicar código y favorece composición.
- **¿Por qué fue creado?**: Para facilitar la composición frente a la herencia.
- **¿Cómo funciona internamente?**: La clase delega el comportamiento a la instancia indicada.
- **¿Qué conceptos previos necesito entender?**: Interfaces, composición, herencia, `by`.
- **¿Cuándo debería usarlo?**: Cuando una clase necesita implementar una interfaz con lógica simple.
- **¿Cuándo no debería usarlo?**: Si la implementación necesita lógica compleja o estado propio.
- **Alternativas**: Herencia, composición manual, wrappers.
- **Ventajas**: Menos código y mejor mantenimiento.
- **Desventajas**: Puede ser menos obvio para quien no conoce la técnica.
- **Arquitectura**: Muy útil para servicios, adaptadores o wrappers.
- **Errores comunes**: Delegar sin entender qué comportamiento se está reutilizando.
- **Prueba**: Probar que la clase delega correctamente el comportamiento.
- **Depuración**: Revisar la implementación del objeto delegado.
- **Rendimiento, memoria y seguridad**: Muy buen balance; suele ser ligero.
- **Entrevista**: “¿Qué es la delegación en Kotlin?”
- **Ejemplo real**: Delegar una interfaz `Logger` a una implementación concreta.
- **Explicación para junior**: “Le dices a una clase: ‘usa a otra para hacer esto.’”
- **Explicación para no técnico**: “Es como pedirle a otra persona que haga una tarea por ti.”

```kotlin
interface Printer { fun print(msg: String) }
class ConsolePrinter : Printer { override fun print(msg: String) = println(msg) }
class MessageService(private val printer: Printer) : Printer by printer
```

## **inline y reified**
- **¿Qué es?**: `inline` permite que el compilador copie el código de la función en el sitio de llamada; `reified` permite acceder al tipo real en funciones genéricas.
- **¿Qué problema resuelve?**: Evita overhead de funciones de orden superior y facilita trabajar con tipos genéricos.
- **¿Por qué fue creado?**: Para mejorar rendimiento de lambdas y simplificar operaciones con tipos.
- **¿Cómo funciona internamente?**: El compilador inyecta el cuerpo de la función en el punto de uso.
- **¿Qué conceptos previos necesito entender?**: Lambdas, funciones de orden superior, generics.
- **¿Cuándo debería usarlo?**: En funciones de alto rendimiento con lambdas, y en `when` con tipos genéricos.
- **¿Cuándo no debería usarlo?**: Si la función es grande o se usa mucho en múltiples puntos; puede aumentar el tamaño del bytecode.
- **Alternativas**: Funciones normales, `Class<T>` como parámetro.
- **Ventajas**: Menos overhead, más flexibilidad con tipos.
- **Desventajas**: Puede aumentar el tamaño del código compilado.
- **Arquitectura**: Se usa en bibliotecas, DSLs y APIs de rendimiento.
- **Errores comunes**: Usar `reified` sin `inline`, o abusar de `inline` en funciones grandes.
- **Prueba**: Comprobar que la función funciona con distintos tipos.
- **Depuración**: Revisar el bytecode si hay problemas de rendimiento.
- **Rendimiento, memoria y seguridad**: Muy útil para optimizar; cuidado con el tamaño del código.
- **Entrevista**: “¿Qué significa `inline` y `reified` en Kotlin?”
- **Ejemplo real**: `inline fun <reified T> isOfType(value: Any?) = value is T`.
- **Explicación para junior**: “Es una optimización para que el compilador no cree mucha estructura extra.”
- **Explicación para no técnico**: “Es como pegar el contenido directamente donde lo necesitas para hacerlo más rápido.”

```kotlin
inline fun <reified T> printType(value: Any) {
    println(value is T)
}
```

## **variance**
- **¿Qué es?**: La forma en que los tipos genéricos se relacionan entre sí: invarianza, covarianza y contravarianza.
- **¿Qué problema resuelve?**: Permite escribir APIs más flexibles sin perder seguridad de tipos.
- **¿Por qué fue creado?**: Para modelar relaciones entre jerarquías de tipos.
- **¿Cómo funciona internamente?**: Se expresa con `out` y `in` en los parámetros genéricos.
- **¿Qué conceptos previos necesito entender?**: Herencia, generics, `Any`, `Nothing`.
- **¿Cuándo debería usarlo?**: En colecciones y APIs que deben aceptar subtipos o supertipos.
- **¿Cuándo no debería usarlo?**: Si el tipo no tiene una relación clara con la jerarquía.
- **Alternativas**: Tipos concretos o funciones con castings.
- **Ventajas**: APIs más expresivas y seguras.
- **Desventajas**: Más complejidad conceptual.
- **Arquitectura**: Útil en bibliotecas e interfaces reutilizables.
- **Errores comunes**: Confundir `out` con `in` o usar tipos invariantes por defecto.
- **Prueba**: Probar la compatibilidad entre tipos y subtipos.
- **Depuración**: Revisar los límites del tipo y la jerarquía.
- **Rendimiento, memoria y seguridad**: No afecta mucho a rendimiento; mejora seguridad semántica.
- **Entrevista**: “¿Qué significa `out` y `in` en un tipo genérico?”
- **Ejemplo real**: `List<out Animal>` puede contener `Cat` o `Dog` si `Cat` y `Dog` son `Animal`.
- **Explicación para junior**: “Define si un tipo genérico puede ser usado como padre o como hijo.”
- **Explicación para no técnico**: “Es una regla para saber si una caja de datos puede aceptar cosas más generales o más específicas.”

```kotlin
class Box<out T>(val value: T)
```

## **collections**
- **¿Qué es?**: Conjuntos de datos como `List`, `Set`, `Map` y sus variantes mutables e inmutables.
- **¿Qué problema resuelve?**: Organiza y manipula grupos de datos de forma estándar.
- **¿Por qué fue creado?**: Para proporcionar estructuras de datos comunes y seguras.
- **¿Cómo funciona internamente?**: Se implementan con clases concretas y ofrecen operaciones de transformación, filtrado y recorrido.
- **¿Qué conceptos previos necesito entender?**: Arrays, loops, lambdas, `null safety`.
- **¿Cuándo debería usarlo?**: Siempre que trabajes con colecciones de datos.
- **¿Cuándo no debería usarlo?**: Si necesitas un modelo más especializado o muy grande para rendimiento extremo.
- **Alternativas**: Arrays, secuencias, bases de datos, estructuras propias.
- **Ventajas**: API rica, legible, reutilizable.
- **Desventajas**: Algunas operaciones pueden ser costosas si no se usan bien.
- **Arquitectura**: Muy usual en repositorios, DTOs y vistas.
- **Errores comunes**: Usar colecciones mutables cuando no se necesita, o iterar sin pensar en rendimiento.
- **Prueba**: Comprobar filtros, mapeos y ordenación.
- **Depuración**: Revisar contenido, índice y estado de los elementos.
- **Rendimiento, memoria y seguridad**: Hay impacto en memoria; las colecciones inmutables suelen ser más seguras.
- **Entrevista**: “¿Cuál es la diferencia entre `List`, `MutableList`, `Set` y `Map`?”
- **Ejemplo real**: Lista de productos en una pantalla de catálogo.
- **Explicación para junior**: “Son formas de guardar y trabajar grupos de datos.”
- **Explicación para no técnico**: “Son listas o grupos de cosas organizadas.”

```kotlin
val numbers = listOf(1, 2, 3, 4)
val doubled = numbers.map { it * 2 }
```

## **Result**
- **¿Qué es?**: Un tipo de retorno que representa éxito o fallo sin depender de excepciones.
- **¿Qué problema resuelve?**: Hace explícito el resultado de una operación y evita lanzar excepciones para control normal.
- **¿Por qué fue creado?**: Para modelar errores de forma más expresiva en APIs modernas.
- **¿Cómo funciona internamente?**: Generalmente se implementa con `Success` y `Error` o `Ok`/`Err`.
- **¿Qué conceptos previos necesito entender?**: `sealed class`, funciones, manejo de errores, excepciones.
- **¿Cuándo debería usarlo?**: En operaciones de negocio, validaciones, llamadas a red y lógica de dominio.
- **¿Cuándo no debería usarlo?**: Si el error es excepcional y no forma parte del flujo normal.
- **Alternativas**: `throw`, `try/catch`, `Either`, `sealed class`.
- **Ventajas**: Hace el flujo más claro y predecible.
- **Desventajas**: Puede aumentar el código si se usa en exceso.
- **Arquitectura**: Muy útil en repositorios y casos de uso.
- **Errores comunes**: Mezclar `Result` con excepciones sin criterio.
- **Prueba**: Validar los casos de éxito y fallo.
- **Depuración**: Revisar el valor retornado y el tipo de error.
- **Rendimiento, memoria y seguridad**: Muy bueno para seguridad de control; el coste es bajo.
- **Entrevista**: “¿Por qué usar `Result` en vez de lanzar excepciones?”
- **Ejemplo real**: Una función que obtiene un usuario desde internet y devuelve `Result<User, Error>`.
- **Explicación para junior**: “Devuelve si salió bien o si falló, de forma explícita.”
- **Explicación para no técnico**: “Es como recibir un mensaje de ‘todo salió bien’ o ‘algo falló’.”

```kotlin
fun parseAge(input: String): Result<Int> =
    if (input.toIntOrNull() != null) Result.success(input.toInt())
    else Result.failure(IllegalArgumentException("Edad inválida"))
```

## **null safety**
- **¿Qué es?**: El sistema de Kotlin para evitar errores por `null` mediante tipos no nulos y mecanismos de comprobación.
- **¿Qué problema resuelve?**: Evita `NullPointerException` en tiempo de ejecución.
- **¿Por qué fue creado?**: Para hacer el código más seguro desde el compilador.
- **¿Cómo funciona internamente?**: El compilador exige marcar explícitamente los tipos como nullable con `?`.
- **¿Qué conceptos previos necesito entender?**: Variables, tipos, `?`, `?.`, `?:`, `!!`, `let`.
- **¿Cuándo debería usarlo?**: Siempre que un valor pueda no existir.
- **¿Cuándo no debería usarlo?**: No se debe sobreusar `!!` porque puede romper la seguridad.
- **Alternativas**: Comprobar manualmente, excepciones, patrones de Optional.
- **Ventajas**: Menos fallos en runtime, código más robusto.
- **Desventajas**: Requiere más disciplina y puede producir código más verboso.
- **Arquitectura**: Es clave en ViewModels, repositorios y capas de datos.
- **Errores comunes**: Usar `!!` innecesariamente o no manejar valores nulos en entradas externas.
- **Prueba**: Probar casos con `null` y sin `null`.
- **Depuración**: Revisar el flujo de datos y los puntos donde un valor puede ser nulo.
- **Rendimiento, memoria y seguridad**: Mejora seguridad y reduce crash; muy poco coste.
- **Entrevista**: “¿Qué diferencia hay entre `?.`, `?:` y `!!`?”
- **Ejemplo real**: Manejar un usuario no autenticado o un resultado de red vacío.
- **Explicación para junior**: “Indica qué valores pueden no existir y cómo manejarlos.”
- **Explicación para no técnico**: “Evita que un programa falle cuando algo no tiene valor.”

```kotlin
val nombre: String? = null
val longitud = nombre?.length ?: 0
```

# **Coroutines en Kotlin**

## **suspend**
- **¿Qué es?**: Una función que puede pausar su ejecución sin bloquear el hilo.
- **¿Qué problema resuelve?**: Permite escribir código asíncrono de forma secuencial.
- **¿Por qué fue creado?**: Para simplificar tareas asincrónicas y evitar callbacks.
- **¿Cómo funciona internamente?**: Se compila en máquinas de estado que reanudan el flujo en el punto adecuado.
- **¿Qué conceptos previos necesito entender?**: Hilos, async, callbacks, `coroutineScope`.
- **¿Cuándo debería usarlo?**: En llamadas de red, bases de datos y operaciones largas.
- **¿Cuándo no debería usarlo?**: En operaciones muy cortas o cuando ya se está en un contexto síncrono simple.
- **Alternativas**: Threads, callbacks, RxJava.
- **Ventajas**: Código limpio, mejor rendimiento y menor consumo de recursos.
- **Desventajas**: Puede ser complejo si no se entienden los contextos.
- **Arquitectura**: Muy importante en ViewModel, repositorios y UI.
- **Errores comunes**: Llamar a funciones suspend desde un hilo bloqueante o no manejar excepciones.
- **Prueba**: Usar `runBlocking` y `MainDispatcherRule` en tests.
- **Depuración**: Revisar stack traces y `Job`/`CoroutineExceptionHandler`.
- **Rendimiento, memoria y seguridad**: Mejor escalabilidad; evita bloquear hilos.
- **Entrevista**: “¿Qué hace `suspend`?”
- **Ejemplo real**: Obtener datos de una API sin bloquear la pantalla.
- **Explicación para junior**: “Permite detener una tarea temporalmente para seguir con otra.”
- **Explicación para no técnico**: “Es como pausar una tarea para hacer otra más importante.”

```kotlin
suspend fun cargarDatos(): String {
    delay(1000)
    return "Datos"
}
```

## **coroutineScope**
- **¿Qué es?**: Crea un scope que espera a que todas sus corrutinas hijas terminen.
- **¿Qué problema resuelve?**: Mantiene un flujo estructurado y limpio.
- **¿Por qué fue creado?**: Para evitar fugas y corrutinas huérfanas.
- **¿Cómo funciona internamente?**: El scope se cancela si falla alguna tarea hija o si el padre termina.
- **¿Qué conceptos previos necesito entender?**: `suspend`, `launch`, `async`, structured concurrency.
- **¿Cuándo debería usarlo?**: Cuando necesitas ejecutar varias corrutinas relacionadas y esperar a que todas terminen.
- **¿Cuándo no debería usarlo?**: Si quieres que una hija continue aunque otra falle.
- **Alternativas**: `supervisorScope`, `GlobalScope` (no recomendada).
- **Ventajas**: Control claro del ciclo de vida.
- **Desventajas**: Si una falla, el resto se cancela.
- **Arquitectura**: Muy útil en casos de uso y repositorios.
- **Errores comunes**: Usar `GlobalScope` o ignorar cancelaciones.
- **Prueba**: Verificar que las corrutinas hijas terminan o se cancelan.
- **Depuración**: Revisar el `Job` padre y los hijos.
- **Rendimiento, memoria y seguridad**: Ayuda a evitar fugas y comportamientos inesperados.
- **Entrevista**: “¿Qué diferencia hay entre `coroutineScope` y `supervisorScope`?”
- **Ejemplo real**: Cargar datos de varios endpoints en paralelo y esperar todos.
- **Explicación para junior**: “Es un contenedor que agrupa tareas relacionadas.”
- **Explicación para no técnico**: “Es como un grupo de tareas que deben terminar juntas.”

## **supervisorScope**
- **¿Qué es?**: Un scope que permite que una corrutina hija falle sin cancelar automáticamente a las demás.
- **¿Qué problema resuelve?**: Útil cuando una tarea secundaria no debe arruinar el flujo completo.
- **¿Por qué fue creado?**: Para situaciones donde se desea aislamiento de errores entre tareas hijas.
- **¿Cómo funciona internamente?**: Cada hijo tiene su propia política de fallo.
- **¿Qué conceptos previos necesito entender?**: `coroutineScope`, cancelación, excepciones.
- **¿Cuándo debería usarlo?**: En procesos independientes, logs, métricas o recopilación paralela.
- **¿Cuándo no debería usarlo?**: Cuando la falla de una tarea debería detener el resto del flujo.
- **Alternativas**: `coroutineScope`, manejo manual de excepciones.
- **Ventajas**: Mayor resiliencia y control granular.
- **Desventajas**: Puede ocultar fallos si se usa sin criterio.
- **Arquitectura**: Bueno para componentes de observabilidad o recolección de datos.
- **Errores comunes**: Usarlo para todo y perder la consistencia del flujo.
- **Prueba**: Comprobar que una falla no cancela a las demás.
- **Depuración**: Revisar excepciones de cada hija individualmente.
- **Rendimiento, memoria y seguridad**: Muy útil para robustez; cuidado con errores silenciosos.
- **Entrevista**: “¿Qué hace `supervisorScope`?”
- **Ejemplo real**: Actualizar métricas y guardar datos aunque una parte falle.
- **Explicación para junior**: “Permite que una tarea falle sin arruinar a las demás.”
- **Explicación para no técnico**: “Es como decir: ‘si una parte falla, las demás siguen trabajando’.”

## **async**
- **¿Qué es?**: Inicia una corrutina concurrente y devuelve un `Deferred` con el resultado futuro.
- **¿Qué problema resuelve?**: Permite ejecutar tareas en paralelo y esperar por sus resultados cuando se necesiten.
- **¿Por qué fue creado?**: Para estructurar operaciones concurrentes con más control.
- **¿Cómo funciona internamente?**: Ejecuta el bloque y devuelve un handle que se puede `await`.
- **¿Qué conceptos previos necesito entender?**: `launch`, `suspend`, `Deferred`, `await`.
- **¿Cuándo debería usarlo?**: Cuando necesitas resultados de varias operaciones concurrentes.
- **¿Cuándo no debería usarlo?**: Si solo quieres disparar una tarea sin esperar un valor.
- **Alternativas**: `launch` con callbacks o `Flow`.
- **Ventajas**: Paralelismo claro y resultados esperados.
- **Desventajas**: Requiere más cuidado con cancelaciones y excepciones.
- **Arquitectura**: Muy útil en repositorios y casos de uso de múltiples datos.
- **Errores comunes**: Olvidar `await`, o usarlo para tareas independientes sin scope adecuado.
- **Prueba**: Verificar resultados parciales y cancelaciones.
- **Depuración**: Revisar `Deferred` y el punto de `await`.
- **Rendimiento, memoria y seguridad**: Mejora el rendimiento cuando hay trabajo paralelo.
- **Entrevista**: “¿Qué diferencia hay entre `launch` y `async`?”
- **Ejemplo real**: Cargar perfil y preferencias en paralelo.
- **Explicación para junior**: “Sirve para ejecutar tareas en paralelo y después recoger el resultado.”
- **Explicación para no técnico**: “Es como pedir varias cosas al mismo tiempo y recogerlas después.”

## **launch**
- **¿Qué es?**: Inicia una corrutina sin devolver un resultado futuro.
- **¿Qué problema resuelve?**: Ejecutar tareas en segundo plano sin bloquear el hilo principal.
- **¿Por qué fue creado?**: Para tareas de lado efecto y trabajo asíncrono no orientado a resultados.
- **¿Cómo funciona internamente?**: Crea un `Job` y lo ejecuta en un contexto dado.
- **¿Qué conceptos previos necesito entender?**: `Job`, `scope`, `suspend`.
- **¿Cuándo debería usarlo?**: Para guardar datos, navegación, logs o operaciones que no devuelven un valor.
- **¿Cuándo no debería usarlo?**: Si necesitas un valor concreto o esperar el resultado.
- **Alternativas**: `async` o funciones suspend normales.
- **Ventajas**: Muy simple para tareas de fondo.
- **Desventajas**: Menos expresivo si necesitas el resultado.
- **Arquitectura**: Muy común en ViewModel y UI.
- **Errores comunes**: No cancelar bien la corrutina o lanzar tareas sin control.
- **Prueba**: Verificar el efecto secundario y la cancelación.
- **Depuración**: Revisar el `Job` y el estado de la corrutina.
- **Rendimiento, memoria y seguridad**: Muy útil; cuidado con fugas y ejecuciones no controladas.
- **Entrevista**: “¿Cuándo usar `launch` y cuándo `async`?”
- **Ejemplo real**: Enviar un evento de analytics o actualizar un contador.
- **Explicación para junior**: “Sirve para lanzar una tarea de fondo.”
- **Explicación para no técnico**: “Es como encender una tarea en segundo plano.”

## **Dispatchers**
- **¿Qué es?**: Determinan en qué hilo o pool de hilos se ejecuta una corrutina.
- **¿Qué problema resuelve?**: Permite separar trabajo de CPU, I/O y UI.
- **¿Por qué fue creado?**: Para controlar el contexto de ejecución de forma segura.
- **¿Cómo funciona internamente?**: Cada dispatcher tiene una política concreta de ejecución.
- **¿Qué conceptos previos necesito entender?**: Hilos, Main, IO, Default, Unconfined.
- **¿Cuándo debería usarlo?**: Para no bloquear la UI y utilizar el hilo correcto según la operación.
- **¿Cuándo no debería usarlo?**: No es necesario si la operación es simple o si se está en un contexto adecuado.
- **Alternativas**: Hilos manuales o `Handler` en Android antiguo.
- **Ventajas**: Mejor rendimiento y organización.
- **Desventajas**: Si se usa mal, se pueden introducir bugs de concurrencia.
- **Arquitectura**: Fundamental en Android y servidores.
- **Errores comunes**: Hacer trabajo de I/O en Main, o trabajo pesado en IO sin pensar en la carga.
- **Prueba**: Verificar que las operaciones se ejecutan en el dispatcher adecuado.
- **Depuración**: Revisar el contexto y el hilo donde se ejecuta.
- **Rendimiento, memoria y seguridad**: Muy importante para evitar bloqueos y problemas de UI.
- **Entrevista**: “¿Qué diferencia hay entre `Dispatchers.Main`, `IO` y `Default`?”
- **Ejemplo real**: Llamar a una API en `IO` y actualizar la UI en `Main`.
- **Explicación para junior**: “Indican en qué hilo debe correr la tarea.”
- **Explicación para no técnico**: “Es como decirle a la tarea en qué ‘canal’ debe trabajar.”

## **cancellation**
- **¿Qué es?**: La forma en que una corrutina se detiene de manera cooperativa.
- **¿Qué problema resuelve?**: Evita tareas innecesarias y fugas cuando la pantalla cambia o el usuario cancela una acción.
- **¿Por qué fue creado?**: Para controlar el ciclo de vida de manera segura y eficiente.
- **¿Cómo funciona internamente?**: Se usa `CancellationException` y se revisa el estado de cancelación en puntos de suspensión.
- **¿Qué conceptos previos necesito entender?**: `Job`, `suspend`, `launch`, scopes.
- **¿Cuándo debería usarlo?**: Siempre que exista una operación que pueda cancelarse.
- **¿Cuándo no debería usarlo?**: No hace falta en operaciones inmediatas o sin posibilidad de interrupción.
- **Alternativas**: Threads manuales, flags de stop.
- **Ventajas**: Menos recursos desperdiciados y mejor UX.
- **Desventajas**: Puede ser difícil de depurar si no se maneja bien.
- **Arquitectura**: Crítico en Android y apps con ciclos de vida.
- **Errores comunes**: Bloquear la corrutina con código que no respeta la cancelación.
- **Prueba**: Comprobar que el trabajo se cancela y no sigue ejecutándose.
- **Depuración**: Revisar si la corrutina recibió cancelación y en qué punto.
- **Rendimiento, memoria y seguridad**: Mejora eficiencia y evita procesos zombis.
- **Entrevista**: “¿Cómo se cancela una corrutina?”
- **Ejemplo real**: Cancelar una búsqueda al escribir otra nueva.
- **Explicación para junior**: “Se detiene cuando ya no hace falta.”
- **Explicación para no técnico**: “Es como parar una tarea cuando el usuario cambia de opinión.”

## **structured concurrency**
- **¿Qué es?**: Modelo de corrutinas en el que las tareas viven dentro de un scope con relación padre-hijo.
- **¿Qué problema resuelve?**: Evita fugas y garantiza que las tareas se cancelen y terminen juntas.
- **¿Por qué fue creado?**: Para que el manejo de concurrencia sea más predecible.
- **¿Cómo funciona internamente?**: El padre gestiona la vida de los hijos y los cancela si el padre termina.
- **¿Qué conceptos previos necesito entender?**: Scopes, `launch`, `async`, `Job`.
- **¿Cuándo debería usarlo?**: En toda app que use corrutinas bien estructuradas.
- **¿Cuándo no debería usarlo?**: Si se necesita un lifetime independiente de la UI o del caso de uso.
- **Alternativas**: Scopes manuales o `GlobalScope` (menos recomendable).
- **Ventajas**: Menos errores y mejor mantenimiento.
- **Desventajas**: Requiere disciplina para usar correctamente los scopes.
- **Arquitectura**: Es una de las bases para ViewModel, repositorios y casos de uso.
- **Errores comunes**: Crear corrutinas fuera del scope correcto.
- **Prueba**: Verificar que los hijos terminan con el padre.
- **Depuración**: Revisar el árbol de `Job` y los scopes activos.
- **Rendimiento, memoria y seguridad**: Muy positivo para estabilidad y limpieza.
- **Entrevista**: “¿Qué es structured concurrency y por qué es importante?”
- **Ejemplo real**: Un caso de uso que lanza varias consultas y termina cuando el usuario sale de la pantalla.
- **Explicación para junior**: “Las tareas van dentro de un contexto que las controla.”
- **Explicación para no técnico**: “Es como organizar varias tareas en un mismo grupo para que se gestionen bien.”

# **Flow en Kotlin**

## **Flow**
- **¿Qué es?**: Un flujo reactivo frío que emite valores a lo largo del tiempo.
- **¿Qué problema resuelve?**: Permite trabajar con secuencias asíncronas y reactivas de forma declarativa.
- **¿Por qué fue creado?**: Para reemplazar callbacks y simplificar la programación reactiva.
- **¿Cómo funciona internamente?**: Se ejecuta cuando se colecta y cada collector obtiene su propia ejecución.
- **¿Qué conceptos previos necesito entender?**: Corrutinas, `suspend`, `cold vs hot`, operadores de transformación.
- **¿Cuándo debería usarlo?**: Para llamadas de red, bases de datos, streams y estados reactivos.
- **¿Cuándo no debería usarlo?**: Si solo necesitas un valor único y simple.
- **Alternativas**: LiveData, callbacks, RxJava, Channels.
- **Ventajas**: Muy flexible, composable y escalable.
- **Desventajas**: Requiere aprender operadores y lifecycle.
- **Arquitectura**: Muy común en repositorios, ViewModel y capa de UI.
- **Errores comunes**: No cancelar la recolección, emitir desde Main sin cuidado, usar `flow` para estados simples.
- **Prueba**: Usar `flow` testing y `runTest`.
- **Depuración**: Revisar emisiones, operadores y cancelaciones.
- **Rendimiento, memoria y seguridad**: Muy eficiente; cuidado con emisiones frecuentes y buffering.
- **Entrevista**: “¿Qué es un `Flow` y cómo se diferencia de una corrutina normal?”
- **Ejemplo real**: Obtener resultados paginados de una API.
- **Explicación para junior**: “Es un canal de datos que puede emitir varios valores con el tiempo.”
- **Explicación para no técnico**: “Es como un río de datos que va llegando poco a poco.”

```kotlin
fun numbers(): Flow<Int> = flow {
    for (i in 1..3) {
        delay(100)
        emit(i)
    }
}
```

## **StateFlow**
- **¿Qué es?**: Un `Flow` caliente que siempre tiene un valor actual.
- **¿Qué problema resuelve?**: Modelar estados de UI o estado de la app de forma reactiva.
- **¿Por qué fue creado?**: Para manejar estado compartido y actualizado de forma segura.
- **¿Cómo funciona internamente?**: Mantiene un valor actual y lo entrega a nuevos collectors.
- **¿Qué conceptos previos necesito entender?**: `Flow`, `MutableStateFlow`, `collect`.
- **¿Cuándo debería usarlo?**: Para pantallas con estados de carga, error, éxito y datos actuales.
- **¿Cuándo no debería usarlo?**: Para eventos de una sola vez como navegación o toast.
- **Alternativas**: `LiveData`, `SharedFlow`, `Flow` simple.
- **Ventajas**: Muy útil para UI state y Compose.
- **Desventajas**: No es ideal para eventos de una vez.
- **Arquitectura**: Muy usado en ViewModels y componentes de UI.
- **Errores comunes**: No inicializar el estado o emitir demasiados cambios.
- **Prueba**: Verificar el último valor y los cambios de estado.
- **Depuración**: Revisar el valor actual y los collectors.
- **Rendimiento, memoria y seguridad**: Muy bueno para estado compartido; evita pérdidas de eventos.
- **Entrevista**: “¿Qué diferencia hay entre `StateFlow` y `SharedFlow`?”
- **Ejemplo real**: Un estado de pantalla `Loading`, `Success`, `Error`.
- **Explicación para junior**: “Es un flujo que siempre recuerda el último valor.”
- **Explicación para no técnico**: “Es como un tablero que siempre muestra el estado actual.”

```kotlin
val state = MutableStateFlow("Inicio")
state.value = "Cargando"
```

## **SharedFlow**
- **¿Qué es?**: Un `Flow` caliente pensado para eventos o acciones que no necesitan persistir un estado.
- **¿Qué problema resuelve?**: Notificar a múltiples consumidores sobre eventos únicos o rápidos.
- **¿Por qué fue creado?**: Para casos de navegación, toast, clicks y acciones de una sola vez.
- **¿Cómo funciona internamente?**: Mantiene un buffer y entrega eventos a sus subscribers.
- **¿Qué conceptos previos necesito entender?**: `Flow`, `StateFlow`, eventos.
- **¿Cuándo debería usarlo?**: Para navegación, mensajes cortos, efectos secundarios.
- **¿Cuándo no debería usarlo?**: Si necesitas conservar el estado actual.
- **Alternativas**: `Channel`, `LiveData`, `StateFlow`.
- **Ventajas**: Muy útil para eventos compartidos.
- **Desventajas**: Menos adecuado para representar estado.
- **Arquitectura**: Muy útil en navegación y comunicación entre capas.
- **Errores comunes**: Usarlo para estados o ignorar el buffer y el desbordamiento.
- **Prueba**: Verificar que se reciben los eventos correctos.
- **Depuración**: Revisar si se perdieron eventos por buffer o cancelación.
- **Rendimiento, memoria y seguridad**: Bueno para eventos; si se usa mal puede haber pérdida de eventos.
- **Entrevista**: “¿Cuándo elegir `SharedFlow` sobre `StateFlow`?”
- **Ejemplo real**: Mostrar un `Toast` luego de guardar datos.
- **Explicación para junior**: “Sirve para eventos que ocurren una vez.”
- **Explicación para no técnico**: “Es como enviar una notificación que no debe quedarse guardada.”

## **Channels**
- **¿Qué es?**: Un canal de comunicación entre corrutinas basado en cola.
- **¿Qué problema resuelve?**: Permite enviar y recibir mensajes de forma ordenada entre corrutinas.
- **¿Por qué fue creado?**: Para modelar comunicación asíncrona entre productores y consumidores.
- **¿Cómo funciona internamente?**: Usa buffers y operaciones `send`/`receive`.
- **¿Qué conceptos previos necesito entender?**: Corrutinas, `Flow`, concurrencia, cola.
- **¿Cuándo debería usarlo?**: En pipelines de trabajo, workers o comunicación entre coroutines.
- **¿Cuándo no debería usarlo?**: Si ya tienes un `Flow` simple y suficiente.
- **Alternativas**: `Flow`, `SharedFlow`, `BlockingQueue`.
- **Ventajas**: Comunicación flexible y clara.
- **Desventajas**: Más complejo que `Flow` para casos simples.
- **Arquitectura**: Útil en backends, workers y procesos de eventos.
- **Errores comunes**: Olvidar cerrar el canal o bloquearse por un buffer lleno.
- **Prueba**: Verificar orden y recepción de mensajes.
- **Depuración**: Revisar si hay deadlock o buffer saturado.
- **Rendimiento, memoria y seguridad**: Muy buenos para comunicación; cuidado con memoria del buffer.
- **Entrevista**: “¿Qué diferencia hay entre `Flow` y `Channel`?”
- **Ejemplo real**: Un productor que genera tareas y un consumidor que las procesa.
- **Explicación para junior**: “Sirven para pasar mensajes entre tareas.”
- **Explicación para no técnico**: “Es como una cinta transportadora de mensajes entre procesos.”

## **cold vs hot flow**
- **¿Qué es?**: Distinción entre flujos que solo comienzan cuando alguien los recolecta (`cold`) y los que ya están activos (`hot`).
- **¿Qué problema resuelve?**: Ayuda a entender cuándo se ejecuta el productor y cómo se comparten los valores.
- **¿Por qué fue creado?**: Para modelar diferentes necesidades de reactividad y consumo.
- **¿Cómo funciona internamente?**: En `cold` cada collector tiene su propia ejecución; en `hot` el productor es compartido.
- **¿Qué conceptos previos necesito entender?**: `Flow`, `StateFlow`, `SharedFlow`, `collect`.
- **¿Cuándo debería usarlo?**: Para elegir el tipo correcto de flujo según el caso de uso.
- **¿Cuándo no debería usarlo?**: No es un concepto para usar como solución por sí mismo; hay que aplicarlo al diseño.
- **Alternativas**: Streams tradicionales, observables, eventos directos.
- **Ventajas**: Permite controlar eficiencia y comportamiento de consumo.
- **Desventajas**: Requiere entender bien el modelo.
- **Arquitectura**: Muy importante en diseño de repositorios y UI state.
- **Errores comunes**: Esperar que un `Flow` frío se comporte como uno caliente.
- **Prueba**: Verificar si se dispara al colectar o si permanece activo.
- **Depuración**: Revisar si hay múltiples ejecuciones o si se comparte el estado.
- **Rendimiento, memoria y seguridad**: Impacta mucho en consumo y memoria; elegir bien reduce problemas.
- **Entrevista**: “¿Qué diferencia hay entre un `cold flow` y un `hot flow`?”
- **Ejemplo real**: `Flow` de datos de API vs `StateFlow` de estado de pantalla.
- **Explicación para junior**: “Un flujo frío empieza cuando lo escuchas; uno caliente ya está vivo.”
- **Explicación para no técnico**: “Es como un canal que solo se activa cuando alguien lo mira, versus uno que ya está encendido.”

# **Resumen práctico para estudiar**
- Empieza por `data class`, `sealed class`, `object`, `extension functions` y `null safety`.
- Después domina `lambdas`, `generics` y `collections`.
- Luego estudia corrutinas: `suspend`, `launch`, `async`, `Dispatchers`, `cancellation` y `structured concurrency`.
- Finalmente entiende `Flow`, `StateFlow`, `SharedFlow`, `Channels` y la diferencia entre `cold` y `hot`.



# **Crear un archivo object:**
```Kotlin
object Sumar {

      fun sumar(numero: Int): Int{
          var numero = numero
          numero = numero + 1
          return numero
      }
}
```



## **Importaciones**
```Kotlin
// ViewModel and LiveData
implementation 'androidx.lifecycle:lifecycle-extensions:2.1.0'
annotationProcessor 'androidx.lifecycle:lifecycle-compiler:2.1.0'
```

# **StateFlow y Shared Flow**
StateFlow y SharedFlow son [API de Flow] que permiten que los flujos emitan actualizaciones de estado y valores a varios consumidores de manera óptima.
## **StateFlow**
[**StateFlow**](https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-state-flow/ "https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-state-flow/") es un flujo observable contenedor de estados que emite los estados actual y nuevo actualizaciones a sus recopiladores. El valor del estado actual también se puede leer su [**value**](https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-state-flow/value.html "https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-state-flow/value.html") propiedad. Para actualizar el estado y enviarlo al flujo, asigna un nuevo valor a la propiedad value de la clase [*MutableStateFlow*](https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-mutable-state-flow/index.html "https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-mutable-state-flow/index.html").

En Android, StateFlow es una excelente opción para clases que necesitan mantener un estado observable que muta.

De acuerdo con los ejemplos de los [flujos de Kotlin][API de Flow], se puede exponer un StateFlow del LatestNewsViewModel para que View pueda detectar actualizaciones de estado de la IU y, de manera inherente, permitir que el estado de la pantalla se conserve después de hacer cambios en la configuración.

```kotlin
class LatestNewsViewModel(
      private val newsRepository: NewsRepository
) : ViewModel() {
      // Backing property to avoid state updates from other classes
      private val _uiState = MutableStateFlow(LatestNewsUiState.Success(emptyList()))
      // The UI collects from this StateFlow to get its state updates
      val uiState: StateFlow<LatestNewsUiState> = _uiState
      init {
          viewModelScope.launch {
              newsRepository.favoriteLatestNews
                  // Update View with the latest favorite news
                  // Writes to the value property of MutableStateFlow,
                  // adding a new element to the flow and updating all
                  // of its collectors
.collect { favoriteNews ->
                      _uiState.value = LatestNewsUiState.Success(favoriteNews)
                  }
          }
      }
}

// Represents different states for the LatestNews screen

sealed class LatestNewsUiState {

      data class Success(val news: List<ArticleHeadline>): LatestNewsUiState()

      data class Error(val exception: Throwable): LatestNewsUiState()

}
```

La clase responsable de actualizar un *MutableStateFlow* es el productor, mientras que todas las clases que se recopilan de **StateFlow** son consumidores. A diferencia de un flujo *frío* compilado con el compilador de **flow**, un **StateFlow** es *caliente*; recopilar datos del flujo no activa ningún código de productor. Un objeto **StateFlow** siempre se encuentra activo y en la memoria, y se vuelve apto para la recolección de elementos no utilizados solo cuando no hay otras referencias a él en la raíz de otra recolección.

Cuando un consumidor nuevo comienza a recopilarse desde el flujo, recibe el último estado del flujo y todos los estados posteriores. Puedes encontrar este comportamiento en otras clases observables, como [**LiveData**](https://developer.android.com/topic/libraries/architecture/livedata?hl=es-419 "https://developer.android.com/topic/libraries/architecture/livedata?hl=es-419").

El **View** detecta un elemento **StateFlow** de la misma manera que cualquier otro flujo:
```kotlin
class LatestNewsActivity : AppCompatActivity() {
      private val latestNewsViewModel = // getViewModel()
      override fun onCreate(savedInstanceState: Bundle?) {
...
          // Start a coroutine in the lifecycle scope
          lifecycleScope.launch {
              // repeatOnLifecycle launches the block in a new coroutine every time the
              // lifecycle is in the STARTED state (or above) and cancels it when it's STOPPED.
              repeatOnLifecycle(Lifecycle.State.STARTED) {
                  // Trigger the flow and start listening for values.
                  // Note that this happens when lifecycle is STARTED and stops
                  // collecting when the lifecycle is STOPPED
                  latestNewsViewModel.uiState.collect { uiState ->
                      // New value received
                      when (uiState) {
                          is LatestNewsUiState.Success -> showFavoriteNews(uiState.news)
                          is LatestNewsUiState.Error -> showError(uiState.exception)
                      }
                  }
              }
          }
      }
}
```


# **Preguntas para entrevista.**
¿Qué lenguajes de programación manejas?

¿Qué patrones de diseño conoces?

¿Opciones para almacenamiento de datos de la app?

- **Almacenamiento específico de la app**
- **Almacenamiento compartido**
- **Preferencias**
- **Bases de datos**

¿Qué librerías manejas?

¿Cómo haces una consulta Restful?

¿Diferencias entre constraint layout y linear layout?

¿Qué es un navigation component y sus componentes?

¿Qué es una corrutina?

¿Conoces viewBinding y dataBinding?

¿Qué componentes gráficos se usa para hacer una ventana flotante?

¿Conoces LiveData y para qué sirve?

¿Manejas Git?

¿Diferencia entre un fragmento y una activity?

¿Manejas Firebase, que servicios de Firebase has usado?

¿Conoces la inyección de dependencias, con que la haces?

[API de Flow]: https://developer.android.com/kotlin/flow?hl=es-419 "https://developer.android.com/kotlin/flow?hl=es-419"

[NavController]: https://developer.android.com/reference/androidx/navigation/NavController?hl=es-419 "https://developer.android.com/reference/androidx/navigation/NavController?hl=es-419"

[**NavController**]: http://d.android.com/reference/androidx/navigation/NavController?hl=es-419 "http://d.android.com/reference/androidx/navigation/NavController?hl=es-419"

[ref1]: Aspose.Words.4e276513-788f-4af8-9e8b-9cd31daeee0c.018.png
[ref2]: Aspose.Words.4e276513-788f-4af8-9e8b-9cd31daeee0c.020.png
[ref3]: Aspose.Words.4e276513-788f-4af8-9e8b-9cd31daeee0c.026.png
[ref4]: Aspose.Words.4e276513-788f-4af8-9e8b-9cd31daeee0c.028.png

# **data class**
Esta clase es principalmente usada para almacenar información, para este tipo de clases el compilador automaticamente genera funciones de miembro adicionales que le permiten imprimir una instancia de salida leíble, comparar instancias, copiar instancias y más.

```kotlin
data class User(val name: String, val age: Int)
```

El compilador automáticamente deriva los siguienes miembros de todas la propiedades declaradas en el constructor primario:
- Par `equals()`/`hashCode()`
- `toString()` de la forma `"User(name=John, age=42)"`
- Funciones `componentN()` correspondiendo a las propiedades en sus ordenes de declaración.
- Función `copy()`

Para asegurar consistencia y comportamiento significativo de el código generado, data class tienen que subrir con los siguiente requerimientos:
- El constructor primario deben tener al menos un parámetro.
- Todos los parámetros del constructor primario deben ser marcados como `val` o `var`
- Las data class no pueden ser clases `abstracts`, `open`, `sealed` o `inner`

# **sealed class**
