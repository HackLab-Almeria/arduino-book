
# Ejemplo de LEDs con colores aleatorios

En este ejemplo conectaremos una tira de 60 LEDs al pin 6 e iremos asignándole colores aleatorios.
En caso de usar una tira de menos LEDs, modificar la línea `#define LEDS 60` por lo que corresponda.


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
