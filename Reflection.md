# Reflection on the Source code

## Describe the effect each of the P, I, D components had in your implementation.
I have used two PID controllers . One for controlling the steering angle. The other for Controlling the Speed.

### Steer
This is the most critical component, as we are controlling the steering mostly. All of the components are negative to make the controller output reduce the cross-track error output.

P component (will be referred as `Kp`) is proportional to the Cross-track error. So the steering angle increases with the increase in cross-track error which is logical. If the cross-track error is big, we will be needing higher steering angle to get in the path.

I compnent (will be referred as `Ki`) is proportional to the Summation of all previous cross-track errors. It reduces the effect of total accumulated error.