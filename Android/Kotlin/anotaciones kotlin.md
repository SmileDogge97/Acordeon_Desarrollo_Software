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


# **LiveData**
Crear una variable viewmodel dentro de las activitys o fragments:
```Kotlin
//esta variable es la del viewModel
lateinit var viewModel: LiveDataViewModel

//aquí designamos de que activity es y que viewmodel usa
   viewModel = ViewModelProviders.of(this).get(LiveDataViewModel::class.*java*)
```

El observer dentro de las activitys o fragments:

```Kotlin
val listObserver = *Observer*<List<User>>{
      //esto va agregando la información a la etiqueta
      userList ->
      var texto = ""
      for (user in userList){
          texto += user.nombre + " " + user.edad + "n"
      }
      tvLiveData.*text* = texto
}
```

Suscribir el viewmodel al observer dentro de las activitys o fragments:
```Kotlin
//esto suscribe el observer, se pone:
// el viewmodel, el nombre de la función que lee, la activity en la que está y el nombre del observer
viewModel.getUserList().observe(this@LiveDataActivity, listObserver)
```

Los objetos observables dentro del ViewModel:
```Kotlin
//este es un objeto del tipo MutableLiveData, es un objeto observable
var userListLiveData: MutableLiveData<List<User>> = MutableLiveData()

//esta es una lista mutable pero sin ser livedata, es  solo una lista de usuarios
var userList: MutableList<User> = ArrayList()

//esta función solo es de lectura
fun getUserList(): LiveData<List<User>>{
      return userListLiveData
}

//con esto le doy un valor a la lista del livedata usando una lista normal
userListLiveData.*value* = userList
```

# **Databinding**
Habilitar el databinding desde la clase build.gradle :app dentro de las llaves de Android:
```Kotlin
//esto habilita el dataBinding
dataBinding {
      enabled = true
}
```

El DataBinding dentro del xml de la interfaz gráfica:
```Xml
<?xml version="1.0" encoding="utf-8"?>
<layout xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:tools="http://schemas.android.com/tools"
          xmlns:app="http://schemas.android.com/apk/res-auto">
      <!-- esto convierte el layout a databinding-->
      <data>
          <!-- //esta es la variable del databinding y su nombre es el mismo que el objeto en la activity,
          el type tiene la misma ubicación que la importación del user de la actividad, ósea que usa la clase User de la carpeta utils para crear el objeto databinding en el xml-->
          <variable
                  name="user"
                  type="com.androiddesdecero.viewmodellivedatakotlin.utils.User"/>
      </data>

      <LinearLayout
              android:layout_width="match_parent"
              android:layout_height="match_parent"
              tools:context=".ui.DataBindingActivity">
          <!--en los textos de los textviews manda a llamar las variables del objeto user-->
          <TextView
                  android:text="@{user.nombre}"
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"/>
          <TextView
                  android:text="@{user.edad}"
                  android:layout_width="wrap_content"
                  android:layout_height="wrap_content"/>

      </LinearLayout>
</layout>
```

Variable para ingresar datos dentro del xml de la interfaz, va dentro de la activity o fragment y tienes que remover el setContetView del onCreate:
```Kotlin
super.onCreate(savedInstanceState)
//setContentView(R.layout.activity_data_binding)

//esta variable es para setContent pero usando dataBinding,
//android estudio creo este tipo de variabl así: Activity*nombre de la activity*Binding
//y para **la** parte del setContentView se compone así: this@*nombre completo del archivo activity*, *ubicación del layout de la activity*
val binding: ActivityDataBindingBinding = DataBindingUtil.setContentView(this@DataBindingActivity,R.layout.*activity_data_binding*)


//objeto de tipo User
lateinit var user: User
user = User("Alberto", "30")

//esto sirve por ejemplo cuando haces solicitudes constantes a un webservice y las respuestas
//están constantemente cambiando, con esto se actualizan y muestran los nuevos cambios
binding.*user* = user

Esta es la clase User de la cual se estuvieron haciendo los objetos DataBinding:

class User(
      var nombre: String = "",
      var edad: String = "")
```

## **DataBinding LiveData BindingAdapter**
Las declaraciones del lado de la activity:
```Kotlin
//esta es la variable del viewModel
lateinit var viewModel: DBLDViewModel

override fun onCreate(savedInstanceState: Bundle?) {
      super.onCreate(savedInstanceState)

      //la variable del databinding con la que se ingresa el contenido a la vista
      val binding: ActivityDbldBinding = DataBindingUtil.setContentView(this@DBLDActivity, R.layout.*activity_dbld*)

      //esto declara el propietario del ciclo de vida
      binding.setLifecycleOwner(this)

      //con esto se instancia el viewModel
      viewModel =ViewModelProviders.of(this).get(DBLDViewModel::class.*java*)

      //esto vienen en el segundo video
      //asigna el viewmodel del xml a la variable viewModel de arriba
      binding.*viewModel* = viewModel

      val user = User("Alberto", "30")
      viewModel.setUser(user)

}
```

