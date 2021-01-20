# scribblesV2

This is the code for the webapp used to control Mr Scribbles (A dancing drawing Robot)

## Intro
Some people love expressing themselves while dancing; some people do it while drawing. We thought, why don't we combine those two and create something fun?
The Dancing Drawing Robot was created to help people feel more comfortable about their bodies, about their movements — about being weird sometimes ;)


![gif (1)](https://user-images.githubusercontent.com/75906242/105194991-21363a00-5b08-11eb-83be-e81b04edaf98.gif)
#### The Robot
- Our robot was driven by the arduino microcontroller, connected to DC and servo motors. 
The robot moves from left to right using the DC motors and has arms that rotate 180 using the servo motor.
View the entire video [here](https://vimeo.com/491766360?ref=em-v-share)
#### The Poses 
- We picked out famous dance moves and trained a model on ml5 to recognise the poses. 
These poses were meant to act as a replacement for the standard front, back etc buttons on controllers used for robots.
![poses](https://user-images.githubusercontent.com/75906242/105199690-0914e980-5b0d-11eb-8bc5-c9d370ed2adc.png)

#### Connecting the robot and the poses.
- We created a webpage that had a "menu" of poses available to the user. This webpage initiated an instance of our ml5 model to recognise the poses captured by the webcam.
- This webpage was connected to a websocket server(built on NODEJS). 
- The server on receiving the data forwards the data to our arduino through serial communication.

## Code
#### public/sketch.js
- Here is where the client logic resides. 
- A new instance of the trained ml5 model is created that helps identify the poses made by the user and on appropriate identification sends the data to the server.
   
#### server.js
- The server runs on expressJS. 
- It acts as an messenger between the arduino and client. It waits for incoming messages from the client and transmits it to arduino using the serial communication library. 
- It handles the following conditions 
   ##### WAITING_CLEARED - A newly connected client can control the robot
   ##### IN_USE - If a client is already controlling the robot
   ##### WAITING_CLEARED - A client in waiting has been cleared for use 


Find the webapge on
https://tranquil-dawn-67895.herokuapp.com/

To try out the robot, feel free to reach out
Just a quick start of the robot and you will be able to control it remotely.
