# Uniskill: The Unicycle Skill Evaluator
Whether you are just learning or a unicycle veteran, you may want to know how skilled you are. Maybe it is to see your improvement, or perhaps it is to settle a debate with your unicycle nemesis. After you stop falling off often, how do you know how good you have gotten at unicycling? The Uniskill is a device that evaluates the ability of a unicyclist to balance and ride as smoothly as possible, settling debates and helping unicyclists all around campus improve!
## Our motion sensor solves YOUR problems!
The heart of the Uniskill is a 3-axis accelerometer that measures the motion of the unicycle as it is ridden. The sensor is attached to unicycle frame, measuring tips, tilts, and tumbles of the rider. The data from this sensor are used to calculate the amount of effort the rider spends balancing the Unicycle; an experienced rider uses less effort to balance the unicycle than a new rider uses, so the experienced rider will have less motion overall. We compare the rider's effort to the expected effort based on our model of a perfect rider to quantify the rider's skill.
## How it works
### Collecting and processing data
Our 3-axis accelerometer measures the motion of the unicycle as it is ridden. The sensor is attached to the rod of the unicycle, as this is the most stable location for the sensor where we can accurately infer information about riders' stability. After we collect the motion data, we select a representative section of the data--generally starting from the point that the rider got onto the unicycle and ending at the point the rider got off the unicycle. Currently, Uniskill is best calibrated to determine skill if the rider is going forward in a straight line.
### Calculating effort
1. Calculate net acceleration<br>
![img](https://latex.codecogs.com/gif.latex?a%28t%29%3D%5Csqrt%20%7Ba_x%5E2%28t%29&plus;a_y%5E2%28t%29&plus;a_z%5E2%28t%29%7D)
1. Discrete Fourier Transform net acceleration<br>
![img](https://latex.codecogs.com/gif.latex?A%5Bf%5D%3Dfft%5Cleft%20%5C%7B%20a%28t%29%20%5Cright%20%5C%7D)
1. Calculate energy across all frequencies of net accleration as the Energy Spectral Density (ESD)
![img](https://latex.codecogs.com/gif.latex?S_%7Bxx%7D%5Bf%5D%20%3D%20A%5Bf%5DA%5E*%5Bf%5D)
1. Calculate net power to represent effort<br>
![img](https://latex.codecogs.com/gif.latex?P%20%3D%20%5Cfrac%7B1%7D%7B%5Cpi%7D%20%5Cint%20S_%7Bxx%7D%28f%29df)
1. Normalize power to the ideal unicyclist<br>
![img](https://latex.codecogs.com/gif.latex?USI%20%3D%20%5Cfrac%7BP%7D%7BP_%7Bideal%7D%7D)

### Compare to model

![img](https://i.imgur.com/DDS9Iyt.png)
## Results
## Future
