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
![img](https://latex.codecogs.com/gif.latex?A%5Bf%5D%3Ddft%5Cleft%20%5C%7B%20a%28t%29%20%5Cright%20%5C%7D)
1. Calculate Energy Spectral Density (ESD) using the covariance method
![img](https://latex.codecogs.com/gif.latex?S_%7Bxx%7D%5Bf%5D%20%3D%20A%5Bf%5DA%5E*%5Bf%5D)
1. Calculate net power to represent effort<br>
![img](https://latex.codecogs.com/gif.latex?P%20%3D%20%5Cfrac%7B1%7D%7B%5Cpi%7D%20%5Cint%20S_%7Bxx%7D%28f%29df)
1. Normalize power to the ideal unicyclist, giving the Unicycle Skill Index (USI)<br>
![img](https://latex.codecogs.com/gif.latex?USI%20%3D%20%5Cfrac%7BP%7D%7BP_%7Bideal%7D%7D)

### Compare to model
![img](https://i.imgur.com/rZw0E8A.png)

The above figure shows the free body diagram we constructed when we built our model. Because the Uniskill sensor is attached to the rod of the unicycle, we abstracted our view of the unicycle to include only the rod, with the rider's mass included within the rod's mass. We also assume that there are no frictional forces acting on the rod. We also constructed a specific coordinate system, where the x-axis lines up laterally with the direction of motion of the unicycle, the y-axis lines up with the pedals/the axis of rotation, and the z-axis lines up vertically with the force of gravity.

The major forces acting on the rod are the force of gravity, acting at the center of mass, and the two balancing forces acting at either end. These two balancing forces must be the same in order for there to be no torque; when they are not the same, torque is generated and the rod tips or tilts appropriately.

Considering our defined coordinate system and the forces that would be acting on the system if it were stable, we determined that in the ideal scenario, the acceleration on the x-axis and y-axis would be 0 m/s^2 and the acceleration on the z-axis would be 9.8 m/s^2 (g). The acceleration on all axes would be constant; therefore, there would be a frequency of 0Hz on each axis.

## Results
We have had three participants with the following discrete fourier transforms and net power:

FFT |![img](/assets/img/NS_FFT.png)|![img](/assets/img/NF_FFT.png)|![img](/assets/img/JR_FFT.png)
---|--- | --- | ---
Net Power | 0.0932 | 0.1738 | 0.1033

## Future
