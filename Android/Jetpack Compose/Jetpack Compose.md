# **Apuntes de Jetpack Compose**
## **Navigation Component**
### **Gráfico de navegación**
El siguiente es un ejemplo de una aplicación que hice para una app de conversión de unidades.

```kotlin
// 1. Las rutas de nevegación que se utilizaron, esto iba fuera de la clase kotlin

 	 @Serializable object Temperatura
 	 @Serializable object Area
 	 @Serializable object Volumen
 	 @Serializable object Tiempo
 	 @Serializable object Velocidad
 	 @Serializable object Peso
 	 @Serializable object Longitud

// 2. El controlador gestiona la navegación entre los distintos destinos/clases. Esto va dentro de una función @Composable

val navController = *rememberNavController*()

// 3. El NavHost que contiene todas las vistas de la navegación. Esto va dentro de la función @Composable y las funciones dentro de las {...} tiene las funciones @Composable de cada vista.

NavHost(navController = navController, startDestination = Temperatura) {

composable<Temperatura> { TemperaturaCompose() }

composable<Area> { AreaCompose() }

composable<Volumen> { VolumenCompose() }

composable<Tiempo> { TiempoCompose() }

composable<Velocidad> { VelocidadCompose() }

composable<Peso> { PesoCompose() }

composable<Longitud> { LongitudCompose() }

}
```

## **Preview**
Este es un ejemplo de un preview que hice del convetidor de unidades
```Kotlin
//Este es el preview de con un tamaño específico similar a mi célular

@Preview(
      widthDp = 474,
      heightDp = 997,
      name = "Pantalla de mi Xiaomi Redmi note 8",
      uiMode = Configuration.UI_MODE_NIGHT_NO or Configuration.UI_MODE_TYPE_NORMAL,
      wallpaper = Wallpapers.NONE,
      showSystemUi = true)

//Este es el preview basado en el Pixel 9
@Preview(showBackground = true,
      device = "spec:parent=pixel_9", name = "Pixel 9",
      uiMode = Configuration.UI_MODE_NIGHT_NO or Configuration.UI_MODE_TYPE_NORMAL,
      wallpaper = Wallpapers.NONE,
      showSystemUi = true,
)

//Este es el preview de multiples pantallas automáticamente
@PreviewScreenSizes
@Composable 
fun GreetingPreview() {
ConvertirdorUnidadesAndroidTheme {	Fondo()	}
}
```

## **Exposed drop down menu box**
El siguiente es un ejemplo del equivalente a un spinner pero en jetpack compose, este muestra unidades de conversión.

```Kotlin
@OptIn(ExperimentalMaterial3Api::class)
@Composablefun MenuDesplegable(navController: NavHostController) {
      var expandido by remember { mutableStateOf(false) }    val opciones = listOf(
          "Temperatura" to Temperatura,
          "Área" to Area,
          "Volumen" to Volumen,
          "Tiempo" to Tiempo,
          "Velocidad" to Velocidad,
          "Masa" to Peso,
          "Longitud" to Longitud
      )
      var unidadSeleccionada by remember { mutableStateOf(opciones[0]) }    
      Box {        
        ExposedDropdownMenuBox(
              expanded = expandido,
              onExpandedChange = { expandido = it }        
        ) {
            OutlinedTextField(
                value = unidadSeleccionada.first,
                onValueChange = {},
                readOnly = true,
                label = { Text(text = "Unidad") },
                trailingIcon = {
                    ExposedDropdownMenuDefaults.TrailingIcon(expanded = expandido)
                },
                modifier = Modifier.menuAnchor().width(IntrinsicSize.Min) // Se ajusta al contenido mínimo necesario            
            )// El menú que se despliega            
            ExposedDropdownMenu(
                expanded = expandido,
                onDismissRequest = { expandido = false }            
            ) {
            opciones.forEach { unidad ->                    
                DropdownMenuItem(
                    text = { Text(unidad.first) },
                    onClick = {
                        unidadSeleccionada = unidad
                        expandido = false                            
                        navController.navigate(unidad.second) {                                
                            popUpTo(navController.graph.startDestinationId) {                                    
                                saveState = true                                
                            }                                
                            launchSingleTop = true                                
                            restoreState = true                            
                        }                        
                    },
                    contentPadding = ExposedDropdownMenuDefaults.ItemContentPadding                    
                )
            }            
        }        
    }    }}
```

## **Modifier**
### **Row**
#### ***.heigh***
Con esta propiedad puedes configurar la altura de los elementos internos que coloques dentro de la columna, incluso si dichos elementos varían en su altura entre sí. El siguiente ejemplo es de un proyecto de convertidor de unidades de temperatura, una columna tiene etiquetas y la otra campos de texto.

