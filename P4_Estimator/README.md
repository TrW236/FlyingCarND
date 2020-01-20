# Extended Kalman Filter

## 1. Sensor Noise
The library Pandas in Python is used to calculate the standard deviation `\sigma` for every measurements.

```python
import pandas as pd

data = pd.read_csv(<file_name>, sep=",", header=None, skiprows=1)
print(data.std(axis=0 ))
``` 

## 2. Attitude Estimation
The Bayer Filter has two main processes, one is `Predict`, the other is `Update`. The `Update` part is already implemented by Udacity. The task for the students is to implement the `Predict` part.

* A linear complementary filter is used for this function.
* The class `Quaternion` is used for the integration.

## 3. Prediction

* For the state update part, the next state is simply calculated through the same pattern `x_t = x_{t-1} + dt * \dot{x}_{t or t-1}`, which is the forward Euler method.
* For the covariance matrix update part, Matrix `Rbg'` and `g'` are firstly calculated, then the covariance matrix `\Sigma` is calculated after the formulas given in the documentation. 
* The parameters `QPosXYStd` and `QVelXYStd` are at the end tuned to let the calculated covariance grow similarly as the data.

## 4. Magnetometer Update

The magnetometer can measure the yaw directly. This measurement can be incorperated into the estimation of the value yaw.

## 5. Closed loop + GPS update

The GPS measurements are also used to update the state.

## References:

* [Udacity Flying Car Nanodegree](https://www.udacity.com/)
* [Estimation for Quadrotors](https://www.overleaf.com/read/vymfngphcccj#/54894644/)
* [original repository from Udacity](https://github.com/udacity/FCND-Estimation-CPP)
