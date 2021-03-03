# interfacing 4x3 keypad with pic16F84A on 7segment using decoder 7448

whtat does it do?:

by pressing on button on 7segment shows the corresrpondent character:

note:::the program uses no timers interruptions only for() loop

CODE ON MIKROC FOR PIC:
```C
int i;
void main()
{
       PORTA=0;
       PORTB=0;

       //o registrador TRIS é aquele que determina se um pino/porta é entrada ou saida
       TRISA=0x00;   //saida
       TRISB=0xf0;  //entrada

       for(;;)
    {
       i=99;

      portb.f0=1;
      if(portb.f4){ i=1;}
      if(portb.f5) {i=4; }
      if(portb.f6){ i=7; }
      portb.f0=0;

      portb.f1=1;
      if(portb.f4) {i=2;}
      if(portb.f5) {i=5; }
      if(portb.f6) {i=8;}
      if(portb.f7){ i=0; }
      portb.f1=0;

      portb.f2=1;
      if(portb.f4) {i=3;}
      if(portb.f5) {i=6;}
      if(portb.f6){i=9;}
      portb.f2=0;

      if(i!=99)
     {
              PORTA=i;
     }
  }
}
```
