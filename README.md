# voice-commands-based-LED-scrooling-display
3.4 Program code:
#include <TimerOne.h>
#include"SPI.h"
#include <ledP10.h>
LedP10 myled;
char voice[99];
int i = 0;
void setup() 
{
    myled.init(3,4,8,9 ,2);
      Serial.begin(9600);
    Serial.println("!WELCOME");    
}
void loop() 
{
    while(Serial.available())
    {
        delay(1);
        char c=Serial.read();
          voice[i] = c;
          i++;
    }
    voice[i] = 0;
    if (i > 3) 
    {
           i = 0;
            myled.showmsg_single_scroll(voice,99,4,0); // (msg,no.of Times,speed(0 to 20),Font)
            delay(10);
    }
    delay(70);   
}
[code.docx](https://github.com/SOORAMNIKITHA/voice-commands-based-LED-scrooling-display/files/6326871/code.docx)
