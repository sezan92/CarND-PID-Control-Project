# Reflection on the Source code

## Describe the effect each of the P, I, D components had in your implementation.
I have used two PID controllers . One for controlling the steering angle. The other for Controlling the Speed.

### Steer
This is the most critical component, as we are controlling the steering mostly. All of the components are negative to make the controller output reduce the cross-track error output.

The P component (will be referred as `Kp`) is proportional to the Cross-track error. So the steering angle increases with the increase in cross-track error which is logical. If the cross-track error is big, we will be needing higher steering angle to get in the path.

The I component (will be referred as `Ki`) is proportional to the Summation of all previous cross-track errors. It reduces the effect of total accumulated error.

The D Component (will be referred as `Kd`) is proportional to the derivative of cross-track error. It tries to reduce any change in the cross-track error.

### Throttle

For throttle a simple P-controller was used but the error is modified.. 

```
throttle = Kp / (100 x cte)
```
The intuition is , that whenever cross-track error is high, the speed should be a bit lower to have more control over the steering. The constant factor of `Kp / (100 x cte)` is used instead of `Kp / cte ` so that the change in cte is amplified. It was set by trial and error.


### How the final Parameters were chosen.

The final parameters were chosen manually. At first only `Kp` was tuned. After getting good performance - the goodness here is subjective - the `Kd` was set to make the car more stable. After stability was good enough, `Ki` parameter was tuned. It should be noted that the effect of `Ki` parameter seems negligible, and requires further study.