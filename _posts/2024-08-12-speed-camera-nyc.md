---
layout: post
title: Speed Camera NYC
date: 2024-08-12 09:28 -0400
---

<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

# Why is this titled Speed Camera NYC ?

In New York speed cameras are placed in school zones to photograph speeding vehicles. They operate 24 hours a day, 7 days a week. On sundays i would normally take my mom to work, so what are the odds you don't see a speed camera, very unlikely, Now that just got me thinking.

The cameras are usually mounted on poles or existing infrastructure, such as traffic light poles or streetlights, and are angled to capture vehicles as they pass through the monitored area. I would say they roughly stand at around 10 to 12 feet (approximately 3 to 3.6 meters) above the ground.


The PDF below entails some math i did on the objective to find out "How quickly a vehicle traveling above the speed limit would move out of the camera’s range."

[Speed Camera PDF](/assets/Speed_Camera.pdf)

But there's some caveats to the overall objective. 

## Overall Objective

- **Calculate the entire area of the speed camera range**

- **Calculate the vertical distance or more the straight line path the car is driving in**

- **Calculate the horizontal distance of the Speed Camera, given that at most they're two lanes where traffic flows, the camera would need a good enough width.**

- **Calculate the speed at which one would need to be out of the camera range to even have a half successful chances of avoiding the ticket.**

## Problem with objective 1
  > Problem with the above is that we are limited to using the camera footage provided of the violation. The footage at times varies, for example: "7 seconds", "15 seconds", "20 seconds". 

  > Second problem: In different areas, the cameras will be at different heights, giving a greater vertical distance and horizontal distance.

  > I'm also assuming a half-angle θ = 30◦ for the camera’s vertical field of view. Which gave a very inaccurate number.

  > The camera’s lens might introduce distortion, especially near the edges of the field of view, which can affect the accuracy of the coverage area calculation. Additionally, the angle at which the camera is mounted can vary, affecting both the vertical and horizontal coverage differently than a simple geometric calculation might suggest.

  > Environmental conditions like rain, fog, or glare from the sun can obscure parts of the camera’s field of view, effectively reducing the area it can reliably monitor. These factors aren’t typically accounted for in simple geometric models.

  > if the road isn’t perfectly flat and straight, but instead curves or changes elevation, this can drastically affect the actual area that the camera can monitor. A curve in the road could reduce the effective range of the camera, while elevation changes could either extend or reduce the camera's vertical reach.

  > Objects like trees, signs, other vehicles, or even overpasses can obstruct the camera’s view, reducing the actual area covered.

  > The camera's resolution may limit its ability to accurately capture or identify vehicles at the far edges of its field of view. Even if the camera theoretically covers a wide area, it might not be effective across the entire range.

  > Vehicles rarely maintain a constant speed as they pass through the camera zone. They may accelerate or decelerate, especially if the driver notices the camera. This variability makes it challenging to accurately calculate the area covered based solely on a fixed speed.


## Summing Distances Over Time

Integrals can be used to sum distances or areas over a period of time or across a range of speeds.

### Total Distance Traveled Over Time

Suppose we want to find the total distance traveled by a car over a period of time where the speed \( v(t) \) might vary. The total distance is the integral of the speed function over time:

$$
D_{\text{total}} = \int_{t_1}^{t_2} v(t) \, dt
$$

If the speed is constant, this simplifies to:

$$
D_{\text{total}} = v \times (t_2 - t_1)
$$

For non-constant speed \( v(t) \), you would need the specific function of speed over time to evaluate this integral.

  - Summing the total distance traveled by car over a period of time where the speed may be vary, is another way to yield the result of finding the camera range.

  > If speed varies (due to acceleration, deceleration, or different driving conditions), you would integrate the speed function to find out how far the vehicle traveled while in view.

  > If speed is constant, simply multiply the speed by the time the car is in view to determine the distance.

## The number one pitfall again

  **The length of the clip directly relates to how much of the vehicle's journey is captured. If the clip is short and captures only the moment when the violation occurs, then the total distance calculated might only represent a small portion of the vehicle's actual journey.**

  **Which in reality means that we only have a approximation of the total area that the cameras covers.**

## Total Area Covered Over a Range of Camera Angles

If we want to find the total area covered by the camera as the angle \( \theta \) varies, we would integrate the area function over the range of angles:

$$
A_{\text{total}} = \int_{\theta_1}^{\theta_2} 2D \times H \times \tan(\theta) \, d\theta
$$

This integral sums the areas as the camera angle changes from \\(\theta_1\\) to \\(\theta_2\\). This could be useful in scenarios where the camera is sweeping across different angles.

### 3. Example Application

Suppose we have a speed function \( v(t) = 25 + 5t \) (speed increasing linearly over time), and we want to find the total distance covered from time \( t = 0 \) to \( t = 5 \) seconds.

#### Set Up the Integral

$$
D_{\text{total}} = \int_{0}^{5} (25 + 5t) \, dt
$$

#### Evaluate the Integral

$$
D_{\text{total}} = \left[ 25t + \frac{5t^2}{2} \right]_0^5 = (125 + 62.5) - (0 + 0) = 187.5 \text{ feet}
$$

This means the car would cover a total of 187.5 feet in that 5-second period.


## Area Under a Speed-Time Curve

If we want to calculate the total distance traveled by a car using the area under the speed-time curve where the speed function \( v(t) = 20t^2 + 15t \) (speed varying quadratically with time), we integrate the speed function over a given time period.

### Set Up the Integral

Suppose we need to find the total distance traveled from \( t = 1 \) second to \( t = 4 \) seconds:

$$
D_{\text{total}} = \int_{1}^{4} (20t^2 + 15t) \, dt
$$

### Evaluate the Integral

$$
D_{\text{total}} = \left[ \frac{20t^3}{3} + \frac{15t^2}{2} \right]_1^4 = \left( \frac{20 \times 4^3}{3} + \frac{15 \times 4^2}{2} \right) - \left( \frac{20 \times 1^3}{3} + \frac{15 \times 1^2}{2} \right)
$$

Simplifying:

$$
D_{\text{total}} = \left( \frac{1280}{3} + 120 \right) - \left( \frac{20}{3} + 7.5 \right) = 426.67 + 120 - 6.67 - 7.5 = 532.5 \text{ feet}
$$

The car travels a total of 532.5 feet from \( t = 1 \) second to \( t = 4 \) seconds.


## Determining the Range of a Camera with a Moving Vehicle

Consider a scenario where a camera tracks a vehicle moving at a varying speed \( v(t) = 30 - 5t \) (speed decreasing over time). We need to calculate the range over which the camera captures the vehicle as it moves from \( t = 0 \) seconds to \( t = 6 \) seconds.

### Set Up the Integral

The total distance covered by the vehicle, which represents the camera's range, is given by:

$$
D_{\text{total}} = \int_{0}^{6} (30 - 5t) \, dt
$$

### Evaluate the Integral

$$
D_{\text{total}} = \left[ 30t - \frac{5t^2}{2} \right]_0^6 = \left( 30 \times 6 - \frac{5 \times 6^2}{2} \right) - \left( 30 \times 0 - \frac{5 \times 0^2}{2} \right)
$$

Simplifying:

$$
D_{\text{total}} = \left( 180 - 90 \right) - 0 = 90 \text{ feet}
$$

The camera captures the vehicle over a range of 90 feet during the 6-second period.
