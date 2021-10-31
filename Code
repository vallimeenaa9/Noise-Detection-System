#include <ESP8266WiFi.h>;
#include <WiFiClient.h>;
#include <ThingSpeak.h>;
const int ledpin=4;
const int soundpin=5;
const int buzzer=2;
const char *ssid= "Voodoo13"; //WiFi to be connected
const char *password="abcde12345"; //WiFi password
const char* server="api.thingspeak.com";
WiFiClient client;
unsigned long myChannelNumber = 992869;
const char * myWriteAPIKey = "FDRJ24WFERJQHL1D"; // API Key of the project
void setup() {
 // put your setup code here, to run once:
 Serial.begin(115200);
pinMode(ledpin,OUTPUT);
 pinMode(soundpin,INPUT);
 pinMode(buzzer,OUTPUT);
delay(10);
WiFi.begin(ssid,password);
ThingSpeak.begin(client);
}
void loop() {
 // put your main code here, to run repeatedly:
 int soundsens=digitalRead(soundpin);
 if(soundsens==HIGH){
 digitalWrite(ledpin,HIGH);
 tone(buzzer,150);
 ThingSpeak.writeField(myChannelNumber,1,200,myWriteAPIKey);
 delay(1000);
 ThingSpeak.writeField(myChannelNumber,1,0,myWriteAPIKey);
 }
 digitalWrite(ledpin,LOW);
 noTone(buzzer);
}
/*This code is fed into the Node micro-controller unit using a computer system. This code is used to
bridge the gap between Thingspeak cloud service Database and the data gathered by our sound
sensor. It shows the visualizations and graphs of the data received by noise sensor. The signals
received by the noise sensor are of Analogue nature, i.e. it can detect only high and lows.
Whenever it will detect sound, the buzzer will make a buzzing sound so that we have a
acknowledgement that a sound is received.*/
