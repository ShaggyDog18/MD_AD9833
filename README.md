# MD_AD9833 Library for Programmable Waveform Generator Module

Arduino library for managing AD9833 Programmable Waveform Generator by Analog Devices.

The AD9833 is a low power, programmable waveform generator capable of producing sine, triangular, and square wave outputs. The output frequency, phase and all other parameters are software programmable through an SPI interface.

This library features access to all on-chip features though an abstracted class and methods to coordinate register changes to implement user-level functionality.

Modified by **ShaggyDog18@gmail.com**, June 2020

## Modification Change Log

Modification allows an independent functionning of ON and OFF functions. Still 100% compatuble with the original library:
- introduced a new mode `MODE_ON`	to complement an existing `MODE_OFF`.
- added a new method  `setModeSD(mode_t mode)` to accompany the existing `setMode()` function. In the new method I've removed `bitClear` for `D_SLEEP1` and `AD_SLEEP12` bits (disabled ON function) for the following modes that essentially are used to change the form of the signal: `MODE_SINE, MODE_SQUARE1, MODE_SQUARE2, MODE_TRIANGLE`. 
Now, if the output signal is switched `OFF`, it would not get `ON` by changing the form of the output signal (as it is happening by using the stock `setMode()` function).

So, the signal can be separately switched on and off by the following commands (also works with the stock `setMode()` function):
```CPP
// switch ON the output module signal
sigGen.setModeSD( MD_AD9833::MODE_ON ); 
```
or
```CPP
// switch ON the output module signal
sigGen.setMode( MD_AD9833::MODE_ON ); 
```

```CPP
// switch OFF the output module signal
sigGen.setModeSD( MD_AD9833::MODE_OFF ); 
```
or
```CPP
// switch OFF the output module signal
sigGen.setMode( MD_AD9833::MODE_OFF ); 
```

**If you like and use the modified library, please, consider making a small donation using [PayPal](https://paypal.me/shaggyDog18/3USD)**
