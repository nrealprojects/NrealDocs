# Quickstart for Android

Start developing your NRSDK Unity apps on Android.

This quickstart guide will help you set up your development environment and test out the sample app "Hello MR" on NRSDK.

![](https://nreal-public.nreal.ai/developer/img/unity01.jpg)

## Getting Started


**Hardware Checklist**

* A Nreal Computing Unit (Think of it as an Android phone with no screen, so all development processes will be very similar to mobile app development.)

* A pair of Nreal Light glasses

> Don't have an Nreal device? Sign up for the [Nreal Developer Kit](/app/apply)! Or try **Emulator**  to pilot Nreal app functions without Nreal Light glasses and computing unit.

* A USB-C cable to connect the Nreal computing unit to your PC

*  Wi-Fi connection is not necessary. However, a Wi-Fi [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) connection can be used to debug and test.


**Software Checklist**

* [Unity 2018.2.X](https://unity3d.com/get-unity/download) with Android Build Support

* Download [NRSDK for Unity 1.0.0](/download)


  The SDK is downloaded as `NRSDKForUnity_1.0.0.unitypackage`

* Android SDK 7.0 (API Level 24) or later, installed using the SDK Manager in [Android Studio](https://developer.android.com/studio)


## Creating a Unity Project

* Open Unity and create a new 3D project.

* Set`Player Settings > Other Settings > Scritping Runtime Version` to `.net 4.x Equivalent`
* Import NRSDK for Unity
    * Select Assets > Import Package > Custom Package.

    * Select the `NRSDKForUnity_1.0.0.unitypackage` that you downloaded.
    * In the **Importing** Package dialog, make sure that all package options are selected and click **Import**.


## Hello MR - Your First Sample App

* Find the **HelloMR** sample app in the Unity Project window by selecting `Assets > NRSDK > Demos > HelloMR.`

    ![](https://nreal-public.nreal.ai/developer/img/unity02.jpg)



## Configure Build Settings

* Go to **File > Build Settings**.
* Select **Android** and click **Switch Platform**.
* In the **Build Settings** window, click **Player Settings**.
* In the **Inspector** window, configure player settings as follows:

Setting                         |                            Value
-|-
`Player Settings > Resolution and Presentation > Default Orientation` | **"Landscape Left"**  when using an Nreal Light computing unit , **"Portrait"**  when using a smart phone
`Player Settings > Other Settings > Package Name`   |  Create a unique app ID using a Java package name format. For example, use **com.nreal.helloMR**
`Player Settings > Other Settings > Multithreaded Rendering` | Disable
`Player Settings > Other Settings > Minimum API Level` |  Android 4.4 or higher
`Player Settings > Other Settings > Target API Level`  | Android 7.0 or higher
`Player Settings > Other Settings > Write Permission`  | External(SDCard)
`Project Settings > Quality > V Sync Count`   |  Don't Sync


## Connect to Nreal Device

* Enable developer options and USB debugging on your computing unit. [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb)  is enabled as default and does not require manual setting).

* Connect your computing unit to your Windows PC.


## Build and Run

* In the Unity **Build Settings** window, click **Build**. Install your app through WiFi [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) after the build is successful.

* Disconnect the computing unit with your PC, and then connect it to the glasses.

* Launch you app along with the Nreal Light controller. For instructions on how to use the Nreal Light controller, please see the [Controller Guide](/develop/unity/controller).


* Move around until NRSDK finds a horizontal plane and the detected plane will be covered with green grid.

* Click the Trigger button to put an Nreal logo object on it.

* (Optional) Use **Android Logcat** to view logged messages. We recommend using WiFi [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) to connect to your PC so that you do not have to be connected through the data cable most of the time.


## Next Steps

* Use [**Image Tracking**](/develop/unity/image-tracking) to build apps that can detect and track multiple images in the physical environment.
