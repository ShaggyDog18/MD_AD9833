# MD_AD9833

Library for using a AD9833 Programmable Waveform Generator hardware by Analog Devices.

The AD9833 is a low power, programmable waveform generator capable of producing sine, triangular, and square wave outputs. The output frequency, phase and all other parameters are software programmable through an SPI interface.

This library features access to all on-chip features though an abstracted class and methods to coordinate register changes to implement user-level functionality.

## Change Log

The library was modified to allow right functionning of ON / OFF feature. Still 100% compatuble with the original library.
- introduced a new mode **MODE_ON**	 
- introduced a new method  **boolean setModeSD(mode_t mode)** to accompany an existing one. I removed bitClear for AD_SLEEP1 and AD_SLEEP12 for MODE_SINE, MODE_SQUARE1, MODE_SQUARE2, MODE_TRIANGLE. Now, if signal is switched off, it would not get ON by changing the form on the signal.

So, the ginal can be separately switched on and off by the following command:
```CPP
sigGen.setModeSD( signalOn ? MD_AD9833::MODE_ON : MD_AD9833::MODE_OFF); 
```

**If you like and use the library please consider making a small donation using [PayPal](https://paypal.me/shaggyDog18/3USD)**