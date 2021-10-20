# Autonomus Vehicle Control
This repository contain an Implementation of Autonomous Vehicle Control for Self Driving Cars on CARLA Simulator using python for the course Introduction to Self Driving Cars in Self Driving Cars Specialization in Coursera
Both Lateral and Longitudanal Controls were implemented to generate the Control Signals Throttle, Brake and Steering.


<video src='Images/Demo.mp4' width=180/>
## Vehicle Model
For the implementation of the control kinematic bicycle model was used as the prefered vehicle model where front wheels are used as steering wheels and rear wheels are used as driving wheels.

![Vehicle Model](https://github.com/Chumsy0725/Autonomous-Vehicle-Control/blob/main/Images/Bicycle%20model.png)
>Image by Coursera

## Latteral Controller
Latteral Control was implemented using **Stanley Controller** which is a Geomatric Lateral Controller.
Stanley Controller uses the centre of the front wheel axis as the origin of it's coordinate system(Reference Point)
Stanley Controller generate the steering input based on the Heading Error(The angel between the dirrection of where wheels are pointed and the direction of where we should be heading) and the Cross Track Error(the distance between reference point and the closed point on the trajectory line(ax+by+c=0))

First the cross track error is conveted in to a cross track steering angel by geting the inverse tangent of (k*e/v) where **e** is the cross track error, **v** is current vellocity and **k** being a desired contant.

Then the Headding Error is calculated by getting the inverse tangent of the slope of tragetory line and the subtract in by current yaw angle.

the final **Steer Angel** (Delta) is calculated by summing both **Cross track Steering** and **Heading Error**

![Latteral Control](https://github.com/Chumsy0725/Autonomous-Vehicle-Control/blob/main/Images/Stanley%20controller.png)
> Image by Coursera

## Longitudanal Control
A PID Controller in a Closed Feedback Loop was implemented for Longitudanal Control due to it's great Performance. 
the Throttle output is  governed by the current error, total error and the derivative term of the current error. Depending on the sign of the throttle output Desired Break output was calculated.


