#include <EEPROM.h>
#include <Servo.h>

Servo myservo;


int sensor1=A1;
int sensor2=A0 ;
int calswitch=2;

int val1;
int val2;

int pos=0;
int error;
int state;

void setup() 
{
  pinMode(sensor1,INPUT);
  pinMode(sensor2,INPUT);
  pinMode(calswitch,INPUT); 
  myservo.attach(13);
}

void loop() 
{
  if(digitalRead(calswitch)==0) 
  {
    myservo.detach();

    val1=analogRead(sensor1);
    val2=analogRead(sensor2);


    if (val1>300) 
    {
      error=val1-val2; 
      state=0; 
    }
    else 
    {
      error=val2-val1; 
      state=1; 
    }

    EEPROM.write(0,error);
    EEPROM.write(1,state);

    delay(10);
  }

  else
  {
    myservo.attach(13);

    val1=analogRead(sensor1);
    val2=analogRead(sensor2);

    state=EEPROM.read(1);
    error=EEPROM.read(0);

    if 
    (val1-val2>4) 
    {
      myservo.write(pos); 
      pos=pos-1; 
      delay(50);
    }
    else if (val2-val1>4) 
    {
      myservo.write(pos); 
      pos=pos+1; 
      delay(50);
    }
    else 
    {
      myservo.write(pos);
    }
    if (pos>90) 
    {
      pos=90;
    }
    else if(pos<0) 
    {
      pos=0;
    }

  }
}
