<H2> The Model </H2>
MPC is based on the following <br>
  1> Kinematic Vehicle Model<br>
  2> Dynamic Vehicle Model<br>
  3> Actuate
  4> Actuator Constraints
  
  Putting it all together, here's the diagram<br>
  <img src="img/mpc.png">

<H2> Timestep Length and Elapsed Duration (N & dt) </H2>
<H2> Polynomial Fitting and MPC Preprocessing </H2>
I did preprocessing of px, py, psi and velocity. I added latency and calculated state 100ms seconds ahead. This helped in giving better control to the car.
<H2> Model Predictive Control with Latency</H2>
