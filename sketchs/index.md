# Sketchs

Los _sketchs_ son los archivos de código que conforman un programa arduino. El fichero principal suele tener el mismo nombre que el proyecto
y terminar en `.ino`. Por ejemplo: **blink.ino**.

El fichero suele divirse en 4 partes.

```c++

/**
 * #### PARTE 1: Includes y defines ####
 *
 * Aquí se incluirán todos los ficheros y bibliotecas que componen nuestro programa
 * así como las definiciones
 */
 
//Incluimos la biblioteca para controlar servos
#include <Servo.h> 

//Incluimos las bibliotecas para usar los NeoPixel
#include <Adafruit_Neopixel.h> 

//Definimos el PIN_LED. Los defines son constantes que usamos en nuestro programa
//para mayor comidad. Si después cambiamos la posición del LED basta con modificar el 
//define en vez de buscar todos los sitios dónde habríamos puesto «13»
#define PIN_LED 13


/**
 * #### PARTE 2: Variables globales ####
 * 
 * Aquí definiremos las variables globales de nuestro código, que son aquellas que queremos que estén
 * accesibles desde cualquier lugar el programa
 */
 
 int ledStatus = LOW; //Definimos el valor del LED a LOW (apagado)
 
 
 /**
 * ### PARTE 3: Función setup() ####
 * 
 * La función setup() es una función que se ejecutará al encender nuestro arduino una única vez.
 * Se usa para inicializar valores y configurar los GPIOs.
 */
 
 void setup() {
    pinMode(PIN_LED, OUTPUT); //Configuramos nuestro PIN como modo salida.
    digitalWrite(PIN_LED, LOW); //Nos aseguramos que nuestro LED comienza como apagado.
 }
 
 
 /**
 * ### PARTE 4: Función loop() ####
 * 
 * La función loop() será la que se repita infinitamente en nuestro programa. 
 * Cada vez que termina de ejecutarse comienza a ejecutarse de nuevo desde el principio.
 * En ella definiremos el comportamiento de nuestro programa
 */
 
 void loop() {
 
    //Si el ledStatus está encendido, lo ponemos apagado y viceversa 
    if (ledStatus == LOW)
       ledStatus = HIGH;
    else
       ledStatus = LOW;
 
    //Ponemos el PIN al modo que corresponda
    digitalWrite(PIN_LED, ledStatus);
    
    //Esperamos 1 segundo (1000 milisegundos)
    delay(1000);
 
 }
 
```