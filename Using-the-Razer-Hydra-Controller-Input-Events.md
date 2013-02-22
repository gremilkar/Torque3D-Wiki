The new Torque 3D Razer Hydra input device provides a number of input events that may be used with Torque 3D's action map system. There are a number of different ways to use the Razer Hydra input device, which are set up using global TorqueScript variables.

## Action Map Device Type ##

When binding a TorqueScript function to a Razer Hydra input event using Torque 3D's action map system, the device name to use is `razerhydra`.  As only one Razer Hydra may be used on a computer at a time, there is no need to append a device instance number to the end of the device name.  The following is an example of setting up a proper action map binding:

```
moveMap.bind( razerhydra, rh_trigger1, gamepadFire );
```

## Standard Gamepad Input Events ##

The Razer Hydra provides a full compliment of gamepad buttons and sticks spread across two hand held controllers.  Torque 3D provides complete access to all of these input events which behave as you would expect from a Xbox 360 compatible gamepad.  The following action map input events are available:

**Left Controller**
* `rh_thumbx0` - thumb stick x-axis motion in the range of -1.0 to 1.0
* `rh_thumby0` - thumb stick y-axis motion in the range of -1.0 to 1.0
* `rh_trigger0` - trigger motion (sometimes referred to as z-axis motion) in the range of 0.0 to 1.0
* `rh_shoulder0` - shoulder (or bumper) button
* `rh_thumb0` - thumb stick used as a button
* `rh_start0` - start button
* `rh_1button0` - 1 button
* `rh_2button0` - 2 button
* `rh_3button0` - 3 button
* `rh_4button0` - 4 button

**Right Controller**
* `rh_thumbx1` - thumb stick x-axis motion in the range of -1.0 to 1.0
* `rh_thumby1` - thumb stick y-axis motion in the range of -1.0 to 1.0
* `rh_trigger1` - trigger motion (sometimes referred to as z-axis motion) in the range of 0.0 to 1.0
* `rh_shoulder1` - shoulder (or bumper) button
* `rh_thumb1` - thumb stick used as a button
* `rh_start1` - start button
* `rh_1button1` - 1 button
* `rh_2button1` - 2 button
* `rh_3button1` - 3 button
* `rh_4button1` - 4 button

As with a standard gamepad, each of the thumb stick motions (and even the trigger although it is not usually used this way) are of the *AXIS* type.  This means that additional modifiers may be placed on their inputs, such as defining a dead zone.  For example, here is how you could set up the right controller's thumb stick to be used to rotate the player with a slight dead zone around the stick's neutral position:

```
moveMap.bind( razerhydra, rh_thumbx1, "D", "-0.23 0.23", gamepadYaw );
moveMap.bind( razerhydra, rh_thumby1, "D", "-0.23 0.23", gamepadPitch );
```

## Controller Absolute Position and Rotation Events ##

The unique feature of the Razer Hydra is being able to detect each the left and right controller's absolute position and rotation in space.  When it comes to generating position input events, there are two options available.  The first option is to receive each x, y and z axis update as separate events given as `rh_posx`, `rh_posy` and `rh_posz`.  You activate this option by setting the global TorqueScript variable `$RazerHydra::SeparatePositionEvents` to `true`, which is the default setting.  This is similar to how a thumb stick generates separate events for both the x and y axis.

The second option is to receive only a single position event `rh_pos` that includes each axis as a separate parameter.  You activate this mode by setting the global TorqueScript variable `$RazerHydra::CombinedPositionEvents` to `true`.  The primary advantage of this mode is you generally produce much less input events for Torque 3D to process.

The following action map input events are available (all positions are in millimeters and all rotations are in angled axis format):

**Left Controller**
* `rh_posx0` - absolute x axis position
* `rh_posy0` - absolute y axis position
* `rh_posz0` - absolute z axis position
* `rh_pos0` - absolute position provided as 3 parameters
* `rh_rot0` - absolute rotation

**Right Controller**
* `rh_posx1` - absolute x axis position
* `rh_posy1` - absolute y axis position
* `rh_posz1` - absolute z axis position
* `rh_pos1` - absolute position provided as 3 parameters
* `rh_rot1` - absolute rotation