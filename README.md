## Install ADB & Fastboot on the MacOS Devices :

<ins> setup ADB & fastboot on macOS device, follow these steps:</ins>
1.  Go to this [Platform Tools](https://developer.android.com/studio/releases/platform-tools) website. and Download.
2.  Scroll down the page to locate Downloads. 
3.  Select SDK Platform-Tools for Mac and download it.
   <img width="561" height="265" alt="image" src="https://github.com/user-attachments/assets/31b68ffa-707f-44c2-8030-294fb33c679d" />

4.  The platform-tools zip file will be downloaded. Extract the folder and place it in an accessible location.
5.  Save it in a location where you won't accidentally delete it.
6.  Start the terminal on the platform tools folder and execute the following commands:
```
mkdir ~/.android-sdk-macosx
mv platform-tools/ ~/.android-sdk-macosx/platform-tools
```
7.  Add platform-tools to the path
```
echo 'export PATH=$PATH:~/.android-sdk-macosx/platform-tools/'   >> ~/.bash_profile
```
8.  Refresh your bash_profile (or restart the Terminal app).
```
source ~/.bash_profile
```
9.  This package contains an <ins>adb</ins> file; please note down this path which is required when configuring the agent.
10. Enable Developer Option and USB Debugging on the device
11. Ensure USB debugging is enabled on the Android device that you want to connect with AstroFarm.

### To enable USB debugging on a device :
1.  On the Android device, open the **Settings** application.
2.  Tap **About Phone** option at the bottom of the list. 
If the About Phone option is unavailable,  go to **System > About Phone**.
3.  Tap the **Build Number** option 7 times to enable **Developer Mode**. 
     You can see a toast message once it is enabled.
4.  Now go back to the initial **Settings** screen and tap **Developer Options**.
5.  If the developer option is not visible under settings, go to **System -> Developer Options**.
6.  Enable the **USB Debugging mode** option on the device. **Select Always allow from this computer** and tap **OK**.
   <img width="350" height="845" alt="image" src="https://github.com/user-attachments/assets/ae1bcdc0-5b2a-4990-a912-299694d340d6" />

7. Plug the device into your host machine via USB cable.
8. Open the Command window and enter :
```
adb devices
```
9. The device information will be displayed. Watch the device's screen for any authorization message and allow the connection.
<img width="550" height="483" alt="Screenshot 2025-09-04 at 6 00 38 AM" src="https://github.com/user-attachments/assets/6843c86f-579f-4c5c-b2f7-5013d17b20ea" />

## Done, Now enjoy ADB & Fastboot services on your Mac.
