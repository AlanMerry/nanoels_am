This software and instructions are [provided as is](LICENSE), without warranty of any kind. [🇷🇺 Перевод на русский](https://translate.google.com/translate?hl=en&sl=en&tl=ru&u=https%3A%2F%2Fgithub.com%2Fkachurovskiy%2Fnanoels%2Fblob%2Fmain%2FREADME.md), [🇩🇪 deutsche Übersetzung](https://translate.google.com/translate?hl=en&sl=en&tl=de&u=https%3A%2F%2Fgithub.com%2Fkachurovskiy%2Fnanoels%2Fblob%2Fmain%2FREADME.md)

This is a fork created by Alan Merry and includes changes to the Nextion display to cater for a 7 inch diaplay and changes to the sketch as follows:-


//alan.  Change axis button text colour to yellow when it is disabled by pressing the Axis Letter

//alan1. Add a Unit Confirmation Change, press Unit Button within 3 secs to confirm the change. Otherwise it will revert to the original Units.

//alan2. Resolve the joystick not respecting the move limits when the Z Axis Joystick is inverted. This is despite the fact that the Joystick moves correctly.
         The Z Pulse sign is restored.

//alan3. Limit Joystick moves to a single axis, the first big move takes priority.

//alan4. After all power ons, display the Software version and IP address until the play button is pressed. This is after the wifi configuration has been completed

//alan5. Add new Web UI Page to display all of the Pref Settings on a single page. This faciltates easy output of all of the Pref Settings as a report

//alan6. Amend the diameter display so the correct diameter is displayed after the diameter has been entered by pressing button tx, this was previously doubling the diameter. 


The assumption with this fork is that the Nextion Touch screen is deplyed as the sole data entry method.




**Design lathe parts in the browser with [LatheCode](https://kachurovskiy.com/lathecode/):** start from sample shapes, dimensions, drawings, saved profiles, or STL meshes; preview the result in 2D/3D; then export STL or G-code for machining. It fits naturally with NanoELS and Modulathe workflows: design the turned profile, inspect the generated toolpath, and run or save G-code for your controller, with drafts and settings kept locally in your browser.

# NanoEls H5

CNC and electronic lead screw controller based on ESP32-S3 that supports up to 3 axes:

- All the features of H4
- Cheaper and much easier to make than H4
- External PS2 keyboard
- High resolution touch screen
- More ports: joystick, MPGs, scales

![image](https://github.com/user-attachments/assets/de30c2ee-14d5-483a-b23d-0edc43125bd0)

See [h5 folder for hardware files, software and assembly](https://github.com/AlanMerry/nanoels_am/tree/main/h5).


## Build examples

- [EdFleta](https://github.com/kachurovskiy/nanoels/discussions/87)
- [fmw626](https://github.com/kachurovskiy/nanoels/discussions/118)
- [Johannmupa](https://github.com/kachurovskiy/nanoels/discussions/89)
- [kachurovskiy](https://youtu.be/jR4tBBHSl3c?t=62)

# Contributing to the project

- Questions, problems and improvements: please start [a new GitHub Discussion](https://github.com/kachurovskiy/nanoels/discussions/new) or a new Issue
- Successful builds: please start a new GitHub Discussion with photos and comments
