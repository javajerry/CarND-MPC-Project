<H2> The Model </H2>
Model Predictive Control (MPC) is an optimization model which tries to minimize the difference between the model predicted value and the reference trajectory path which includes distance of the vehicle from the trajectory as well as vehicle orientation and trajectory orientation.
MPC is based on the following <br>
  1> Kinematic Vehicle Model<br>
  This model defines the state of the vehicle. state=[x, y, ψ, v] where x,y is the position of the car. ψ (psi) is the orientation with respect to the x-axis. v is the velocity of the vehicle.<br>
  2> Dynamic Vehicle Model<br>
  This model covers longitudinal and lateral forces. <br> in this project we used Lf which is the distance between gravity of the vehicle and the front wheels<br>
  3> Actuator Constraints
  This defines the limitation for the vehicle. In this project, steering angle [denoted by δ] is limited between -25 degree to 25 degree. Similarly throttle/brake [denoted by a] is limited between -1 and 1 where -1 represents the brake and 1 is the full acceleration.<br>
  
  Putting it all together, here's the diagram<br>
  <img src="img/mpc.png">
  <br>
<H2> Timestep Length and Elapsed Duration (N & dt) </H2>
N is the number of timesteps and dt is the time elapse between actuations. I started with N=10 an dt=.1 which gives 1 second of future prediction T (= N * dt). These values made car unstable (oscillate) and throw of the track. I reduced dt=0.5 and was able to stabilize the car. Then I played with N with values 8 and 12 and got better result with 12. Also got tip from the forum, keep dt lower than latency value.

<H2> Polynomial Fitting and MPC Preprocessing </H2>
The waypoints are preprocessed by transforming them to the vehicle's perspective  Third degree polynomial fit is applied to the waypoints because the vehicle's x and y coordinates are now at the origin (0, 0) and the orientation angle is also zero.

<H2> Model Predictive Control with Latency</H2>
Latency was applied to positiox x, y psi and v prior to passing it to MPC solver. In order to handle 100ms latency, dt was set 0.1. This helped in predicitng car state in the next acutation (100 ms) which was taken into the account when MPC solved it and then fed to the simulator. Prior to adding latency I observed car had oscillation along the yellow trajectory but after adding it, it made car more stable. Adapting to latency, gives MPC bigger advantage over PID controller which cant handle latency.
<br>
<H2>Video Link of my project</H2>
<a href="https://www.youtube.com/watch?v=HLHeEp52BbM">https://www.youtube.com/watch?v=HLHeEp52BbM</a>