```kotlin
@Composable
fun temperaturasOutput(state: TemperaturaUiState) {
        Row(
            modifier = Modifier.fillMaxWidth().height(IntrinsicSize.Min)
        ){        
            Column(modifier = Modifier.padding(end= 7.dp).fillMaxHeight()) {
                val labelModifier = Modifier.weight(1f).wrapContentHeight(Alignment.CenterVertically).padding(top= 3.5.dp, bottom = 3.5.dp)
                Text(
                    text = stringResource(R.string.temperatura_celsius),
                    modifier = labelModifier
                )
                Text(
                    text = stringResource(R.string.temperatura_farenheit),
                    modifier = labelModifier
                )
                Text(
                    text = stringResource(R.string.temperatura_kelvin),
                    modifier = labelModifier
                )
                Text(
                    text = stringResource(R.string.temperatura_rankine),
                    modifier = labelModifier
                )
            }
            Column(
                modifier = Modifier.wrapContentHeight().fillMaxWidth()
            ) {            
                val fieldModifier = Modifier.fillMaxWidth().padding(top= 3.5.dp, bottom = 3.5.dp)
                TextField(
                    value = state.salidaCelsius.toString(),
                    readOnly = true,
                    onValueChange = { },
                    modifier = fieldModifier
                )
                TextField(
                    value = state.salidaFarenheit.toString(),
                    readOnly = true,
                    onValueChange = { },
                    modifier = fieldModifier
                )
                TextField(
                    value = state.salidaKelvin.toString(),
                    onValueChange = { },
                    readOnly = true,
                    modifier = fieldModifier
                )
                TextField(
                    value = state.salidaRankine.toString(),
                    onValueChange = { },
                    readOnly = true,
                    modifier = fieldModifier
                )
            }    
        }
    }
```

La porpiedad *height* de la fila establece el tamaño que tendrá dicho elemento y se le asignó el valor **IntrinsicSize.Min** para que adopte el tamaño mínimo que debe tener la fila en base al elemento más grande que tenga en su interior (en este caso sería la columna de los campos de texto).

También se estableció el valor **weight(1f)** en el **modifier** de **cada elemento interno de la columna de las etiquetas** para que dichos elementos ocupen el mismo espacio entre si. Solo se configura en los elementos de dicha columna debido a que estos son más pequeños y tiende por si solo a acumularse uno sobre otro en la parte superior y a la izquierda en la pantalla.

Se configuró el valor **.wrapContentHeight(Alignment.CenterVertically)** en los elementos internos de la columna de etiquetas para que estos **ocupen el espacio central vertical y queden alineados a los campos de texto**.

![](Aspose.Words.e512a623-bc8c-4d84-931e-df13ac00b3bf.001.png)
### **Column**
#### ***.verticalScroll***
Con esta propiedad puede habilitar que los elementos internos de una columna puedan ser scrolleados, el siguiente es un ejemplo que se aplicó en una columna que tenían varios Rows que no cabían a primera vista en la pantalla.

```kotlin
Column(
    modifier = Modifier.*verticalScroll*(rememberScrollState()),
    horizontalAlignment = Alignment.CenterHorizontally
) {
RenglonMetro()
 	RenglonKilometro()
 	RenglonCentimetro()
 	RenglonPulgada()
 	RenglonPie()
 	RenglonYarda()
 	RenglonMilla()
 	RenglonMillaNautica()
 	RenglonAnosLuz()
}
```

# **Estados.**
## **Flow**
El siguiente es un ejemplo de como utilizar estados de tipo flow para comunicar la IU de las pantallas compose con variables de estado tipo state Flow en viewModel

```kotlin
@Composable
fun TemperaturaCompose(viewModel: TemperaturaViewModel = viewModel()){
    val iuState by viewModel.uiState.collectAsStateWithLifecycle()  //esta es la variable Flow
    Column(
        modifier = Modifier.padding(7.dp),
        horizontalAlignment = Alignment.CenterHorizontally
    ){
        tituloTemperatura()
        temperaturaInput(
            value = iuState.valorConvertible.toString(),
            onValueChange = { viewModel.onValorChange(it) },
            onUnidadChange = { viewModel.onUnidadChange(it) }        )
            Spacer(modifier = Modifier.padding(8.dp)
        )
        temperaturasOutput(iuState)
    }
}
```

El parámetro viewModel del método TemperaturaCompose ya tiene el objeto del VM y no requiere que se genere por separado.

Los parámetros onValueChange y onUnidadChange hacen referencia a métodos del VM que actualizan el valor de la temperatura que se convierte y la unidad base de conversión; respectivamente.

Al método temperaturaOutput se les pasan los métodos el estado para que pueda actualizar los datos que se mostrarán resultado de las conversiones.

