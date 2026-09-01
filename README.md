# Repositorio-2
<img width="1902" height="865" alt="image" src="https://github.com/user-attachments/assets/3e8867eb-20eb-408f-8570-57eb6e058375" />

// Variables
int buzzer = 3;
int btn = 2;

int t = 200;
int leds;

void setup() {
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);

  pinMode(buzzer, OUTPUT);
  pinMode(btn, INPUT);

  randomSeed(analogRead(A0));
}

void rebote() {
  if (digitalRead(btn) == HIGH) {

    int sonido = random(300, 2000);

    tone(buzzer, sonido);
    delay(500);
    noTone(buzzer);

    t = t - 20;

    if (t < 50) {
      t = 200;
    }
  }
}

void loop() {

  for (leds = 5; leds <= 9; leds++) {
    digitalWrite(leds, HIGH);

    rebote();

    delay(t);

    digitalWrite(leds, LOW);
  }

  for (leds = 8; leds >= 6; leds--) {
    digitalWrite(leds, HIGH);

    rebote();

    delay(t);

    digitalWrite(leds, LOW);
  }

}

 Descripción del circuito

Este circuito es un sistema de luces LED con efecto de rebote y sonido, elaborado con un Arduino UNO. Los cinco LED se encienden de forma consecutiva, primero de izquierda a derecha y luego regresan en sentido contrario, creando un efecto de movimiento. Además, cuenta con un botón que permite activar un sonido mediante un buzzer y modificar la velocidad de la secuencia de luces.

 Componentes
Arduino UNO: controla las luces, el botón y el buzzer.
5 LED: producen la secuencia de luces.
5 resistencias: protegen los LED limitando la corriente.
1 botón pulsador: activa el sonido y cambia la velocidad.
1 buzzer: genera un sonido de frecuencia aleatoria.
1 protoboard: permite montar y conectar los componentes.
Cables jumper: realizan las conexiones entre los componentes.

 Funcionamiento

Al iniciar, los LED conectados a los pines 5, 6, 7, 8 y 9 se encienden uno por uno hasta llegar al último y después regresan, formando un efecto de rebote.

Cuando se presiona el botón conectado al pin 2, el buzzer del pin 3 emite un sonido durante un corto período. Al mismo tiempo, el programa reduce el tiempo entre cada LED, haciendo que la secuencia sea más rápida. Si la velocidad llega a ser demasiado alta, vuelve al tiempo inicial de 200 ms.
