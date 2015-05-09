# Adafruit NeoPixel

Los tecnología NeoPixel nos permite enlazar multitud LEDs RGB y controlarlos con un solo cable de datos, ahorrándonos
multitud de cables y simplificando la instalación.

Para controlar cada uno de LEDs tendremos que usar biblioteca específica de _Adafruit_. Dicha biblioteca está disponible
su [GitHub][1], bastará con descargarla e instalarla.


Para _controlar_ la tira deberemos crear un objeto `Adafruit_NeoPixel`:

```c++
    Adafruit_NeoPixel * strip = new Adafruit_NeoPixel(LEDS, PIN, NEO_GRB + NEO_KHZ800);
```

Dónde `LEDS` es el número de LEDs de nuestra tira y `PIN` el GPIO en el que está conectado. Ha de ser un GPIO del tipo
**PWM**.

Posterioremente, podremos asignar un color a cada uno de los LEDs mediante `setPixelColor` y llamamos a `show` para actualizar
la tira.

```c++

//Creamos una variable con el color que queramos
uint32_t rojo = Adafruit_NeoPixel::Color(255,  0,   0);
//Asignamos el color al LED número 4
strip->setPixelColor(4, rojo);

//También podemos asignar el color con el patrón RGB directamente,
//en este caso estamos colocando el LED 6 de color verde
strip->setPixelColor(6, 0, 255, 0);

//Finalmente actualizamos la tira llamando a show
strip->show();
```

[1]: https://github.com/adafruit/Adafruit_NeoPixel
