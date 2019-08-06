# RGB Camera

Follow this guide to learn how to build a sample app to retrieve RGB camera data from Nreal Light glasses through NRSDK.

## Open the Sample Scene
* In the Unity Project window, you can find the **CameraCaptureDemo** sample in:
    `Assets > NRSDK >Demos > RGBCamera`.

## Build and Run the Sample App
* Enable developer options and USB debugging on your Nreal Light computing unit. [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) is enabled as default. 

* Connect your Nreal Light computing unit to your Windows PC.

* In the Unity **Build Settings** window, click **Build and Run**.

> See `CameraCaptureController.cs` , located in `Assets > NRSDK > Demos > CameraCapture > Scripts` for an example on how to get the texture of RGB Camera. 

* Initialize NRCameraCapture in MonoBehaviour and configure it as follows:
    ~~~c#
    NRCameraCapture CameraCapture = gameObject.AddComponent<NRCameraCapture>();
    CameraCapture.Format = CameraImageFormat.RGB_888;
    CameraCapture.UpdateFrameRate = FrameRate;
    CameraCapture.OnFirstFrameReady += OnFirstFrameReady;
    CameraCapture.OnError += OnError;
    CameraCapture.Play();
    ~~~
* Implement your callback function to get the texture in OnFirstFramReady.
    ~~~c#
    private void OnFirstFrameReady()
    {
        CaptureImage.texture = CameraCapture.Texture;
    }
    ~~~   
    