A continuación viene el ejemplo de como se utilizó el estado para comunicar los datos de entrada de un textfield en su estado con el estado tipo Flow que recibió en el parámetro.

```kotlin
@Composable
fun temperaturaInput(
      value: String,
      onValueChange: (String) -> Unit,
      onUnidadChange: (UnidadTemperatura) -> Unit
){
    // Estado local para manejar el texto y permitir borrar puntos decimales
    var entradaTemperatura by remember {
        mutableStateOf(if(value.equals(0.0)) "" else value.toString())
    }
    Row(
        modifier = Modifier.fillMaxWidth(),
        verticalAlignment = Alignment.CenterVertically,
        horizontalArrangement = Arrangement.Center
    ){
        TextField(
            value = entradaTemperatura,
            onValueChange = { nuevoTexto ->
                // FILTRO: Solo permite números, un solo punto decimal y un signo menos al inicio
                if (nuevoTexto.*isEmpty*() || nuevoTexto.*matches*(Regex("""^-?\d\*\.?\d\*$"""))) {
                    entradaTemperatura = nuevoTexto
                    // Solo enviamos al ViewModel si es un número convertible                    
                    val numero = nuevoTexto.toDoubleOrNull()
                    if (numero != null) {
                        onValueChange(numero.toString())
                    } else if (nuevoTexto.*isEmpty*() || nuevoTexto == "-") {
                        onValueChange((0.0).toString()) // Valor por defecto si está vacío o solo tiene el menos
                    }
                }
            },
            placeholder = { Text(text = stringResource(R.string.placeholder_temperatura)) },
            keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Decimal)
        )
        menuTemperatura(onUnidadChange)
    }
}

@Composable
private fun menuTemperatura(onUnidadChange: (UnidadTemperatura) -> Unit){
    var expanded by remember { mutableStateOf(false) }    
    Box() {        
        IconButton(onClick = { expanded = !expanded }) {
            Icon(
                imageVector = Icons.Default.MoreVert,
                contentDescription = stringResource(R.string.menu_temperatura)
            )
        }
        DropdownMenu(
            expanded = expanded,
            onDismissRequest = { expanded = false }
        ) {
            DropdownMenuItem(
                text = { Text(text = stringResource(R.string.temperatura_celsius)) },
                onClick = {
                    onUnidadChange(UnidadTemperatura.CELSIUS)
                    expanded = false                
                }
            )
            DropdownMenuItem(
                text = { Text(text = stringResource(R.string.temperatura_farenheit)) },
                onClick = {
                    onUnidadChange(UnidadTemperatura.FAHRENHEIT)
                    expanded = false
                }
            )
            DropdownMenuItem(
                text = { Text(text = stringResource(R.string.temperatura_kelvin)) },
                onClick = {                     
                    onUnidadChange(UnidadTemperatura.KELVIN)
                    expanded = false
                }
            )
            DropdownMenuItem(
                text = { 
                    Text(text = stringResource(R.string.temperatura_rankine))
                },
                onClick = {                     
                    onUnidadChange(UnidadTemperatura.RANKINE)
                    expanded = false
                }
            )
        }    
    }
}
```


A continuación viene un ejemplo de los métodos que estaban relacionados con los resultados de las conversiones de temperatura.
```kotlin
@Composable
    fun temperaturasOutput(state: TemperaturaUiState) {
    renglonCelsius(state.salidaCelsius.toString())
    renglonFahrenheit(state.salidaFarenheit.toString())
    renglonKelvin(state.salidaKelvin.toString())
    renglonRankine(state.salidaRankine.toString())
}

@Composableprivate fun renglonCelsius(valor: String) {
    Row(
        modifier = Modifier.padding(7.dp),
        verticalAlignment = Alignment.CenterVertically    ) {        
            Text(
                text = stringResource(R.string.temperatura_celsius),
                modifier = Modifier.weight(2F)
            )
        TextField(
            value = valor,
            readOnly = true,
            onValueChange = { },
            modifier = Modifier.weight(8F)
        )
    }
}

@Composable
private fun renglonFahrenheit(valor: String) {
    Row(
        modifier = Modifier.padding(7.dp),
        verticalAlignment = Alignment.CenterVertically
    ) {
        Text(
            text = stringResource(R.string.temperatura_farenheit),
            modifier = Modifier.weight(2F)
        )
        TextField(
            value = valor,
            readOnly = true,
            onValueChange = { },
            modifier = Modifier.weight(8F)
        )
    }
}

@Composable
private fun renglonKelvin(valor: String) {
    Row(
        modifier = Modifier.padding(7.dp),
        verticalAlignment = Alignment.CenterVertically
    ) { 
        Text(
            text = stringResource(R.string.temperatura_kelvin),
            modifier = Modifier.weight(2F)
        )
        TextField(
            value = valor,
            onValueChange = { },
            readOnly = true,
            modifier = Modifier.weight(8F)
        )
    }
}

@Composable
private fun renglonRankine(valor: String) {
    Row(
        modifier = Modifier.padding(7.dp),
        verticalAlignment = Alignment.CenterVertically
    ) {
        Text(
            text = stringResource(R.string.temperatura_rankine),
            modifier = Modifier.weight(2F)
        )
        TextField(
            value = valor,
            onValueChange = { },
            readOnly = true,
            modifier = Modifier.weight(8F)
        )
    }
}
```

