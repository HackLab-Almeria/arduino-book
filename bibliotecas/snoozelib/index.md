# Snoozelib

Snoozelib es una librería para arduino que permite poner arduino en modo bajo consumo. Snoozelib esta pensado para proyectos que requieran un bajo consumo y requieran una gran durabilidad de las baterias por ejemplo. Puede descargarse [aquí](https://github.com/zerasul/snoozeLib)

Esta librería se basa en el uso del WatchDog del microcontrolador que usa arduino (atmel). Puede ver más información en el siguiente enlace:

[watchDog Arduino](http://blog.bricogeek.com/noticias/arduino/como-utilizar-watchdog-con-arduino/)

Esta librería se basa en otra librería llamada [Narcoleptic](https://code.google.com/p/narcoleptic/).

Seguidamente se muestra un ejemplo de esta librería, haciendo uso de interrupciones para volver a encender el arduino.

```c++
/*********************************************************************************
 * SnoozeLib: This Arduino Library make the use of Low Power Mode                *
 * very Easy. This library Helps you make your arduino based microcontroller     *
 * use the Low Power Mode it use the WatchDog Functionallity and sleep the       *
 * CPU clock for low consumption.                                                *
 * Example: Interrupt WakeUp. This example Snooze the CPU and Wake Up by an      *
 * Interupt.                                                                     *
 * this library is under GNU GPL v3 license.                                     *
 * Version: 1.0.                                                                 *
 * Based on the library Narcoleptic: https://code.google.com/p/narcoleptic/      *
 * Author: Victor Suarez Garcia<suarez.garcia.victor@gmail.com>                  *
 *********************************************************************************/
#include <SnoozeLib.h>//Include the library

int state = HIGH;//Led State
void setup(){
  pinMode(6,OUTPUT);
  attachInterrupt(0,wakeup,RISING);//Attaching the 0 Interrupt(on Arduino UNO pin 2) for RISING.
  Serial.begin(9600);
}

void loop(){

  Serial.println("Snoozing...");
  snoozeLib.snooze(10000);//Snooze the CPU
  Serial.println("Wake UP!!");
  digitalWrite(6,state);
}

void wakeup(){ //Interrupt Handle Function
snoozeLib.wakeup(); //WakeUp The CPU
 state=!state;//Change the State
}
```
