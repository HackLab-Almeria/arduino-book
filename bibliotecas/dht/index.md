# DHT

**DHT** es una biblioteca diseñada para usar los distintos sensores de humedad y temperatura, el DHT11, DHT22 y DHT 21.

Podremos descagarla desde su [GitHub][1]


### Ejemplo

```c++
//Incluimos la librería
#include "DHT.h"

//Indiciamos el pin en el que usamos el sensor
#define DHTPIN 2

//Definimos el tipo de sensor que usamos
//Los valores pueden ser DHT11, DHT21 o DHT 22
#define DHTTYPE DHT21


//Creamos el sensor
DHT dht(DHTPIN, DHTTYPE);


void setup() {
  //Iniciamos un puerto serie para visualizar
  //los datos mediante el puerto serie
  Serial.begin(9600);
  Serial.println("Iniciamos el programa");

  //Inicializamos el sensor de DHT
  dht.begin();

  //Esperamos unos segundos para que arranque
  //el sensor
  delay(2000);

}

void loop() {

  //Leemos la humedad
  float humedad = dht.readHumidity();
  //Leemos la temperatura
  float temperatura = dht.readTemperature();


  //Comprobamos que los datos son válidos
  if (isnan(humedad) || isnan(temperatura)) {
    Serial.println("Fallo al leer.");
    return;
  }


  //Mostramos toda la información mediante el serie.
  Serial.print("Humedad: ");
  Serial.println(humedad);
  Serial.print("Temperatura: ");
  Serial.println(temperatura);
}

```



[1]: https://github.com/adafruit/DHT-sensor-library