En los parámetros de cada renglón viene la variable estado del viewModel.
## **StateFlow**
El siguiente es un ejemplo de como mantener el estado de datos que se quieran comunicar a la IU, pero estos estados se mantienen en el ViewModel. El siguiente es un ejemplo de ViewModel que contiene los StateFlow de valor base, dato de conversión y los datos a convertir que se hizo para una pantalla del convertidor de temperatura.

```kotlin
class TemperaturaViewModel : ViewModel() {
    private val _iuValorState = MutableStateFlow(TemperaturaUiState())
    val uiState: StateFlow<TemperaturaUiState> = _iuValorState.asStateFlow()

    private val transformador = Temperatura()

    fun onValorChange(nuevoValor: String) {
        _iuValorState.update { it.copy(valorConvertible = nuevoValor.toDoubleOrNull()) }
        convertirTemperatura()
    }

    fun onUnidadChange(nuevaUnidad: UnidadTemperatura) {
        _iuValorState.update { it.copy(unidadDeConversion = nuevaUnidad) }        
        convertirTemperatura()
    }

    private fun convertirTemperatura() {
        val valor = _iuValorState.value.valorConvertible ?: 0.0        
        val unidad = _iuValorState.value.unidadDeConversion // Configuramos el transformador según la unidad seleccionada        
        when (unidad) {
            UnidadTemperatura.CELSIUS -> {
                transformador.setCelsius(valor)
                transformador.conversionCelsius()
                _iuValorState.update { it.copy(
                    salidaCelsius = valor,
                    salidaKelvin = transformador.ck(),
                    salidaFarenheit = transformador.cf(),
                    salidaRankine = transformador.cr()
                )}
            }
            UnidadTemperatura.FAHRENHEIT -> {
                transformador.setFarenheit(valor)
                transformador.conversionFarenheit()
                _iuValorState.update { it.copy(
                    salidaCelsius = transformador.fc(),
                    salidaKelvin = transformador.fk(),
                    salidaFarenheit = valor,
                    salidaRankine = transformador.fr()
                )}
            }
            UnidadTemperatura.KELVIN -> {
                transformador.setKelvin(valor)
                transformador.conversionKelvin()
                _iuValorState.update { it.copy(
                    salidaCelsius = transformador.kc(),
                    salidaKelvin = valor,
                    salidaFarenheit = transformador.kf(),
                    salidaRankine = transformador.kr()
                )}
            }
            UnidadTemperatura.RANKINE -> {
                transformador.setRankine(valor)
                transformador.conversionRankine()
                _iuValorState.update { it.copy(
                    salidaCelsius = transformador.rc(),
                    salidaKelvin = transformador.rk(),
                    salidaFarenheit = transformador.rf(),
                    salidaRankine = valor
                )}
            }
            else -> {}
        }
    }
}
```

# **Tipos de Clase**
## **Data Class**
El siguiente es un ejemplo de data class que hice para un convertidor de unidades de temperatura y almacena los datos del valorConvertible, Unidad de conversión, salida a Celsius, salida a Kelvin, salida a Farenheit, salida a Rankine.

```kotlin
data class TemperaturaUiState(
    val valorConvertible: Double ?= 0.0,
    val unidadDeConversion: UnidadTemperatura ?= UnidadTemperatura.CELSIUS,
    val salidaCelsius: Double ?= 0.0,
    val salidaKelvin: Double ?= 0.0,
    val salidaFarenheit: Double ?= 0.0,
    val salidaRankine: Double ?= 0.0
)
```

## **Enum Class**
El siguiente es un ejemplo de un listado que hice para unidades de conversión de temperatura.

```kotlin
enum class UnidadTemperatura {
    CELSIUS,
    KELVIN,
    FAHRENHEIT,
    RANKINE
}
```

# TexField
## **.placeholder**
Con este parámetro se puede agregar el texto que viene por defecto en la caja de texto cuando está vacío el campo.
## **.keyboardOptions**
Con este parámetro se puede especificar que teclado se utilizará para que el el usuario ingrese texto al TextField. Adjunto un ejemplo de caja de texto que solo admite datos decimales.

