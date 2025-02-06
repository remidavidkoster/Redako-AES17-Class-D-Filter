# Redako-AES17-Class-D-Filter

A compact AES17 / Class D Filter board based on the Audio Precision AUX0025, yet with slightly looser tolerances. 

The goal of this filter is to remove the switching noise from a class D amplifier output (and (optionally) divide the high voltage output down to a lower sense voltage) so it can accurately be measured with a regular audio interface. 

![](Images/Side.png)

![](Images/BottomSide.png)

# Schematics

The schematic is based on the AUX0025. The resistors and capacitors values are slightly different (for sourcing reasons), the inductors aren't giant coreless types (for size reasons), and the resistors also have smaller packages. The result is that the frequency response will be slightly different (but according to my simulations still properly flat in the 20Hz-20kHz band), there might be some more harmonic distortion (which I'll measure later, but planning to use this for amplifiers there's plenty of margin), and the filter's power rating is less than the Audio Precision version - which I'm not expecting to be a problem unless someone assembles it with low series resistors and shorts the output. 

![](Images/Filter.png)

# Series resistors

Besides the AUX0025's 22Ω output series resistor I have added two more, and a parallel resistor to ground, which can be switched with the output DIP switch. This will allow me to divide the output voltage down to a range my Cosmos ADC will swallow. What these values should be for someone else will depend entirely on the amplifier (voltage) you're planning to measure, the input range of your ADC / scope, and its input impedance. I have added an LTSpice simulation you can play with to determine what's best for you. 

![](Images/Resistors.png)

# Enclosure

I'm still looking for a simple extruded enclosure that'll nicely fit the boards. I have a CNC router here I'd be able to make the panel cutouts with. I'm hoping to find something like this in the right size: 

![](Images/Enclosure.png)

# Tests & Measurements

The frequency response looks pretty spot on. Here's the LTSpice simulation: 

![](Images/file-20250101152243354.png)

And here's the measured response:

![](Images/file-20250101151917224.png)

Measuring the THD is a bit more troublesome, as I don't have that good a DAC. The best I think I can do is playing a sine and comparing a loopback connection on my audio interface: 

![](Images/image-20250206100353339.png)

With the same lookback connection with the filter in between:

![](Images/image-20250206100506386.png)

The main difference I see is that the 2nd order harmonics seem to go from 0.00085% to 0.00110%. Still 60dB below the [audible threshold](https://www.klippel.de/listeningtest/)! More than good enough for me. 

# License

### CC BY-NC

