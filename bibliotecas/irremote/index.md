# IR Remote

La biblioteca _IR Remote_ nos permite utilizar infrarrojos en nuestro proyecto de forma muy sencilla.

Lo primero que tendremos que hacer es descargar la biblioteca desde su [GitHub][1]. La rama _master_ suele tener problemas,
por lo que se recomienda descargar una versión estable desde _tags_ y la instalamos.


Conectaremos el receptor como muestra la siguiente imagen

![Esquema](esquema.png)


En algunos receptores marcan los pines de la siguiente forma:

- **R**: Alimentación
- **G**: Tierra
- **Y**: Datos


Para **leer** datos mediante infrarrojos el sistema es muy sencillo:

```c++
//Incluimos la biblioteca
#include <Arduino.h>
#include <IRremote.h>

#define IR_PIN 11

IRrecv ir(IR_PIN);

decode_results read;

void setup() {

    Serial.begin(9600);
    ir.enableIRIn();

}

void loop() {

    if (ir.decode(&read)) {
        Serial.println(read.value, HEX);
        ir.resume();
    }

}
```

Dependiendo del botón pulsado en nuestro mando recibiremos un valor u otro. En caso de que **mantegamos pulsado el botón**
recibiremos `FFFFFFFF` como valor mientras mantegamos el botón pulsado.



[1]: https://github.com/shirriff/Arduino-IRremote