```kotlin
TextField(
    value = entradaTemperatura,
    onValueChange = { nuevoTexto -> 
        // FILTRO: Solo permite números, un solo punto decimal y un signo menos al inicio
        if (nuevoTexto.*isEmpty*() || nuevoTexto.*matches*(Regex("""^-?\d\*\.?\d\*$"""))) {
            entradaTemperatura = nuevoTexto

            // Solo enviamos al ViewModel si es un número convertible
            val numero = nuevoTexto.toDoubleOrNull()
            if (numero != null) {
                onValueChange(numero.toString())
            } else if (nuevoTexto.*isEmpty*() || nuevoTexto == "-") {
                onValueChange((0.0).toString()) // Valor por defecto si está vacío o solo tiene el menos
            }
        }
    },
    placeholder = { 
        Text(text = stringResource(R.string.placeholder_temperatura))
    },
    keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Decimal)
)
```

# **Menús**
## **DropDownMenú**
El siguiente es un ejemplo de un dropdown que se depliega al hacer click en un iconbutton, este se utilizaba justo a lado de un campo textfiel de conversión de unidades de temperatura.

```kotlin
@Composable
private fun menuTemperatura(onUnidadChange: (UnidadTemperatura) -> Unit){
    var expanded by remember { 
        mutableStateOf(false)
    }
    Box() {
            IconButton(onClick = { expanded = !expanded }) {
                Icon(
                    imageVector = Icons.Default.MoreVert,
                    contentDescription = stringResource(R.string.menu_temperatura)
                )
            }
            DropdownMenu(
                expanded = expanded,
                onDismissRequest = { expanded = false }        
            ) {
                DropdownMenuItem(
                    text = { 
                        Text(text = stringResource(R.string.temperatura_celsius)) 
                    },
                    onClick = {                     
                        onUnidadChange(UnidadTemperatura.CELSIUS)
                        expanded = false
                    }
                )
                DropdownMenuItem(
                    text = { Text(text = stringResource(R.string.temperatura_farenheit)) },
                    onClick = {
                        onUnidadChange(UnidadTemperatura.FAHRENHEIT)
                        expanded = false                
                    }
                )
                DropdownMenuItem(
                    text = { Text(text = stringResource(R.string.temperatura_kelvin)) },
                    onClick = {
                        onUnidadChange(UnidadTemperatura.KELVIN)
                        expanded = false
                    }
                )
                DropdownMenuItem(
                    text = { Text(text = stringResource(R.string.temperatura_rankine)) },
                    onClick = {
                        onUnidadChange(UnidadTemperatura.RANKINE)
                        expanded = false
                    }            
                )
            }    
        }
    }
```

![](Aspose.Words.e512a623-bc8c-4d84-931e-df13ac00b3bf.002.png)
# ViewModel
El siguiente es un ejemplo de una clase ViewModel que es utilizado por la IU de una aplicación de conversión de unidades.

```kotlin
class TemperaturaViewModel : ViewModel() {
    private val _iuValorState = MutableStateFlow(TemperaturaUiState())
    val uiState: StateFlow<TemperaturaUiState> = _iuValorState.asStateFlow()

    private val transformador = Temperatura()

    fun onValorChange(nuevoValor: String) {
        _iuValorState.update { 
            it.copy(valorConvertible = nuevoValor.toDoubleOrNull()) 
        } 
        convertirTemperatura()
    }

    fun onUnidadChange(nuevaUnidad: UnidadTemperatura) {
        _iuValorState.update { it.copy(unidadDeConversion = nuevaUnidad) }
        convertirTemperatura()
    }

    private fun convertirTemperatura() {
        val valor = _iuValorState.value.valorConvertible ?: 0.0        
        val unidad = _iuValorState.value.unidadDeConversion // Configuramos el transformador según la unidad seleccionada        
        when (unidad) {
            UnidadTemperatura.CELSIUS -> {
                transformador.setCelsius(valor)
                transformador.conversionCelsius()
                _iuValorState.update { it.copy(
                    salidaCelsius = valor,
                    salidaKelvin = transformador.ck(),
                    salidaFarenheit = transformador.cf(),
                    salidaRankine = transformador.cr()
                )}            }
            UnidadTemperatura.FAHRENHEIT -> {
                transformador.setFarenheit(valor)
                transformador.conversionFarenheit()
                _iuValorState.update { it.copy(
                    salidaCelsius = transformador.fc(),
                    salidaKelvin = transformador.fk(),
                    salidaFarenheit = valor,
                    salidaRankine = transformador.fr()
                )}            
            }
            UnidadTemperatura.KELVIN -> {
                transformador.setKelvin(valor)
                transformador.conversionKelvin()
                _iuValorState.update { it.copy(
                    salidaCelsius = transformador.kc(),
                    salidaKelvin = valor,
                    salidaFarenheit = transformador.kf(),
                    salidaRankine = transformador.kr()
                )}
            }
            UnidadTemperatura.RANKINE -> {
                transformador.setRankine(valor)
                transformador.conversionRankine()
                _iuValorState.update { it.copy(
                    salidaCelsius = transformador.rc(),
                    salidaKelvin = transformador.rk(),
                    salidaFarenheit = transformador.rf(),
                    salidaRankine = valor
                )}
            }
            else -> {}
        }
    }
}
```

