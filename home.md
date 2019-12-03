# Uniskill: The Unicycle Skill Evaluator
Whether you are just learning or a unicycle veteran, you may want to know how skilled you are. Maybe it is to see your improvement, or perhaps it is to settle a debate with your unicycle nemesis. After you stop falling off often, how do you know how good you have gotten at unicycling? The Uniskill is a device that evaluates the ability of a unicyclist to balance and ride as smoothly as possible, settling debates and helping unicyclists all around campus improve!
## Our motion sensor solves YOUR problems!
The heart of the Uniskill is a 3-axis accelerometer that measures the motion of the unicycle as it is ridden. The sensor is attached to unicycle frame, measuring tips, tilts, and tumbles of the rider. The data from this sensor are used to calculate the amount of effort the rider spends balancing the Unicycle; an experienced rider uses less effort to balance the unicycle than a new rider uses, so the experienced rider will have less motion overall.
## How it works
### Collecting data
### Calculating effort
1. Cut out a representative section of the data
1. Calculate net acceleration<br>
![img](https://latex.codecogs.com/gif.latex?a%28t%29%3D%5Csqrt%20%7Ba_x%5E2%28t%29&plus;a_y%5E2%28t%29&plus;a_z%5E2%28t%29%7D)
1. Discrete Fourier Transform net acceleration<br>
![img](https://latex.codecogs.com/gif.latex?A%28f%29%3Dfft%5Cleft%20%5C%7B%20a%28t%29%20%5Cright%20%5C%7D)
1. Calculate power across all frequencies as the Power Spectral Density
1. Calculate net power
![img]()
1. Normalize power to the ideal unicyclist

### Compare to model

## Results
## Future
