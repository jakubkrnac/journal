[< home](https://github.com/jakubkrnac/journal)

# Electronics workshop

On today's workshop I have worked with [Nokia 5110 LCD](https://www.sparkfun.com/products/10168). I have previous experience with electronics and I have asked TAs whether it would be alright to work with the display istead.

I wired the display according to the [this guide](https://learn.sparkfun.com/tutorials/graphic-lcd-hookup-guide#hardware-assembly--hookup) and have used the Adafruit [library](https://github.com/adafruit/Adafruit-PCD8544-Nokia-5110-LCD-library) recommended for this LCD.

| LCD Pin	     | Arduino    | Pin	Notes                                             |
|--------------|------------|-------------------------------------------------------|
| 1 - VCC      | 3.3V (VCC) | 3.3V only (not 5V!)                                   |
| 2 - GND	     | GND	      |                                                       |
| 3 - SCE	     | 7          |	Can be any digital pin                                |
| 4 - RST	     | 6	        |	Can be any digital pin                                |
| 5 - D/C	     | 5	        |	Can be any digital pin                                |
| 6 - DN(MOSI) | 11	        | Can't be moved                                        |
| SCLK	       | 13         | Can't be moved                                        |
| LED          | 9          | Can be any PWM pin. 330Ω resistor in between the pins |

[Source](arn.sparkfun.com/tutorials/graphic-lcd-hookup-guide#hardware-assembly--hookup)

&nbsp;

![IMG_WIRING](https://user-images.githubusercontent.com/23638332/219662598-7c8848bf-0d9b-4b61-8faa-35ee4d8a4b5e.jpg)

(Different wiring than the guide mentioned above)

&nbsp;

After uploading the sketch to the Arduino board, the display appeared to do nothing. I have tried using different libraries as well as drifferent wiring combinationa. I have also tried hooking it up to the [Espruino Pico](https://www.espruino.com/Pico) board that we were provided, however non of this did work. 

I have noticed that some wiring guides power the display with 5 Volts, instead of 3.3 Volts ([3V3](https://imagedelivery.net/7FIW-iB8fZn595Ch5hs_rg/5fd9969d-3db3-4d50-52d4-dbeeb9265500/public), [5V](https://electronoobs.com/images/Arduino/tut_53/sch_1.png), [5V](http://www.multiwingspan.co.uk/images/arduino/nokia_bb.png), [3V3](http://www.multiwingspan.co.uk/images/arduino/nokia_bb.png)). Based on this, I have assumed that there might be different versions of the display breakout board. Since this was the only thing that I haven't tried yet, I decided to to try powering the LCD with 5 Volts.

Thid indeed did work! The display was now working as expected, displaying a demonstration graphics from the [Adafruit Graphics library](https://github.com/adafruit/Adafruit-GFX-Library).

&nbsp;

![IMG_LOGO](https://user-images.githubusercontent.com/23638332/219656977-49bbf5fd-14e9-43d3-8364-23f24cf609f7.jpg)

&nbsp;

jakubkrnac · 31 jan 2023 