Se puede ver que el tipo de clase es ViewModel para que pueda ser utilizado por el cliclo de vida de las aplicaciones android.

La constante _iuValorState es una clase de tipo StateFlow y recibe un parámetro del tipo TemperaturaUiState que almacena cada estado que pueda llegar a cambiar en la IU de la aplicación que fue hecha en JetpackCompose. En este caso los estados almacenan el valor que se quiere convertir, la unidad de dicho valor y los resultados que tendrá de conversión cada Unidad.

La constante iuState es igual a la constante _iuValorState y se ve reflejada cualquier cambio que que tenga.

La constante Temperatura esta hecha en base a la clase que tiene el mismo nombre, ya que esta tiene la lógica detrás de la conversión de unidades de temperatura.

El método onValorChange recibe en el parámetro el valor que introdujo el usuario en el textField de la IU

El método onUnidadChange recibe en el parámetro el valor que seleccionó el usuario del DropDownMenu.

El método convertirTemperatura tiene dos constante; Valor y Unidad. Cada una está apuntando a sus respectivas variables que contiene el estado _iuValorState, de esta forma siempre tiene la información acual del estado. Dentro del método también tiene una condicional “when” que ejecuta la conversión de unidades dependiendo de lo que haya seleccionado e introducido de valores el usuario en la IU.

A continuación se muestra el código de la IU.

