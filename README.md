# Сomplete guide for installing custom firmware on HTC One m7

![image](https://user-images.githubusercontent.com/123565843/227847022-bb9b7a35-4f98-4c7c-a05f-b44d5fd23769.png)


*Attention!*
*When installing new firmware, you risk breaking the device beyond repair.*
*I am not responsible for bricked devices, lost data. dead SD cards, and other consequences associated with the implementation of the guide below.*
*By continuing to perform actions, you agree to this provision. Thank you and good luck! =)*



## Presetting:

0. To work with adb on your phone, you need to enable USB debugging. To do this, go to Settings, then About the phone. Find the line with the build number and click on it 7 times! After that, go back to the first settings screen, select the item for developers and check the box next to the corresponding item there.
1. Download files to work with  [adb and fastboot](https://developer.android.com/studio/releases/platform-tools#revisions)
2. Unpack the archive to c:\android folder
3. Connect your phone to your computer via USB
4. Install [the drivers](https://github.com/TomNotArtem/Android_11_on_HTC_One_M7/raw/main/HTC_drivers_Win7_x64.zip). The phone in the PC device manager should be defined as "MyHTC". Drivers for Windows 7 and later

*If you are unable to install the driver, switch your phone to fastboot mode and install the driver again. How to switch the phone is indicated in point 4 Opening the bootloader.*

*In my case, the phone showed up under "Other Devices" called "Android 1". After installing the driver, it appeared in the "Android USB Devices" section called "My HTC".*

## Opening the bootloader:
*Attention! When you open the bootloader, the internal memory of the phone will be completely cleared! Save the data to your PC.*

0. Register on the website HTCDev.com
1. Select Unlock Bootloader and click Start
2. Select all other supported models from the list and click Start Unlocking the bootloader
3. We agree to all the conditions and go to the instructions page (the Instructions button for unlocking the bootloader).
4. Switch the phone to the fast boot mode (bootloader): turn off the phone by pressing the power button and holding it until it starts to reboot, then release the power and immediately press the volume down button (-) and hold until you get into the bootloader
5. Check how the phone was identified in the device manager. It must be MyHTC. If not, install the driver again.
6. In the c folder:\android with the Shift key pressed, right-click anywhere and select Open Command Window. The command line will start, in which it should be written c:\android >
7. At the command prompt, type the ```fastboot oem get_identifier_token``` command
8. Select and copy the text (right-click, select Mark, press Enter) as shown in step 9 on HTCDev
9 website. Insert the "My Device ID Token" into the form:" on htcdev.com and click Submit (step 10)
10. After some time, an email with the Unlock_code files attached will be sent to your mailbox specified during registration.bin
11. Download it and save it in the c folder:\android
12. At the command prompt, type fastboot flash unlocktoken Unlock_code.bin
13. A menu with unlocking the bootloader should appear on the smartphone. Select "Yes" (using the volume control) and press the power button.
14. The phone will reboot. Ready!
15. To make sure that the bootloader is unlocked, we reboot into the bootloader (see point 5.5) and we see the inscription *** UNLOCKED at the top of the screen ***

## Download TWRP:

0. Download [TWRP](https://dl.twrp.me/m7univ/) and rename it to recovery.img. If the zip archive is downloaded, then you need to pull out the recovery.img file from there
1. Place the file you downloaded in the same folder where the Android files are, that is C:\Android
2. Switch the phone to fastboot mode
3. Now type in the command line:
```
fastboot flash recovery recovery.img
fastboot erase cache
fastboot reboot
```
4. Recovery is established. In order to enter recovery, you need to switch the phone to fastboot mode, use the volume buttons to select Bootloader and press the Power button, then select Recovery and press the Power button again

## Installing Firmware and BiTGApps:

0. Download the selected firmware and put it in the phone's memory, for convenience, it is better to put it in the root folder. You also need to download BiTGApps- Google apps (Play Market, etc.)
1. Reboot into recovery
2. We make types, that is, bringing it to the factory state:
```Swipe, swipe to execute. You can manually select the items to be cleaned: Dalvik Cache, Cache, Data, System. To do this, click Advanced Wipe.```
3. Installing the firmware:
```Install -> select the downloaded firmware -> confirm```
4. Done! The firmware will be installed! Next, you need to install BiTGApps- just like the firmware
5. Reboot the device


P.S. If the command line responds to the input of adb commands with error: ```device not found```, then there is a problem with the drivers. Go to the device manager and see how the phone is identified.

P.P.S. Thread on XDA: [[ROM][11.0][UNOFFICIAL][M7-ALL] LineageOS 18.1 [STABLE]](https://forum.xda-developers.com/t/rom-11-0-unofficial-m7-all-lineageos-18-1-stable.4454219/)
