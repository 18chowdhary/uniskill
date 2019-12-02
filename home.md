# Uniskill: The Unicycle Skill Evaluator
Whether you are just learning or a unicycle veteran, you may want to know how skilled you are. Maybe it is to see your improvement, or perhaps it is to settle a debate with your unicycle nemesis. After you stop falling off often, how do you know how good you have gotten at unicycling? The Uniskill is a device that evaluates the ability of a unicyclist to balance and ride as smoothly as possible, settling debates and helping unicyclists all around campus improve!
## Our motion sensor solves YOUR problems!
The heart of the Uniskill is a 3-axis accelerometer that measures the motion of the unicycle as it is ridden. The sensor is attached to unicycle frame, measuring tips, tilts, and tumbles of the rider. The data from this sensor are used to calculate the amount of effort the rider spends balancing the Unicycle; an experienced rider uses less effort to balance the unicycle than a new rider uses, so the experienced rider will have less motion overall.
### How we calculate effort
1. Acquire time domain accelerometer data
1. Calculate net acceleration
1. Discrete Fourier Transform net acceleration 
1. Calculate power over all frequencies as the variance of the DFT
1. Normalize power to the ideal unicyclist

### Why does this calculation work?

## Do
## Done