```kotlin
@Composable
    fun TemperaturaCompose(viewModel: TemperaturaViewModel = viewModel()){
    val iuState by viewModel.uiState.collectAsStateWithLifecycle()
    Column(modifier = Modifier.padding(7.dp),
        horizontalAlignment = Alignment.CenterHorizontally) {
        tituloTemperatura()
        temperaturaInput(
            value = iuState.valorConvertible.toString(),
            onValueChange = { viewModel.onValorChange(it) },
            onUnidadChange = { viewModel.onUnidadChange(it) }        
        )
        Spacer(modifier = Modifier.padding(8.dp))
        temperaturasOutput(iuState)
        }
    }

@Composable
fun tituloTemperatura() {
    Row(
        modifier = Modifier.fillMaxWidth(),
        horizontalArrangement = Arrangement.Center    
    ) {
        Text(
            text = stringResource(R.string.*titulo_temperatura*),
            modifier = Modifier.padding(all = 15.dp),
            textAlign = TextAlign.Center
        )
    }
}

@Composablefun temperaturaInput(
    value: String,
    onValueChange: (String) -> Unit,
    onUnidadChange: (UnidadTemperatura) -> Unit
) {

    // Estado local para manejar el texto y permitir borrar/puntos decimales    
    var entradaTemperatura by remember { mutableStateOf(if(value.equals(0.0)) "" else value.toString()) }    
    Row(
        modifier = Modifier.fillMaxWidth(),
        verticalAlignment = Alignment.CenterVertically,
        horizontalArrangement = Arrangement.Center    
    ) {
            TextField(
                value = entradaTemperatura,
                onValueChange = { nuevoTexto -> 
                // FILTRO: Solo permite números, un solo punto decimal y un signo menos al inicio
                if (nuevoTexto.*isEmpty*() || nuevoTexto.*matches*(Regex("""^-?\d\*\.?\d\*$"""))) {
                    entradaTemperatura = nuevoTexto
                    // Solo enviamos al ViewModel si es un número convertible                    
                    val numero = nuevoTexto.toDoubleOrNull()
                    if (numero != null) {
                        onValueChange(numero.toString())
                    } else if (nuevoTexto.*isEmpty*() || nuevoTexto == "-") {
                        onValueChange((0.0).toString()) // Valor por defecto si está vacío o solo tiene el menos                    
                    }
                }
            },
            placeholder = { Text(text = stringResource(R.string.placeholder_temperatura)) },
            keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Decimal)
        )
        menuTemperatura(onUnidadChange)
    }
}

@Composable
fun temperaturasOutput(state: TemperaturaUiState) {
    renglonCelsius(state.salidaCelsius.toString())
    renglonFahrenheit(state.salidaFarenheit.toString())
    renglonKelvin(state.salidaKelvin.toString())
    renglonRankine(state.salidaRankine.toString())
}

@Composable
private fun renglonCelsius(valor: String) {
    Row(
        modifier = Modifier.padding(7.dp),
        verticalAlignment = Alignment.CenterVertically
    ){
        Text(
            text = stringResource(R.string.temperatura_celsius),
            modifier = Modifier.weight(2F)
        )
        TextField(
            value = valor,
            readOnly = true,
            onValueChange = { },
            modifier = Modifier.weight(8F)
        )
    }
}

@Composable
private fun renglonFahrenheit(valor: String) {
    Row(
        modifier = Modifier.padding(7.dp),
        verticalAlignment = Alignment.CenterVertically
    ) {
        Text(
            text = stringResource(R.string.temperatura_farenheit),
            modifier = Modifier.weight(2F)
        )
        TextField(
            value = valor,
            readOnly = true,
            onValueChange = { },
            modifier = Modifier.weight(8F)
        )
    }
}

@Composable
private fun renglonKelvin(valor: String) {
    Row(
        modifier = Modifier.padding(7.dp),
        verticalAlignment = Alignment.CenterVertically    
    ) {
        Text(
            text = stringResource(R.string.temperatura_kelvin),
            modifier = Modifier.weight(2F)
        )
        TextField(
            value = valor,
            onValueChange = { },
            readOnly = true,
            modifier = Modifier.weight(8F)
        )
    }
}

@Composable
private fun renglonRankine(valor: String) {
    Row(
        modifier = Modifier.padding(7.dp),
        verticalAlignment = Alignment.CenterVertically
    ) {
        Text(
            text = stringResource(R.string.temperatura_rankine),
            modifier = Modifier.weight(2F)
        )
        TextField(
            value = valor,
            onValueChange = { },
            readOnly = true,
            modifier = Modifier.weight(8F)
        )
    }
}

@Composable
private fun menuTemperatura(onUnidadChange: (UnidadTemperatura) -> Unit){
    var expanded by remember { mutableStateOf(false) }    
    Box() {        
        IconButton(onClick = { expanded = !expanded }) {            
            Icon(
                imageVector = Icons.Default.MoreVert,
                contentDescription = stringResource(R.string.menu_temperatura)
            )
        }        
        DropdownMenu(
            expanded = expanded,
            onDismissRequest = { expanded = false }
        ) {            
            DropdownMenuItem(
                text = { Text(text = stringResource(R.string.temperatura_celsius)) },
                onClick = {
                    onUnidadChange(UnidadTemperatura.CELSIUS)
                    expanded = false
                })
            DropdownMenuItem(
                text = { Text(text = stringResource(R.string.temperatura_farenheit)) },
                onClick = {                     
                    onUnidadChange(UnidadTemperatura.FAHRENHEIT)
                    expanded = false                
                }            
            )
            DropdownMenuItem(
                text = { Text(text = stringResource(R.string.temperatura_kelvin)) },
                onClick = {                     
                    onUnidadChange(UnidadTemperatura.KELVIN)
                    expanded = false                
                }            
            )
            DropdownMenuItem(
                text = { Text(text = stringResource(R.string.temperatura_rankine)) },
                onClick = {                     
                    onUnidadChange(UnidadTemperatura.RANKINE)
                    expanded = false                
                }            
            )
        }    
    }
}
```

El método TemperaturaCompose tiene en el parámetro el objeto viewModel el cuál está relacionado con la clase ViewModel que coordina la vista y la lógica de la aplicación. Dentro de dicho método se tiene el objeto/estado iuState el cuál ya está vinculado al objeto StateFlow del mismo nombre en el viewModel (dicho objeto es el que almacena los datos de valor a convertir, unidad base, y las conversiones). En dicho método se pasa el estado a los métodos temperaturaInput y temperaturaOutput ya que estos métodos necesitarán hacer la conversión de unidades u obtener los datos de dicha conversión.

El método temperaturaInput recibe en sus parámetros el valor que se desea convertir, así como los métodos del viewModel relacionados a la ejecución de la conversión de unidades y la unidad base del valor que se desea convertir. También tiene un objeto entradaTemperatura que almacena el dato del textfield con la cantidad a convertir.

# **AdMob**
## **Agregar AdMob a los build.Gradle**
### Agregar dependencia en build.gradle project
```gradle
plugins {    
.......
alias(libs.plugins.google.*gms*.google.services) apply false
.......
}
```

