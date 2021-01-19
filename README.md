# scribblesV2

This is the code for the webapp used to control Mr Scribbles (A dancing drawing Robot)
## Intro
#### The Robot
- Our robot was driven by the arduino microcontroller, connected to DC and servo motors. 
The robot moves from left to right using the DC motors and has arms that rotate 180 using the servo motor.

#### The Poses 
- We picked out famous dance moves and trained a model on ml5 to recognise the poses. 
These poses were meant to act as a replacement for the standard front, back etc buttons on controllers used for robots.

#### Connecting the robot and the poses.
- We created a webpage that had a "menu" of poses available to the user. This webpage initiated an instance of our ml5 model to recognise the poses captured by the webcam.
- This webpage was connected to a websocket server(built on NODEJS). 
- The server on receiving the data forwards the data to our arduino through serial communication.

## Code
#### server.js
- The server runs on expressJS. 
- It acts as an messenger between the arduino and client. It waits for incoming messages from the client and transmits it to arduino using the serial communication library. 
- It handles the following conditions 
   ##### WAITING_CLEARED - A newly connected client can control the robot
   ##### IN_USE - If a client is already controlling the robot
   ##### WAITING_CLEARED - A client in waiting has been cleared for use 
