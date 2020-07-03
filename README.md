# MD_AD9833

Library for using a AD9833 Programmable Waveform Generator hardware by Analog Devices.

The AD9833 is a low power, programmable waveform generator capable of producing sine, triangular, and square wave outputs. The output frequency, phase and all other parameters are software programmable through an SPI interface.

This library features access to all on-chip features though an abstracted class and methods to coordinate register changes to implement user-level functionality.

## Change Log

The library was modified to allow right functionning of ON / OFF feature. Still 100% compatuble with the original library.
- introduced a new mode `MODE_ON`	to complement an existing `MODE_OFF`.
- added a new method  `setModeSD(mode_t mode)` to accompany an existing `setMode()` function. I removed `bitClear` for `D_SLEEP1` and `AD_SLEEP12` for the following modes (these are, essentially, used to change the form of the signal): `MODE_SINE, MODE_SQUARE1, MODE_SQUARE2, MODE_TRIANGLE`. 
Now, if the output signal is switched `OFF`, it would not get `ON` by operation of changing the form on the signal (as it is happening by using the stock `setMode()` function).

So, the signal can be separately switched on and off by the following commands (also works with the stock `setMode()` function):
```CPP
// ON the output module signal
sigGen.setModeSD( MD_AD9833::MODE_ON ); 

// OFF the output module signal
sigGen.setModeSD( MD_AD9833::MODE_OFF ); 
```

**If you like and use the library please consider making a small donation using [PayPal](https://paypal.me/shaggyDog18/3USD)**
