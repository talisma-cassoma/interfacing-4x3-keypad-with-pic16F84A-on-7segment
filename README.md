# interfacing 4x3 keypad with Microcontroller pic16F84A on 7segment using decoder 7448

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

       //o registrador TRIS é aquele que determina se um 
       //pino/porta é entrada ou saida
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

## How keypad works & How to scan them?

The working principle is very simple. Pressing a button shorts one of the row lines to one of the column lines, allowing current to flow between them. For example, when key ‘4’ is pressed, column 1 and row 2 are shorted.
<p align="center">
<img src="https://lastminuteengineers.com/wp-content/uploads/arduino/4x3-Membrane-Keypad-Working.gif">
</p>
4x3 Membrane Keypad Working
A microcontroller can scan these lines for a button-pressed state. To do this, it follows below procedure.

Microcontroller sets all the column and row lines to input.
Then, it picks a row and sets it HIGH.
After that, it checks the column lines one at a time.
If the column connection stays LOW, the button on the row has not been pressed.
If it goes HIGH, the microcontroller knows which row was set HIGH, and which column was detected HIGH when checked.
Finally, it knows which button was pressed that corresponds to detected row & column.
this excerpt was taked from https://lastminuteengineers.com/arduino-keypad-tutorial/

## keypad algorithm
::with for loop


::with timer interruptions 
