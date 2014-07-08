LEAPController
========================================================

Name: LEAPController Plugin.

Version: 0.1.3

Type: Service Plugin

Author: Zachary Freiberg - Kiwi.js Team

Website: www.kiwijs.org

This is a plugin for the LEAP Motion Controller developed by LEAP Motion. 
For more information about LEAP Motion go to the LEAP motion website here. https://www.leapmotion.com/

Tutorials can be found on the KiwiJS.org website here:
http://www.kiwijs.org/documentation/tutorials/using-the-leap-motion-controller-plugin/

----------------------------------------------------------------------------------------
Files:
----------------------------------------------------------------------------------------

- leapMotion-0.1.2.js
- leapMotion-0.1.2.min.js

- examples/
	-usePlugin/
		- exampleSimpleMove.html
		- examplePlane.html
		- kiwi.js
		- simpleMove.js
		- Plane.js
		- assets/
			...
	
----------------------------------------------------------------------------------------
Description:
----------------------------------------------------------------------------------------
This plugin is developed to let users work with a Leap Motion controller. As of right now it is still in beta.

Current:
-Track Multiple hands:
	- Position
	- Direction
	- Normal
	- Roll
	- Pitch
	- Yaw

Track Multiple Fingers
	- Position
	- length
	- direction
	-
	

If you have any problems then feel free to contact us via the http://www.kiwijs.org/help

----------------------------------------------------------------------------------------
How to Include: 
----------------------------------------------------------------------------------------
First Step:
- Copy either the LEAPController.0.1.2.js or the LEAPController.0.1.2.min.js file (they should be right next to this one right now) into your project directory. We recommend that you save the files under a plugin directory that lives inside of your project directory so that you can easily manage all of the plugins but that is not required. 

Second:
- Link in the JavaScript file (that you have just copied across in the first step) into your HTML file. Make sure you link it in underneath the link to the main Kiwi.js file otherwise the plugin will not register and you can come across some errors.

Third: 
- Now that you have linked in the plugin, the next step is to tell the game to use this plugin. To do so, when you create a new Kiwi.Game you need to pass 'SaveGame' the confiration object's plugins item. You can see an example of the code below.

	var game = new Kiwi.Game('domElement', 'GameName', 'State', { plugins: ["LEAPController"]});

- Just make sure if you are including more than one System plugin that you pass other plugin's that you want to use also.

Lastly:
- Now that you have successfully include the plugin you can start using it.


----------------------------------------------------------------------------------------
How to use.
----------------------------------------------------------------------------------------
Creating a Controller

To create a controller all you simply need to do is call upon the createController method of the LEAPController plugin.

	this.control = Kiwi.Plugins.LEAPController.createController();

Each 'controller' has an array of 'hands' that store all hands that the leap controller is currently detecting. To access these 'Hand' objects and their properties look into the ‘hands’ array of the controller.

	this.control.hands;
	
This should return an array of hands that are currently being detected.

Each 'Hand' has an array of 'PointableObjects' that store all fingers of a 'Hand' object that the leap controller is currently detecting. To access these 'PointableObject' and their properties look into the ‘pointables’ array of the 'Hand'.

	this.control.hands[0].pointables;

This should return an array of 'PointableObjects' that are currently being detected.

--------------------------------------------
Properties of a Hand Object
--------------------------------------------
The 'hands' array stores all of the current 'Hand' objects.

Each hand object has these properties

posX - The X position of the center position of the palm in millimeters from the Leap origin.
posY - The Y position of the center position of the palm in millimeters from the Leap origin.
posZ - The Z position of the center position of the palm in millimeters from the Leap origin.

directionX - The X direction from the palm position toward the fingers.
directionY - The Y direction from the palm position toward the fingers.
directionZ - The Z direction from the palm position toward the fingers.

palmNormalX - The X component of the vector that exisits at 90 degrees to the face of the palm.
palmNormalY - The Y component of the vector that exisits at 90 degrees to the face of the palm.
palmNormalZ - The Z component of the vector that exisits at 90 degrees to the face of the palm.


roll - The roll angle in radians.

Roll is the angle between the y-axis and the projection of
the vector onto the x-y plane. In other words, roll represents rotation
around the z-axis. If the vector points to the left of the y-axis,
then the returned angle is between 0 and pi radians (180 degrees);
if it points to the right, the angle is between 0 and -pi radians.


pitch - The pitch angle in radians.

Pitch is the angle between the negative z-axis and the projection of
the vector onto the y-z plane. In other words, pitch represents rotation
around the x-axis.
If the vector points upward, the returned angle is between 0 and pi radians
(180 degrees); if it points downward, the angle is between 0 and -pi radians.


yaw - The yaw angle in radians.

Yaw is the angle between the negative z-axis and the projection of
the vector onto the x-z plane. In other words, yaw represents rotation
around the y-axis. If the vector points to the right of the negative z-axis,
then the returned angle is between 0 and pi radians (180 degrees);
if it points to the left, the angle is between 0 and -pi radians.


pointables[] - is the array that stores the 'PointableObjects' of the 'Hand' object.

--------------------------------------------
Properties of a PointableObject Object
--------------------------------------------

pointableLength - 
pointableWidth

tipX - The tips X position in millimeters from the Leap origin.
tipY - The tips Y position in millimeters from the Leap origin.
tipZ - The tips Z position in millimeters from the Leap origin.

directionX - The X direction in which this finger or tool is pointing.
directionY - The Y direction in which this finger or tool is pointing.
directionZ - The Z direction in which this finger or tool is pointing.

touchZone -  * The current touch zone of this Pointable object.

 The Leap Motion software computes the touch zone based on a floating touch
 plane that adapts to the user's finger movement and hand posture. The Leap
 Motion software interprets purposeful movements toward this plane as potential touch
 points. When a Pointable moves close to the adaptive touch plane, it enters the
 "hovering" zone. When a Pointable reaches or passes through the plane, it enters
 the "touching" zone.

 The possible states include:

 	"none" -- The Pointable is outside the hovering zone.
 	"hovering" -- The Pointable is close to, but not touching the touch plane.
 	"touching" -- The Pointable has penetrated the touch plane.

 The touchDistance value provides a normalized indication of the distance to
 the touch plane when the Pointable is in the hovering or touching zones.


touchDistance - A value proportional to the distance between this Pointable object and the adaptive touch plane.


 The touch distance is a value in the range [-1, 1]. The value 1.0 indicates the
 Pointable is at the far edge of the hovering zone. The value 0 indicates the
 Pointable is just entering the touching zone. A value of -1.0 indicates the
 Pointable is firmly within the touching zone. Values in between are
 proportional to the distance from the plane. Thus, the touchDistance of 0.5
 indicates that the Pointable is halfway into the hovering zone.

 You can use the touchDistance value to modulate visual feedback given to the
 user as their fingers close in on a touch target, such as a button.

--------------------------------------------
Take Note!
-------------------------------------------- 
 This plugin is still being developed

--------------------------------------------
TODO:
--------------------------------------------


