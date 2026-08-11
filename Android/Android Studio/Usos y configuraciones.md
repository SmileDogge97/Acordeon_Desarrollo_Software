# **Android Studio**
## Variantes de compilación.
Cada variante de compilación representa una versión diferente  de tu app que puedes compilar. Por ejemplo, es posible que desees  compilar una versión de tu app que sea gratuita con contenido limitado y  una versión pagada que incluya más contenido. También puedes compilar  diferentes versiones de tu app para diferentes dispositivos, según el  nivel de API y otras variantes de dispositivos. 

Las variantes de compilación surgen del uso de un conjunto específico  de reglas a través de Gradle para combinar los parámetros de  configuración, código y recursos configurados en tus tipos de  compilación y variantes de productos. Aunque no configuras variantes de  compilación directamente, sí configuras los tipos de compilación y las  variantes de productos que las forman.
### **Cómo configurar tipos de compilaciones**
Puedes crear y configurar tipos de compilaciones dentro del bloque android del archivo build.gradle.kts a nivel del módulo. Cuando creas un módulo nuevo, Android Studio genera automáticamente los tipos de compilación de depuración y lanzamiento. Si bien el tipo de compilación de depuración no aparece en el archivo de configuración de compilación, Android Studio lo configura con debuggable true. Esta configuración te permite depurar la app en dispositivos Android seguros y configura la firma de la app con un almacén de claves de depuración genérico.

Puedes agregar el tipo de compilación de depuración a tu configuración si deseas agregar o cambiar determinadas opciones de configuración. En el siguiente ejemplo, se especifica un applicationIdSuffix para el tipo de compilación de depuración y se configura un tipo de compilación "staging" (etapa de pruebas) que se inicializa con la configuración del tipo de compilación de depuración: 

```gradle
android {
      defaultConfig {
          manifestPlaceholders = [hostName:"www.example.com"]
...
      }
      buildTypes {
          release {
              minifyEnabled true
              proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
          }

          debug {
              applicationIdSuffix ".debug"
              debuggable true
          }
          /**

           * The `initWith` property lets you copy configurations from other build types,

           * then configure only the settings you want to change. This one copies the debug build

           * type, and then changes the manifest placeholder and application ID.

           */

          staging {

              initWith debug

              manifestPlaceholders = [hostName:"internal.example.com"]

              applicationIdSuffix ".debugStaging"

          }

      }

}
```

### **Cómo configurar variantes de productos**
   Crear tipos de productos es similar a crear tipos de compilación. Agrega variantes de productos al bloque productFlavors de tu configuración de compilación e incluye los parámetros de configuración que desees. Las variantes de productos admiten las mismas propiedades que defaultConfig, ya que defaultConfig en realidad pertenece a la clase [ProductFlavor](https://developer.android.com/reference/tools/gradle-api/current/com/android/build/api/dsl/ProductFlavor?hl=es-419 "https://developer.android.com/reference/tools/gradle-api/current/com/android/build/api/dsl/ProductFlavor?hl=es-419"). Eso significa que puedes proporcionar la configuración básica para todas las variantes en el bloque defaultConfig, y cada una puede cambiar cualquiera de estos valores predeterminados; por ejemplo, applicationId. Para obtener más información sobre el ID de aplicación, consulta [Cómo establecer el ID de aplicación](https://developer.android.com/studio/build/configure-app-module?hl=es-419#set-application-id "https://developer.android.com/studio/build/configure-app-module?hl=es-419#set-application-id"). 

**Nota:** No obstante, debes especificar un nombre de paquete usando el atributo [package](https://developer.android.com/guide/topics/manifest/manifest-element?hl=es-419#package "https://developer.android.com/guide/topics/manifest/manifest-element?hl=es-419#package") en el archivo de manifiesto main/. También debes usar ese nombre de paquete en tu código fuente para hacer referencia a la clase R, o bien resolver cualquier actividad o registro de servicio relacionados. Esto te permite usar applicationId para asignar a cada variante de producto un ID exclusivo para el empaquetado y la distribución, sin necesidad de cambiar el código fuente. 

   Todas las variantes deben pertenecer a una dimensión denominada, que es un grupo de variantes de productos. Debes asignar todas las variantes a una dimensión; de lo contrario, obtendrás el siguiente error de compilación.
## **Cómo configurar el módulo de la app**
### **Cómo establecer el ID de aplicación**
Cada app para Android tiene un ID de aplicación exclusivo similar a un nombre de paquete de Java o Kotlin (por ejemplo, *com.example.miapp*). Este ID permite identificar de manera exclusiva tu app en el dispositivo y en Google Play Store.

**Importante:** Una vez que publiques tu app, no debes cambiar el ID de aplicación. Si cambias el ID de aplicación, Google Play Store trata la carga como una app completamente diferente. Si quieres subir una versión nueva de tu app, debes usar el mismo ID de aplicación y [certificado de firma](https://developer.android.com/studio/publish/app-signing?hl=es-419 "https://developer.android.com/studio/publish/app-signing?hl=es-419") de cuando se publicó originalmente.

```gradle
android {    
  defaultConfig {
    applicationId "*com.example.myapp*"
    minSdkVersion 15
    targetSdkVersion 24
    versionCode 1
    versionName "1.0"
  }
}
```

![](Aspose.Words.4e276513-788f-4af8-9e8b-9cd31daeee0c.029.png)El ID de aplicación se define con la propiedad applicationId en la biblioteca build.gradle.kts, como se muestra aquí. Actualiza el valor de applicationId reemplazando com.example.myapp con tu ID de la aplicación:

## **Establecer el número de versión de la app**
### **¿Por que es importante el control de versiones?**
- Informar a los usuarios sobre el número de versión instalada y las versiones disponibles
- Otras apps pueden consultar información del número de versión de tu app
- Otros servicios que en los que publicas tu app también llegan a consultar esa información.

El sistema android usa la información de la versión de la ap para evitar las versiones obsoletas de la app, pero no impone restricciones de actualización o compatibilidad de terceros.

### **Como configurar la información de la versión de la app**

Los siguientes son ejemplos de como configurar la versión de la app.

Groovy
```Groovy
    android {
      namespace 'com.example.testapp'
      compileSdk 33

      defaultConfig {
          applicationId "com.example.testapp"
          minSdk 24
          targetSdk 33
          versionCode 1
          versionName "1.0"
          ...
      }
      ...
    }
    ...
```

Kotlin
```Kotlin
    android {
      namespace = "com.example.testapp"
      compileSdk = 33

      defaultConfig {
          applicationId = "com.example.testapp"
          minSdk = 24
          targetSdk = 33
          versionCode = 1
          versionName = "1.0"
          ...
      }
      ...
    }
    ...
```
#### Parámetros de configuración de la versión
**versionCode**
Este es solo un número de valor entero positivo que se usa como número de versión interno. Este no se muestra a los usuarios y mientras mayor sea más reciente es la aplicación. El sistema Android usa este valor para evitar que la app cambie a una versión inferior. El valor máximo que permite Google play para este valor es el 2,100,000,000 y google play no te permite subir una apk con un valor anterior.

**versionName**
Este es un valor tipo string que se usa como número y se muestra a los usuarios.