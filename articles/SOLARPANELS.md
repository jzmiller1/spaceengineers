Solar Panels and Where Are We?
==============================

## Testing Solar Panels

I'm new to Space Engineers and solar panels as of June 2014 so I attached a solar panel to a ship to find out the maximum power generation from a single panel.  I had previously only built a solar panel on a station and quickly found out that the orientation of the panel matters.  I built my first panel on the back side of my asteroid and surprise...no sun.  

![Solar Panel Testing Ship](https://raw.githubusercontent.com/jzmiller1/spaceengineers/master/images/SOLARPANEL/PanelTester.png)

After pointing the panel directly at the sun I disovered that 6 kilowatts is the maximum output and distance to the sun didn't seem to change that very much.  I tested distance by moving 50,000 km closer to the sun and noting that nothing changed.


## Lots of Questions

I know a little bit about physics and solar panels so I thought that I could discover where in the solar system we are based on the solar panel power.  I actually don't know the backstory for the game so I'm not sure if we are actually in the solar system...so I'm going to make a few assumptions:

0. We are in the solar system and the "sun" is the Sun.
1. Assume that the "sun" is a blackbody with a surface temperature of 6000 Kelvin
2. The sun has a radius of 696,000,000 meters (696,000km)

![Solar Panel Scale](https://raw.githubusercontent.com/jzmiller1/spaceengineers/master/images/SOLARPANEL/PanelScale.png)


From this image I worked out a rough estimate of the area of the solar panel:

* 5 astronauts tall x 3 astronauts wide
* assume 6 foot astronaut
* 30 foot x 18 foot
* 540 square feet -> 50 Square Meters
* Max generation is 6kW -> 6000 Watts

6000 Watts / 50 Square Meters -> 120 W/m^2



If the sun is a blackbody we can apply the [Stefan-Boltzmann law](http://en.wikipedia.org/wiki/Stefan%E2%80%93Boltzmann_law) to find how much energy it is putting out:

```
Radiative Energy = 5.6697x10^-8 W/m^2K^4 * (6000K)^4
                 = 7.35x10^7 W/m^2
```

This is the amount of energy per square meter.
What is the total radiative energy output of the sun?

```
Surface Area of sun = 4 *  pi * r^2
                    = 4 * pi * 696000000^2
                    = 6.08 x 10^18m^2

Total radiative energy = 6.08 x 10^18m^2 * 7.35x10^7 W/m^2
                       = 3.87 x 10^26 W (aka Joules per second)
```

So we know how much energy the sun is releasing and we know how much energy our panel is recieving.
The energy falls off as our distance from the sun increases according to the [inverse square law](http://en.wikipedia.org/wiki/Inverse-square_law).

The irradiance at any distance from the sun is equal to the total radiative energy of the sun divided
by the surface area of a sphere at the specified distance from the sun.

For example for earth the Irradiance (I) is:

1 Astronomical Unit (Distance from Sun to Earth) = 149 597 870 700 meters

```
I = 3.87 x 10^26 W / (4 *  pi * r^2)
  = 3.87 x 10^26 W / (4 *  pi * (1.49 x 10^11m)^2)
  = 3.87 x 10^26 W / (4 *  pi * 2.22x10^22m^2)
  = 3.87 x 10^26 W / (2.79x10^23m^2)
  = 1387 W/m^2
```

So if our solar panel is pulling 120 W/m^2 and it is 100% efficient it can't be located 1AU from the
"sun" or the "sun" is not the sun.

For the panel to make sense it would have to be about 8.65% efficient or located further from the sun.

The peak of metal-rich M-type asteroids is roughly 2.7 AU from the sun.<sup>[1](http://en.wikipedia.org/wiki/Asteroid_belt)</sup>

2.7 Astronomical Units = 403 914 250 890 meters

```
I = 3.87 x 10^26 W / (4 *  pi * r^2)
  = 3.87 x 10^26 W / (4 *  pi * (4.04 x 10^11m)^2)
  = 3.87 x 10^26 W / (4 *  pi * 1.63x10^23m^2)
  = 3.87 x 10^26 W / (2.05x10^24m^2)
  = 187 W/m^2
```

So if our solar panel is pulling 120 W/m^2 and it is 100% efficient it can't be located 2.7 AU from the
"sun" or the "sun" is not the sun.

For the panel to make sense it would have to be about 63.6% efficient or located further from the sun.

What is reasonable? The 100% efficiency assumption is bad.  The theoretical limit is 86% and 30% efficiency seems to be a reasonable number for current or near future panels.<sup>[2](http://en.wikipedia.org/wiki/Solar_cell_efficiency)</sup>

Where would that be? 120/400 = .3 so we need to be where we would get about 400 W/m^2

```
400 W/m^2 = 1387 W/m^2 (1 AU / x AU)^2
(1 AU / x AU)^2 = 400 / 1387
sqrt((1 AU / x AU)^2) = sqrt(400 / 1387)
1 / x = .537
x = 1.86 AU
```

For reference Mars is about 1.38 AU from the Sun.
