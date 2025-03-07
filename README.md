# MSD-Oasis

# Installation
All of these instructions assume you are on a Windows system.
For our purposes, _software_ runs on your computer while _firmware_ runs on the printer's electronics.

## One-time prep for software
1. Clone this repo!
2. Install [Python 3.6.2](https://www.python.org/downloads/release/python-362/) on your system
3. Open a terminal and execute:
    ```(bash)
    pip install pyqt5 pyserial numpy   
    ```

## Running the software
1. Navigate to this repo's `Software` directory, and execute:
    ```(bash)
    python '.\Oasis controller.py'
    ```
2. Open `Device Manager` on your computer, and observe which `COM` ports appear as you plug in the print head USB and the electrical cabinet USB. These generally don't change until you plug other stuff into your computer, so it's useful to check often but not every time.
3. One port at a time, enter the appropriate COM port into the right-side software panel and click connect.
4. Ideally, you have now connected and the software is fully up and running!

## Editing the software
To edit the software, make sure the software is closed (click Disconnect on COM ports first !!), make your changes, and launch it again with the `python` command listed above.

## One-time prep for motion firmware
To edit the firmware, you'll first need the [Arduino IDE](https://www.arduino.cc/en/software) installed. 

___Don't do this (it will remove Oasis' custom settings)___, but here's how to flash the motion firmware to the Arduino:
1. In the Arduino IDE, go to `Sketch` > `Include Library` > `Add .ZIP Library...` and select the file `<this repo>/Firmware/GRBL/GRBL Uno 4 axis/grbl-master/grbl_4x.zip`. 
2. Then go to `File` > `Examples` > `grbl_4x` and you should see `grblUpload`. You're ready to build and flash!

Note: This was not written by Yvo, the creator of Oasis, but is a standard method of controlling 3D printer motion.

## To build and flash the motion firmware
Open the `grblUpload` project and flash it to the Arduino by using the round arrow button in the top left of the IDE (select the correct Board and Port first, with the Arduino plugged in). I have not made any changes to this code, and none should ever be necessary!

## One-time prep for print head firmware
To edit the firmware, you'll first need the [Arduino IDE](https://www.arduino.cc/en/software) installed. 

The print head firmware is entirely written by Yvo, and is not 100% working. See my section below on Todos regarding this firmware and the software.

1. Go to `File` > `Preferences` and enter the following URL under `Additional board manager URLs`:
    ```
    https://www.pjrc.com/teensy/package_teensy_index.json
    ```
2. Now, go to `Tools` > `Board` > `Boards Manager`.
3. Search for `teensy`, and install the `Teensy` package by Paul Stoffregen.

## To build and flash the print head firmware
1. Open the project `HP45_Standalone_V3.00.00.ino` located in the `Firmware/HP45` directory in this repository. All files within `HP45/` are used.
2. Have at it! Select the proper board and port, click the `Upload` arrow button, and ensure that the little window that opens doens't display errors. After making future edits, just click that upload button again and it will recompile the code.

## Committing and pushing to this repository
TODO

(learn git I guess)