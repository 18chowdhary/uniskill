# Uniskill: The Unicycle Skill Evaluator
Whether you are just learning or a unicycle veteran, you may want to know how skilled you are. Maybe it is to see your improvement, or perhaps it is to settle a debate with your unicycle nemesis. After you stop falling off often, how do you know how good you have gotten at unicycling? The Uniskill is a device that evaluates the ability of a unicyclist to balance and ride as smoothly as possible, settling debates and helping unicyclists all around campus improve!
## Our motion sensor solves YOUR problems!
The heart of the Uniskill is a 3-axis gyroscope that measures the motion of the unicycle as it is ridden. The sensor is attached to unicycle frame, measuring tips, tilts, and tumbles of the rider. The data from this sensor are used to calculate the amount of effort the rider spends balancing the Unicycle; an experienced rider uses less effort to balance the unicycle than a new rider uses, so the experienced rider will have less motion overall. We compare the rider's effort to the expected effort based on our model of a perfect rider to quantify the rider's skill.
## How it works
### Collecting and processing data
Our 3-axis gyroscope measures the motion of the unicycle as it is ridden. The sensor is attached to the rod of the unicycle, as this is the most stable location for the sensor where we can accurately infer information about riders' stability. After we collect the motion data, we select a representative section of the data--generally starting from the point that the rider got onto the unicycle and ending at the point the rider got off the unicycle. Currently, Uniskill is best calibrated to determine skill if the rider is going forward in a straight line.
### Calculating effort
1. Calculate net angular velocity<br>
![img](https://latex.codecogs.com/gif.latex?g%5Bt%5D%3D%5Csqrt%20%7Bg_x%5E2%5Bt%5D&plus;g_y%5E2%5Bt%5D&plus;g_z%5E2%5Bt%5D%7D)
1. Calculate the N-point Discrete Fourier Transform of net angular velocity<br>
![img](https://latex.codecogs.com/gif.latex?G%5Bf%5D%3Ddft%5Cleft%20%5C%7B%20g%5Bt%5D%20%5Cright%20%5C%7D)
1. Calculate Energy Spectral Density (ESD) using the covariance method<br>
![img](https://latex.codecogs.com/gif.latex?S_%7Bxx%7D%5Bf%5D%20%3D%20G%5Bf%5DG%5E*%5Bf%5D)
1. Calculate effort as a summation of the ESD<br>
![img](https://latex.codecogs.com/gif.latex?%5Csum_%7Bf%3D0%7D%5E%7BN-1%7D%20S_%7Bxx%7D%5Bf%5D%5CDelta%20f)
1. Compare power to the ideal unicyclist, giving the Unicycle Skill Index (USI)<br>
![img](https://latex.codecogs.com/gif.latex?USI%20%3D%20P-P_%7Bideal%7D)

### Comparing to model and quantifying skill
![img](/assets/img/fbd_updated.PNG)

The above figure shows the free body diagram we constructed when we built our model. Because the Uniskill sensor is attached to the rod of the unicycle, we abstracted our view of the unicycle to include only the rod, with the rider's mass included within the rod's mass. We also assume that there are no frictional forces acting on the rod. We also constructed a specific coordinate system, where the unicycle x-axis points in the direction of motion of the unicycle, the unicycle y-axis is aligned with the wheel axle, and the unicycle z-axis is aligned to the unicycle rod. The global axes are aligned to the initial frame of the unicycle, with the global z-axis aligning with gravity.

The major forces acting on the rod are the force of gravity, acting at the center of mass, and the two balancing forces acting at either end of the rod. There is a balancing force at the top of the rod, F<sub>s</sub>, due to the rider leaning back and forth. This force acts in the opposite direction of the rod's angular velocity. There is also a balancing force at the bottom from the rod, F<sub>p</sub>, from the bearings, due to the rider pushing on the pedals. This force acts along the y-axis of the unicycle. These two balancing forces must be the same in order for there to be no torque; when they are not the same, torque is generated and the rod tips or tilts.

Considering our defined coordinate system and the forces that would be acting on the system if it were stable, we determined that in the ideal scenario, the angular velocity for all axes should be zero. This means that the effort for the ideal rider would also be 0 (though this is unlikely to actually happen in reality, as riding a unicycle and staying balanced creates some measurable angular velocity as the rider tilts and rotates, ).

In order to compare a rider's skill to our modeled ideal unicyclist, we calculate the difference between their measured effort and the ideal power (0).

## Results
We tested Uniskill on three participants by asking them to ride down a straight path that was about 50m long. We collected motion data and evaluated their skill. Below are their discrete Fourier transforms and Unicycle Skill Indices:

FFT | USI
---|---
![img](/assets/img/NS_FFT.png)|0.0932
![img](/assets/img/JR_FFT.png)|0.1033
![img](/assets/img/NF_FFT.png)|0.1738





## Future
Our prototype and analytical process are designed for simple forward motion; in the future, we would like to adapt Uniskill to be able to handle more complicated motion, like the rider riding in a circle (which would require different motion analysis to calculate the USI).

We would also like to collect data on more riders, in order to be able to compare riders to one another and get a better sense of what the USI of a highly skilled rider might actually be (rather than comparing the riders to an intangible ideal). This may also inform a better way to calculate the USI that captures more aspects of unicycling ability.
