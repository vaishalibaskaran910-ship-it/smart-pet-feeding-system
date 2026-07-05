# smart-pet-feeding-system
Designed and developed an IoT-based Smart Pet Feeding System featuring automatic feeding schedules, remote control through Blynk, live video streaming using ESP32-CAM, and GSM-based emergency notifications.
Smart Pet Feeding System, here’s a basic example using NodeMCU + Servo + Blynk.
#define BLYNK_TEMPLATE_ID "TMPLxxxx"
#define BLYNK_TEMPLATE_NAME "Pet Feeder"
#define BLYNK_AUTH_TOKEN "YourAuthToken"

#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>
#include <Servo.h>

char ssid[] = "WiFi_Name";
char pass[] = "WiFi_Password";

Servo feederServo;

BLYNK_WRITE(V0)
{
  int value = param.asInt();

  if(value == 1)
  {
    feederServo.write(90);
    delay(2000);

    feederServo.write(0);
  }
}

void setup()
{
  Serial.begin(115200);

  feederServo.attach(D4);
  feederServo.write(0);

  Blynk.begin(BLYNK_AUTH_TOKEN, ssid, pass);
}

void loop()
{
  Blynk.run();
}
Servo Feeding Function
void feedPet()
{
   feederServo.write(90);
   delay(2000);

   feederServo.write(0);
}
