# GPIOs

Los GPIOs son salidas digitales que admiten solo dos estados, _HIGH_ (encendido o 1), y LOW (apagado o 0). Pueden ser
configurados para entrada o para salida, permitiendo _leer_ o _escribir_ información respectivamente.

Los GPIOs disponen de varios modos,

 - **OUTPUT**: De salida, permitirá enviar una señal de _HIGH_ o _LOW_.
 - **INPUT**: De entrada, permitirá leer el valor conectado al pin, si no está conectado a nada puede devolver cualquier valor.
 - **INPUT_PULLUP**: De entrada, funciona igual que _INPUT_ salvo que devolverá _HIGH_ salvo que se conecte a una entrada _LOW_.

 Para usar un GPIO lo primero será definir su modo, normalmente la función `void setup()` mediante `pinMode()`


 ```c++
 void setup() {
    //Establecemos el pin 13 como salida
    pinMode(13, OUTPUT);

    //Establecemos el pin 10 como entrada
    pinMode(10, INPUT);
 }
 ```

 Posteriormente podremos _leer_ o _escribir_ con las funciones _digitalRead()_ y _digitalWrite()_.

 ```c++
 void loop() {
    //Escribimos el valor HIGH en el pin 13
    digitalWrite(13, HIGH);

    //Leemos el valor del pin 10
    int status = digitalRead(10);

 }

 ```
 Adicionalmente, los GPIOs pueden utilizarse para controlar dispositivos más avanzados mediante el uso de ciertas bbliotecas como veremos más tarde.

