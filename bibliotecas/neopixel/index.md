# Adafruit NeoPixel

Los tecnología NeoPixel nos permite enlazar multitud LEDs RGB y controlarlos con un solo cable de datos, ahorrándonos
multitud de cables y simplificando la instalación.

Para controlar cada uno de LEDs tendremos que usar biblioteca específica de _Adafruit_. Dicha biblioteca está disponible
su [GitHub][1], bastará con descargarla e instalarla.


## Ejemplo de LEDs con colores aleatorios

````c++

//Incluimos la biblioteca
#include <Adafruit_NeoPixel.h>

//Especificamos el número de LEDS de la tira
#define LEDS 60

//PIN en el que conectaremos el bus de datos
#define PIN 6

//Especificamos el brillo, de 0 a 255
#define BRILLO 200

//Declaramos la tira de LEDS
Adafruit_NeoPixel * strip;

void setup() {
    //Creamos la tira
    strip = new Adafruit_NeoPixel(LEDS, PIN, NEO_GRB + NEO_KHZ800);
    //Asignamos el brillo
    strip->setBrightness(BRILLO);
    //Iniciamos la tira. Es MUY importante.
    strip->begin();
}

void loop() {

   //Creamos un bucle que vaya de 0 a LEDs para ir asignando a cada
   //LED un color aleatrio
   for (int i = 0; i < LEDS; i++) {
        //Creamos un color, en este caso, aleatorio
        uint32_t color = Adafruit_NeoPixel::Color(random(0, 255), random(0, 255), random(0, 255));

        //Asignamos el color. El primer parámetro determina el LED al que le asignamos el color
        //y el segundo parámetro el color en cuestión
        strip->setPixelColor(i, color);
   }

   //Llamamos a "show" para actualizar los colores de los LEDS
   strip->show();

   //Esperamos 1 segundo antes actualizar los valores
   delay(1*1000);

}

````

### Semáforo con un solo LED



````c++

//Incluimos la biblioteca
#include <Adafruit_NeoPixel.h>

//PIN en el que conectaremos el bus de datos
#define PIN 6

//Especificamos el brillo, de 0 a 255
#define BRILLO 200

//Declaramos la tira de LEDS
Adafruit_NeoPixel * strip;

//Creamos los colores que vamos a utilizar según el esquema RGB
//Podemos consultar los valores RGB de un color en cualquier programa
//de dibujo como en el Paint.
uint32_t rojo      = Adafruit_NeoPixel::Color(255,  0,   0);
uint32_t verde     = Adafruit_NeoPixel::Color(  0, 255,  0);
uint32_t amarillo  = Adafruit_NeoPixel::Color(255, 255,  0);

void setup() {
    //Creamos la tira
    strip = new Adafruit_NeoPixel(1, PIN, NEO_GRB + NEO_KHZ800);
    //Asignamos el brillo
    strip->setBrightness(BRILLO);
    //Iniciamos la tira. Es MUY importante.
    strip->begin();
}

void loop() {

    //Lo ponemos de color rojo
    strip->setPixelColor(0, rojo);
    //Activamos el color
    strip->show();
    //Esperamos 2 segundos
    delay(2*1000);

    //Creamos un bucle para el parpadeo
    //del color amarillo
    for (int i = 0; i < 5; i++) {
       //Activamos el Amarillo
       strip->setPixelColor(0, amarillo);
       //Activamos el color
       strip->show();
       //Esperamos
       delay(200);
       //Apagamos (color 0)
       strip->setPixelColor(0, 0);
       //Activamos el color
       strip->show();
       //Esperamos
       delay(200);
    }


    //Lo ponemos de color verde
    strip->setPixelColor(0, verde);
    //Activamos el color
    strip->show();
    //Esperamos 2 segundos
    delay(2*1000);

}

````


[1]: https://github.com/adafruit/Adafruit_NeoPixel