### Agregar dependencias en build.gradle app y modificar versión de kotlin usada
```gradle
plugins {
......
    alias(libs.plugins.google.gms.google.services)
.......
}


//El kotlinOptions fue eliminado para usar una versión de kotlin correcta

kotlinOptions {
    jvmTarget = "11"
}

kotlin {
    compilerOptions {
        jvmTarget.set(org.jetbrains.kotlin.gradle.dsl.JvmTarget.JVM_11)
    }
}

dependencies {
.......

    implementation(libs.play.services.ads)
    implementation(platform("com.google.firebase:firebase-bom:34.16.0"))
    implementation("com.google.firebase:firebase-analytics")
.......
}
```

## Agregar el archivo google-services.json
El siguiente archivo es solo un ejemplo, para el proyecto donde se quiera implementar firebase se tiene que obtener el archivo desde el panel de firebase del proyecto.

```json
{
    "project_info": {
        "project_number": "327133111462",
        "project_id": "convertirdorunidades-ea748c90",
        "storage_bucket": "convertirdorunidades-ea748c90.firebasestorage.app"  
    },
    "client": [{
        "client_info": {
            "mobilesdk_app_id": "1:327133111462:android:dfbb783c4765a1d2548067",
            "android_client_info": {
                "package_name": "com.jfsolutions.convertirdorunidadesandroid"        
            }
        },
        "oauth_client": [],
        "api_key": [
            {
                "current_key": "AIzaSyA1hgJ08gAs7FQ1XQ2MnjPye8Iq63niqcI"
            }
        ],
        "services": {
            "appinvite_service": {
                "other_platform_oauth_client": []
            }
        }
    }],
    "configuration_version": "1"
}
```

## **Administración del identificador del Ad Unit ID**
Se debe almacenar en la aplicación el identificador de avisos para la aplicación, en este ejemplo se gestionan por medio de variables en el archivos strings.xml y se tiene en el archivo tanto el identificador productivo como uno para pruebas. **SOLO SE PUEDE USAR LA CLAVE admob_bloque_anuncios_id CUANDO SEA PUBLICADA EN LA PLAY STORE O DE LO CONTRARIO NOS PUEDE SUSPENDER LA APLICACIÓN ADMOB DE GOOGLE.**

```xml
<resources>
.....
<string name="admob_app_id">ca-app-pub-2546662781964002~1993811313</string> 
<string name="admob_bloque_anuncios_id">ca-app-pub-2546662781964002/7657321674</string>
<string name="admob_bloque_anuncios_id_test">ca-app-pub-3940256099942544/6300978111</string>
.......
</resources>
```

Se tienen que considerar dos claves “admob_app_id” y “admob_bloque_anuncios_id”, estas son claves distintas y se tienen que consultar de la consola de AdMob.
## **Agregar admob en el AndroidManifest.xml**
```xml
<application>
......
<!-- Sample AdMob app ID: ca-app-pub-3940256099942544~3347511713 -->
<meta-data    
    android:name="com.google.android.gms.ads.APPLICATION_ID"
    android:value="@string/admob_app_id"
/>
.......
</application>
```

## **Inicializar Ads**
```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        CoroutineScope(Dispatchers.IO).launch {            
            MobileAds.initialize(this@MainActivity)
        }

......

    }

}
```
## **Invocación y uso de la Interfaz gráfica del AdMob**
```kotlin
@Composable
fun Fondo(modifier: Modifier = Modifier) {
    // 3. El navController se recuerda dentro de la composición, no en la Activity    
    val navController = rememberNavController()
    val configuration = LocalConfiguration.current    
    val isLandscape = configuration.orientation == Configuration.ORIENTATION_LANDSCAPE    
    Column(modifier = modifier) {        
        if(isLandscape){
            Row() {                
                Column(modifier = Modifier.weight(1f).fillMaxHeight()) {                    
                    AdMobBanner()
                }
                Column(modifier = Modifier.weight(8f).fillMaxHeight()) {                    
                    Encabezado(navController)
                    Navegacion(navController = navController)
                }
                Column(modifier = Modifier.weight(1f).fillMaxHeight()) {                    
                    AdMobBanner()
                }
            }
        } else {
            Column(modifier = Modifier.weight(1f).fillMaxWidth()) {                    
                Encabezado(navController)
                    Navegacion(navController = navController)
            }
            AdMobBanner()
          }
    }
}
```

## **Diseño de interfaz gráfica del AdMob**
```kotlin
@Composablefun AdMobBanner(){
    val adUnitId = stringResource(R.string.admob_bloque_anuncios_id)
    val width = LocalConfiguration.current.screenWidthDp        
    AndroidView(
        modifier = Modifier.fillMaxWidth(),
        factory = { context ->            
        AdView(context).apply {                
            setAdSize(AdSize.getCurrentOrientationAnchoredAdaptiveBannerAdSize(context, width))
                setAdUnitId(adUnitId)
                loadAd(AdRequest.Builder().build())
            }        
        }    
    )
}
```