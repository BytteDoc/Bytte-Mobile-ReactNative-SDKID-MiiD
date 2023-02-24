# Bytte SAS


# react-native-bytte-bio-lib-miid

## Instalación

`$ npm i react-native-rn-bytte-bio-lib-miid --save`

### Configuración Plataformas


## iOS

######   Adicionar la implementación bytte a su proyecto NPM
para esta implementación se puede generar desde npm integrando de la siguiente forma: 

``` npm i react-native-rn-bytte-bio-lib-miid --save```

Luego de instalar las dependencias npm se ingresa a la carpeta ***ios*** y se ejecuta el comando `pod install`

    $ cd ios
    $ pod install

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/podinstall.png)

Luego se ingresa al proyecto IOS y en la sección  ***Development Pods*** se busca la carpeta  ***RNBytteBioLibMiiD*** donde se encuentra los archivos correspondientes a la libreria. En la carpeta ***Frameworks*** se encuentran los binarios que deben ser embebidos de manera local al proyecto.

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/framework4.png)

Una vez agregados se valida que se encuentren  ***Embed & sign*** 

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/framework5.png)

######   Configuración Framework Search Paths

Se optiene la ruta donde se encuentran los Framework bytte y se configura en Framework Search Paths

Ruta por defecto : ***Ruta_Proyecto***/bytteTest/node_modules/react-native-bytte-bio-lib-miid/ios/Frameworks

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/framework2.png)

######   Configuración Pod RNBytteBioLib Framework Search Paths

Se optiene la ruta donde se encuentran los Framework bytte y se configura en ***pod*** ***RNBytteBioLibMiiD*** Framework Search Paths

Ruta por defecto : ***Ruta_Proyecto***/bytteTest/node_modules/react-native-bytte-bio-lib-miid/ios/Frameworks

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/framework3.png)

###### Licencia captura dactilar

Bytte proporciona el archivo de licencia para captura dactilar. Este archivo debe ser guardado en la raiz del proyecto IOS y embebido como recurso en la aplicación nativa tal como lo muestra la siguiente imagen.

![Directories](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/framework6.png)

El nombre del archivo se envía por parámetro ***(namePath)*** en la captura dactilar.


######   Permisos
Los permisos en runtime deben ser solicitados por la app para el uso de bytte es necesario el siguiente:
configurar en el archivo Info.plist para el uso de la ***Camara***

`Privacy - Camera Usage Description`
# Android

* **Se debe verificar la calidad de la cámara, es recomendable utilizar dispositivos con cámara que tengan la característica de “Auto Foco” habilitada**
* **Se recomiendan cámaras con resolución mayores o iguales a 5 Mega Pixeles para un óptimo rendimiento**
* **El SDK no funciona sobre dispositivos virtuales, únicamente sobre dispositivos físicos IPhone y**
* **Sistemas soportados Android 5.0 o superior gradle 4.1.2 o superior arquitecturas x86,64 bits**


### Para compilación de aplicación en plataforma Android, se requiere:
* **Java JDK Versión 1.8**
* **Android SDK** 
* **Funciona con Android 5.0 o superior**
* **Para el uso de la licencia identy es necesario registrar el app Pakage ID**  
* **Para generar la llave safetyNet api key busca los detalles del resgistro**
en https://developer.android.com/training/safetynet/attestation 
* **Desarrollador SHA1 Key. Cada desarrollador necesita un par de claves para firmar aplicaciones: una para debug y otra para el modo de release. Estos HASH también deben estar asociados con la licencia.**

## licencia  Android para el uso de huellas
* **crear una carpeta en el direccorio android llamada assets**
Dentro de esa carpeta depositamos el archivo de licencia que se generara para la implementación en debug y otra para reléase


## Luego vamos a generar la llave safetynet 
https://developer.android.com/training/safetynet/attestation
en la url se muestran los detalles para solicitar la llave safetynet 


## Los permisos en runtime deben ser solicitados por la app
para el uso de bytte es necesario los siguientes:
uso de ***Camara y almacenamiento***
`<uses-permission android:name="android.permission.CAMERA" />`
`<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>`
######   Adicionar la implementación bytte a su proyecto 
``` npm i react-native-bytte-bio-lib --save```

Luego vamos a android en la app, para la configuración en el archivo `build.gradle` del proyecto

`android/build.gradle`:

##### en la etiqueta 
   ``` 
allprojects {
    repositories {
          maven {
        url 'https://multifactorbyttelibrary.pkgs.visualstudio.com/BytteSDKLibraryX/_packaging/BytteSDKIdenty/maven/v1'
        name 'BytteSDKIdenty'
        credentials {
            username ""
            password ""
        }
    }
    }
}

   ``` 

Solicitar a **Bytte lo siguiente:**   ingresarlo dentro de los "" 
- **username**
- **password**


Tener en cuenta que debe estar habilitado multidex para android revisar la documentación para generarlo en react-native
' multiDexEnabled true'
Las librerías bytte soportan las arquitecturas a 32 y 64 bits necesarias para Android
 ndk{
             abiFilters  "armeabi-v7a", 'arm64-v8a'
        }
        
## Uso
```javascript
import { NativeModules } from 'react-native';

const { RnBytteBioLibMiid } = NativeModules;

export default RnBytteBioLibMiid;
```

## Metodos react-native-bytte-bio-lib-miid

#### Captura Documento Reverso
```javascript
import {NativeModules} from 'react-native'

//Captura documento reverso
    onCaptureBackDocument = () =>{
        NativeModules.RnBytteBioLibMiid.startBarCode(license,key,timeOut,pais,(response)=>{
            var obj = JSON.parse(response);
            if(obj.StatusOperacion){
                alert(obj.MensajeOriginal + '\n' + '\n' + obj.NombresCompletos + '\n' + "Sexo: " + obj.Sexo + '\n' + "Fecha Nacimiento: " + obj.FechaNacimiento + '\n' + "RH: " + obj.RH);
            } else {
                alert(obj.MensajeOriginal);
            } 
        }); 
    }
```

#### Captura Documento Frente
```javascript
import {NativeModules} from 'react-native'

 //Captura documento frente
    onCaptureFrontDocument = () =>{
        NativeModules.RnBytteBioLibMiid.startFrontDocument(license,key,timeOut,pais,(response)=>{
            var obj = JSON.parse(response);
            if(obj.StatusOperacion){
                alert(obj.MensajeOriginal + '\n' + '\n' + obj.Nombres + '\n' + obj.Apellidos + '\n' + obj.NumeroCedula);
            } else {
                alert(obj.MensajeOriginal);
            } 
        });
    }
```

#### Captura Facial
```javascript
import {NativeModules} from 'react-native'

//Facial capture
    onCaptureFace = () =>{
        NativeModules.RnBytteBioLibMiid.startFace((response)=>{
            var obj = JSON.parse(response);
            if(obj.StatusOperacion){
                alert(obj.MensajeOriginal);
            } else {
                alert(obj.MensajeOriginal);
            } 
        }); 
    }
```

#### Captura Dactilar
```javascript
import {NativeModules} from 'react-native'

//Fingerprint
    onCaptureFinger = () => {
        NativeModules.RnBytteBioLibMiid.startFinger(finger,namePath,netkey,(response)=>{
            var obj = JSON.parse(response);
            if(obj.StatusOperacion){
                alert(obj.MensajeOriginal);
            } else {
                alert(obj.MensajeOriginal);
            } 
        }); 
    }
```

## Ejemplo Demo

URL:  [http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/MiiD/bytteTest.zip](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/MiiD/bytteTest.zip)




