---
layout: post
title: Speed Camera NYC
date: 2024-08-12 09:28 -0400
---


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

