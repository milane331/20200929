# 20200929
int va=255 ; int x=-15;
int a=-1,jj=0,b=0;
void setup() {
pinMode(3,OUTPUT);
pinMode(5,OUTPUT);
pinMode(6,OUTPUT);
pinMode(2,INPUT);
pinMode(7,INPUT);
digitalWrite(2,1);
digitalWrite(7,1);
byte ledpin[3]={3,5,6};



}

void loop()
{
  if(!digitalRead(7)) 
  {
    debounce(7);
    if(!jj)
    {
      a++;
      jj=1;
      
    }
  }
  else
  {
    jj=0;
     switch(a)
    {
      case 0:
      rgb(255,0,0);
      rgb(0,255,0);
      rgb(255,182,0);

      break;
       case 1:
       argb();
      break;
       case 2:
        ccc();
      break;
       case 3:
       a=0;
        break;
   }
  
 }
}
void debounce(byte value)
{
  while(!digitalRead(value))
  {
    rgb(0,0,0);
    delay(10);
  }
}
void rgb(byte r,byte g,byte b) 
{
analogWrite(3,r);
analogWrite(5,g);
analogWrite(6,b);

delay(1000);
}
void argb()
{
    
if(va <=0 || va>=255) x=-x;
analogWrite(3,va);
delay(20);
va=va-x;
}
void ccc()
{
  if(!digitalRead(2)) 
  {
    debounce(2);
    if(!jj)
    {
      b++;
      jj=1;
    }
  }
  else
  {
    jj=0;
    switch(b)
    {
      case 0:
          rgb(255,0,0);
      break;
      case 1:
           analogWrite(3,0);
           analogWrite(5,255);
           analogWrite(6,0);
       break;
     
      case 2:
           analogWrite(3,0);
           analogWrite(5,0);
           analogWrite(6,255);
      break;
      case 3:
           analogWrite(3,0);
           analogWrite(5,255);
           analogWrite(6,255);
      break;
      case 4:
           analogWrite(3,255);
           analogWrite(5,255);
           analogWrite(6,0);
      break;
      case 5:
           analogWrite(3,255);
           analogWrite(5,182);
           analogWrite(6,0);
      break;
      case 6:
      b=0;
      break;
    }
  }
}
