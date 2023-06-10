# Practica ESP32 con DHT22 CON LCD
Este repositorio muestra como podemos programar una ESP32 con el sensor DHT22 y mostrar la informacion en un LCD.

## Introducción

### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH22```) para adquirir temperatura y humedad del entorno Y en esta practica se añade un LCD para imprimir la informacio cadaa 1 seg; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT11
- Pantalla LCD



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(1000);
  lcd.setCursor(0,0);
  lcd.print("    DAIyM_2023  ");
  delay(1000);
  lcd.setCursor(0,1);
  lcd.print("    VARGAS_95    ");
  delay(1000);

}
```
2. Instalar la libreria de **DHT sensor library for ESPx** como se muestra en la siguente imagen.

![](https://raw.githubusercontent.com/DavidVar95/Practica_DHT22_con_LCD/abf0161d7d364f01ccb82441f23fd3ae766003a2/Captura%20de%20pantalla%202023-06-10%2008.02.20.png)

3. Instalar la libreria de **LiquidCrystal I2C** como se muestra en la siguente imagen.

![](https://github.com/DavidVar95/Practica_DHT22_con_LCD/blob/main/Captura%20de%20pantalla%202023-06-10%2008.03.20.png?raw=true)

4. Hacer la conexion de **DHT11** con la **ESP32** como se muestra en la siguente imagen.

![](![Alt text](image.png))

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT11** 

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguentes imagenes.

![](https://github.com/DavidVar95/Practica_DHT22_con_LCD/blob/main/Captura%20de%20pantalla%202023-06-10%2007.53.19.png?raw=true)

![](https://github.com/DavidVar95/Practica_DHT22_con_LCD/blob/main/Captura%20de%20pantalla%202023-06-10%2007.54.10.png?raw=true)



# Créditos

Desarrollado por Ing. David Vargas Gonzalez

- [GitHub](https://github.com/DiegoJm10)