El databinding del lado del xml:
```Xml
<?xml version="1.0" encoding="utf-8"?>
<layout xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:tools="http://schemas.android.com/tools"
          xmlns:app="http://schemas.android.com/apk/res-auto">
      <!--esto convierte al layout en databiding-->
      <data>
      <!--esto le da un nombre a la variable y el type especifica con que viewModel está relacionado-->
          <variable
`             `name="viewModel"
`             `type="com.androiddesdecero.viewmodellivedatakotlin.viewmodel.DBLDViewModel"/>
      </data>

.

.

.

.


<!--esto enlaza el texto con la variable del objeto user. La visibilidad y tamaño lo tiene asociado
al bindingAdapter. el visibility es exactamente el mismo que el del bindingadapter-->
<TextView
          android:text="@{viewModel.user.nombre}"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          app:visibility="@{viewModel.visible}"
          app:size="@{viewModel.size}"/>

<!--esto enlaza el texto con la variable del objeto user. La visibilidad y tamaño lo tiene asociado
al bindingAdapter. el visibility es exactamente el mismo que el del bindingadapter-->
<TextView
          android:text="@{viewModel.user.edad}"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          app:visibility="@{viewModel.visible}"
          app:size="@{viewModel.size}"/>


<!--esto enlaza el texto con la función updateUser del viewmodel al botón-->
<Button
          android:onClick="@{()->viewModel.updateUser()}"
          android:text="Actualizar User"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"/>

<!--esto enlaza el texto con la función changeVisibility del viewmodel al botón-->
<Button
          android:text="Visibilidad"
          android:onClick="@{()->viewModel.changeVisibility()}"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"/>
```

El viewModel: 
```Kotlin
//esta clase desciente de ViewModel
class DBLDViewModel: ViewModel() {

      //una variable livedata que cambia
      var user: MutableLiveData<User> = MutableLiveData()
      //esto maneja la visibilidad de las textview de la interfaz
      var visible: MutableLiveData<Boolean> = MutableLiveData()
      //esta variable es para controlar el tamaño de las textView
      var size: MutableLiveData<Float> = MutableLiveData(14f)


      //esto le ingresa los valores al observador
      fun setUser(user: User){
          this.user.*value* = user
      }
      //esto actualiza el valor del objeto
      fun updateUser(){
          val user = User("Laura", "23")
          this.user.*value* = user
      }

      fun setVisible(visible: Boolean){
          this.visible.*value* = visible
      }

      fun changeVisibility(){
          if(visible.*value* == true){
              visible.*value* = false
          }else{
              visible.*value* = true
          }
          size.*value* = size.*value*!!.toFloat() + 5f
      }
}
```

La Clase User con la cual se hicieron los objetos del databinding:
```Kotlin
class User(
      var nombre: String = "",
      var edad: String = "")

el objeto BindingAdapter para controlar la visibilidad de los textview y el tamaño de la fuente:

object BindingAdapter {

      //esta etiqueta se usa por que los bindingAdapter se basan en métodos estáticos
      @JvmStatic
      //esto controla la visibilidad de la interfaz y está asociado a los textview de la interfaz
      @BindingAdapter("visible")
      fun setVisibility(view: View, visibility: Boolean){
          if(visibility == true){
              view.*visibility* = View.*VISIBLE*
          }else{
              view.*visibility* = View.*GONE*
          }
      }

      //esta etiqueta se usa por que los bindingAdapter se basan en métodos estáticos
      @JvmStatic
      //esto controla la visibilidad de la interfaz y está asociado a los textview de la interfaz
      @BindingAdapter("visibility", "size")
      fun setSizeAndVisibility(view: TextView, visibility: Boolean, size: Float){
          if(visibility == true){
              view.*visibility* = View.*VISIBLE*
          }else{
              view.*visibility* = View.*GONE*
          }
          view.*textSize* = size
      }
}
```

Habilitar el buildAdapter para el proyecto desde el archivo build.graddle(:app):
```Kotlin
//esto lo agregué para el buildingAdapter va al principio del build.graddle
apply plugin: 'kotlin-kapt'
```
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
