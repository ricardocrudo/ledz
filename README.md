ledz
====

Library to control LEDs, implemented in C. It supports single, bicolor or tricolor LEDs.
The library is designed to use only static memory allocation and it can be used with any
microcontroller.

Features
---

* CPU agnostic implementation
* use only static memory allocation
* widely configurable via macros


How to install
---

Simply copy the content of src directory to your work directory.


Configuration
---

The configuration of the library is done by setting 'define' macros in the header file,
under the configuration section.

There are two mandatory configurations before the use, the GPIO include file and the
setting of the *LEDZ_GPIO_SET* macro. In the include files section replace the line
`#include "gpio.h"` with the include of your GPIO library. Then, in the configuration
section, adjust the macro *LEDZ_GPIO_SET* to the "set gpio" function of your library.

To use the library with an Arduino the configuration would be:

    #include <Arduino.h>
    // ...
    #define LEDZ_GPIO_SET(port,pin,value)   digitalWrite(pin,value)

The other settings are optional and can be adjusted as needed. The macro *LEDZ_MAX_INSTANCES*
is used to define the total amount of LEDs being controlled by the library. Note that a RGB
LED requires three LEDs. For example, if you have two RGB LEDs on your system, you have to set
*LEDZ_MAX_INSTANCES* to the value 6.
The macro *LEDZ_TURN_ON_VALUE* defines if the LED turns on with high or low logic. Finally, the
*LEDZ_TICK_PERIOD* macro is used to set the interrupt service routine (ISR) period.

How to use
---

Once the configuration is done the library is ready to be used. However, if you want to use any
time-based function, as `ledz_blink` you must place the call of `ledz_tick`function in the ISR.

Remark: this library does not configure the GPIO direction, you have to do it before use any LED
control function.

To see more details how to use the library, please check the online
[API documentation](http://ricardocrudo.github.io/ledz).

License
---

MIT
