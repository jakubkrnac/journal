[< home](https://github.com/jakubkrnac/journal)

# Electronics workshop

&nbsp;

On today's workshop I have worked with [Nokia 5110 LCD](https://www.sparkfun.com/products/10168). I have previous experience with electronics and I have asked TAs whether it would be alright to work with the display istead.

I wired the

| LCD Pin	     | Arduino    | Pin	Notes              |
|--------------|------------|------------------------|
| 1 - VCC      | 3.3V (VCC) | 3.3V only (not 5V!)    |
| 2 - GND	     | GND	      |                        |
| 3 - SCE	     | 7          |	Can be any digital pin |
| 4 - RST	     | 6	        |	Can be any digital pin |
| 5 - D/C	     | 5	        |	Can be any digital pin |
| 6 - DN(MOSI) | 11	        | Can't be moved         |
| SCLK	       | 13         | Can't be moved         |
| LED          | 9          | Can be any PWM pin. 330Ω resistor in between the pins |


```
#define RST 3
#define CE  4
#define DC  5
#define DIN  6
#define CLK  7

void LcdWriteCmd(byte cmd) {
  digitalWrite(DC, LOW); //DC pin is low for commands
  digitalWrite(CE, LOW);
  shiftOut(DIN, CLK, MSBFIRST, cmd); //transmit serial data
  digitalWrite(CE, HIGH);
}

void setup() {
  pinMode(RST, OUTPUT);
  pinMode(CE, OUTPUT);
  pinMode(DC, OUTPUT);
  pinMode(DIN, OUTPUT);
  pinMode(CLK, OUTPUT);
  digitalWrite(RST, LOW);
  digitalWrite(RST, HIGH);
  
  LcdWriteCmd(0x21);  // LCD extended commands
  LcdWriteCmd(0xB8);  // set LCD Vop (contrast)
  LcdWriteCmd(0x04);  // set temp coefficent
  LcdWriteCmd(0x14);  // LCD bias mode 1:40
  LcdWriteCmd(0x20);  // LCD basic commands
  LcdWriteCmd(0x09);  // LCD all segments on
}

void loop() {}
```

&nbsp;

![IMG_LOGO](https://user-images.githubusercontent.com/23638332/219656977-49bbf5fd-14e9-43d3-8364-23f24cf609f7.jpg)

&nbsp;

![IMG_WIRING](https://user-images.githubusercontent.com/23638332/219656159-1bf6919d-7714-4af1-806e-25af3359b661.jpg)


&nbsp;

jakubkrnac · 31 jan 2023 
