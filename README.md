# Documento Integración SDK React Native
### CONFIDENCIALIDAD

La información contenida en el presente documento es CONFIDENCIAL, hace parte del secreto comercial e industrial de la empresa e implica transmisión de información cuya propiedad corresponde exclusivamente a BYTTE SAS. En consecuencia, la divulgación o el uso inapropiado de la información aquí contenida por parte del receptor de la misma, implicarán la aplicación de las normas legales pertinentes para su debida protección.

### 1. INTRODUCCIÓN

#### Propósito General del Documento

El presente documento tiene como finalidad dar a conocer el paso a paso de la instalación del SDK provisto por Bytte en una aplicación hibrida generada en React Native.

#### 1.1. Objetivo

El presente documento tiene como objetivo explicar basado en un ejemplo, cómo realizar la integración del SDK Bytte a una aplicación React Native.

#### 1.2. Factores Limitantes

Los factores limitantes para la integración del SDK son:
* El Plugin SDK Bytte, está disponible para plataformas IOS y Android únicamente.
* Se recomiendan cámaras con resolución mayores o iguales a 8 Mega Pixeles para un óptimo rendimiento.
* Se debe verificar la calidad de la cámara, es recomendable utilizar dispositivos con cámara que tengan la característica de “Auto Foco” habilitada.
* El SDK no funciona sobre dispositivos virtuales, únicamente sobre dispositivos físicos IPhone y Android.

### 2. INSTALACIÓN

#### 2.1. Pre requisitos

* General:
    > * NPM (sistema de gestión de paquetes)

* Para la compilación de aplicación en plataforma IOS, se requiere:
    > * XCode 12 o Superior con SDK IOS 12 o superior.

#### 2.2. Instalación Plugin react-native-bytte-bio-lib-ID

#### 2.2.1 Configuración Token

#### 2.2.1.1 MAC

Una vez instalado NPM (sistema de gestión de paquetes). En la ruta por defecto de instalación se debe encontrar el archivo .npmrc, si no se encuentra se debe crear a nivel de usuario.

Una vez detectado el archivo se debe configurar de la siguiente manera.

Copie el siguiente código a su .npmrc.


```
; begin auth token
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/react-native-rn-bytte-bio-lib-miid/npm/registry/:username=BytteTFS
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/react-native-rn-bytte-bio-lib-miid/npm/registry/:_password=[BASE64_ENCODED_PERSONAL_ACCESS_TOKEN]
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/react-native-rn-bytte-bio-lib-miid/npm/registry/:email=npm requires email to be set but doesn't use the value
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/react-native-rn-bytte-bio-lib-miid/npm/:username=BytteTFS
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/react-native-rn-bytte-bio-lib-miid/npm/:_password=[BASE64_ENCODED_PERSONAL_ACCESS_TOKEN]
//byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/react-native-rn-bytte-bio-lib-miid/npm/:email=npm requires email to be set but doesn't use the value
; end auth token
```
En el espacio (BASE64_ENCODED_PERSONAL_ACCESS_TOKEN) se debe ingresar el password enviado por Bytte s.a.s.

#### 2.2.1.2 WINDOWS

Una vez instalado NPM (sistema de gestión de paquetes). Se debe ejecutar el siguiente comando en la terminal.

``` vsts-npm-auth -config .npmrc```

este comando creará un archivo .npmrc en la ruta por defecto C:\Users\USER\\.npmrc

Una vez detectado el archivo se debe configurar de la siguiente manera.

```
registry=https://byttetfs.pkgs.visualstudio.com/c1dcbe70-4508-4f44-bfa8-e50bdbfea41f/_packaging/react-native-rn-bytte-bio-lib-miid/npm/registry/
```
                        
always-auth=true


# react-native-bytte-bio-lib-miid

#### 2.2.2 Instalación 

`$ npm install react-native-bytte-bio-lib-id`


Una vez instalado el plugin, se debe realizar la consulta a la aplicación para verificar que este quedó correctamente instalado.

### Configuración Plataformas
#### 2.3. Configuración nativo iOS (XCode)
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

#### 2.4. Configuración nativo Android
## Android

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
``` npm i react-native-rn-bytte-bio-lib-miid --save```

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
        

### 2. USO
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

#### Captura Código QR
```javascript
import {NativeModules} from 'react-native'

//captura Código qr
    onCaptureQR = () => {
        NativeModules.RnBytteBioLibMiid.startQr(license,timeOut,(response)=>{
            var obj = JSON.parse(response);
            if(obj.StatusOperacion){
                alert(obj.MensajeOriginal + '\n' + '\n' + "DataQR: " + obj.QR.Data);
            } else {
                alert(obj.MensajeOriginal);
            } 
        }); 
    }
```
## Ejemplo Demo

URL:  [http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/MiiD/bytteTest.zip](http://www.bytte.com.co/ftpaccess/Varios/CarlosG/ReactNative/MiiD/bytteTest.zip)





