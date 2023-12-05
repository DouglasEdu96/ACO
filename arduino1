#include <Wire.h>
#include <Adafruit_LiquidCrystal.h>

//Inicializamos el controlador de la pantalla
Adafruit_LiquidCrystal lcd_1(0);
//Establecemos pines del Arduino
const int pulsadorPines[] = {0, 1, 2, 3, 4, 5, 6};
//Definimos una matriz de respuestas para claves ABCD
const bool claveA[] = {true, false, false, false, true, false, false, false, true, false};
const bool claveB[] = {false, true, false, false, false, true, false, false, false, true};
const bool claveC[] = {false, false, true, false, false, false, true, false, false, false};
const bool claveD[] = {false, false, false, true, false, false, false, true, false, false};
int cont=0; //Contador de Respuestas correctas
int alumno=1; //Contador de alumnos
//Contador de pulsos
//Iniciado en -1 para hacer match con la posicion 0 de la 
//matriz de respuestas
int pulsos=-1;

void setup() {
  lcd_1.begin(16, 2);
  lcd_1.print("Proyecto ACO");
  lcd_1.setBacklight(1);  // Activa la retroiluminación
  //A continuacion un for para inicializar todos los pines
  for (int i = 0; i < 7; i++) {
    pinMode(pulsadorPines[i], INPUT_PULLUP);
  }
  lcd_1.clear();
  delay(200);
}

void loop() {
  //El siguiente codigo se ejecuta en el loop de Arduino
  lcd_1.setCursor(0, 0); //Fijando cursor
  lcd_1.print("Alumno: ");
  lcd_1.print(alumno);
  lcd_1.setCursor(0, 1);
  //Limitando pulsos a 10 pulsos por alumno
  if (pulsos<=10){
    //Los siguientes IF verifican cuando se presiona un pulsador
    //Y luego verifica que el numero de pulso coincida con la
    //respuesta correcta de la matriz
    if (digitalRead(pulsadorPines[2]) == HIGH){
      pulsos++;
      if (claveA[pulsos]==true){
        cont++; //Aumenta el contador solo cuando se cumple 
        //la condicion de ser la respuesta correcta
        lcd_1.print("Calificacion: ");
        lcd_1.print(cont);
      }
    }
    if (digitalRead(pulsadorPines[3]) == HIGH){
      pulsos++;
      if (claveB[pulsos]==true){
        cont++;
        lcd_1.print("Calificacion: ");
        lcd_1.print(cont);
      }
    }
    if (digitalRead(pulsadorPines[4]) == HIGH){
      pulsos++;
      if (claveC[pulsos]==true){
        cont++;
        lcd_1.print("Calificacion: ");
        lcd_1.print(cont);
      }
    }
    if (digitalRead(pulsadorPines[5]) == HIGH){
      pulsos++;
      if (claveD[pulsos]==true){
        cont++;
        lcd_1.print("Calificacion: ");
        lcd_1.print(cont);
      }
    }
  }
  // El siguiente IF es para pasar al proximo alumno
  if (digitalRead(pulsadorPines[6]) == HIGH){
    //Primero se regresan las variables cont y pulsos a su
    //valor inicial
      cont=0;
      pulsos=-1;
      lcd_1.print("Calificacion: ");
      lcd_1.print(cont);
      alumno++; //El contador de alumno aumenta
  }
}
