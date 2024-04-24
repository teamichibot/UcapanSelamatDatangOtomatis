/* UcapanSelamatDatangOtomatis
Program untuk membuat ucapan selamat datang otomatis ketika ada orang menggunakan arduino nano, sensor pir, dan modul speaker isd1820

bantu kami agar terus berkembang dengan berbelanja di store kami:
- arduino nano : https://tokopedia.link/1qUg1d9jPIb
- sensor PIR : https://tokopedia.link/9vWFUg6k3Ib
- Audio Recorder & Playback ISD1820 : https://tokopedia.link/M9M4CW7k3Ib */

int calibrationTime = 30; //the time when the sensor outputs a low impulse
long unsigned int lowIn;//the amount of milliseconds the sensor has to be low before we assume all motion has stopped
long unsigned int pause = 5000;

int PIR_PIN = 2;    //the digital pin connected to the PIR sensor's output
int LED_PIN = 3;   //the digital pin connected to the Output Status LED
int ISD_PIN = 4;  //the digital pin connected to ISD1820's P-E Pin

////
//SETUP
void setup(){
//Serial.begin(9600);
pinMode(PIR_PIN, INPUT);
pinMode(LED_PIN, OUTPUT);
pinMode(ISD_PIN, OUTPUT);

digitalWrite(LED_PIN, HIGH);
digitalWrite(ISD_PIN, LOW);

//give the sensor some time to calibrate
//Serial.print("calibrating sensor ");
for(int i = 0; i < calibrationTime; i++){
//Serial.print(".");
digitalWrite(LED_PIN,HIGH);
delay(300);
digitalWrite(LED_PIN,LOW);
delay(700);
} 
//Serial.println(" done");
//Serial.println("SENSOR ACTIVE");
digitalWrite(LED_PIN,LOW);
delay(50);
}
//LOOP
void loop(){
if(digitalRead(PIR_PIN) == HIGH ){


digitalWrite(LED_PIN, HIGH);   //the led visualizes the sensors output pin state
digitalWrite(ISD_PIN, HIGH);
delay(200);
digitalWrite(ISD_PIN,LOW);
delay(4800);
digitalWrite(LED_PIN,LOW);
}
}



