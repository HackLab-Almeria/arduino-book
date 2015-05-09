
# Semáforo con un solo LED

En este ejemplo crearemos un semáforo usando un solo LED RGB el cual iremos cambiando de color. Este LED estará
conectado al **pin 6**.


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
